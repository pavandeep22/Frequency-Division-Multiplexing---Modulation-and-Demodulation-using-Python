Skip to content
Navigation Menu
sathish-git-tech
Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python

Type / to search
Code
Pull requests
Actions
Projects
Security
Insights
You’re making changes in a project you don’t have write access to. Submitting a change will write it to a new branch in your fork pavandeep22/Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python, so you can send a pull request.
Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python
/
README.md
in
main

Edit

Preview
Indent mode

Spaces
Indent size

4
Line wrap mode

Soft wrap
Editing README.md file contents
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118


m1 = sin(2*%pi*200*t);
m2 = sin(2*%pi*300*t);
m3 = sin(2*%pi*400*t);
m4 = sin(2*%pi*500*t);
m5 = sin(2*%pi*600*t);
m6 = sin(2*%pi*700*t);

c1 = 3000; c2 = 6000; c3 = 9000; c4 = 12000; c5 = 15000; c6 = 18000;

carrier1 = cos(2*%pi*c1*t);
carrier2 = cos(2*%pi*c2*t);
carrier3 = cos(2*%pi*c3*t);
carrier4 = cos(2*%pi*c4*t);
carrier5 = cos(2*%pi*c5*t);
carrier6 = cos(2*%pi*c6*t);

s1 = m1 .* carrier1;
s2 = m2 .* carrier2;
s3 = m3 .* carrier3;
s4 = m4 .* carrier4;
s5 = m5 .* carrier5;
s6 = m6 .* carrier6;

s_total = s1 + s2 + s3 + s4 + s5 + s6;

// Demultiplex: multiply by carriers to shift each band back to baseband
r1 = s_total .* carrier1;
r2 = s_total .* carrier2;
r3 = s_total .* carrier3;
r4 = s_total .* carrier4;
r5 = s_total .* carrier5;
r6 = s_total .* carrier6;

// Simple FFT-based ideal low-pass filter (avoids butter/toolbox issues)
function y = ideal_lowpass_fft(x, Fs, fc)
    N = length(x);
    X = fft(x);
    f = Fs*(0:N-1)/N;
    mask = (f <= fc) | (f >= Fs-fc);
    Y = X .* mask;
    y = real(ifft(Y));
endfunction

fc = 1000;
dm1 = ideal_lowpass_fft(r1, Fs, fc);
dm2 = ideal_lowpass_fft(r2, Fs, fc);
dm3 = ideal_lowpass_fft(r3, Fs, fc);
dm4 = ideal_lowpass_fft(r4, Fs, fc);
dm5 = ideal_lowpass_fft(r5, Fs, fc);
dm6 = ideal_lowpass_fft(r6, Fs, fc);

figure(1);
subplot(3,2,1); plot(t,m1); title("Message Signal 1");
subplot(3,2,2); plot(t,m2); title("Message Signal 2");
subplot(3,2,3); plot(t,m3); title("Message Signal 3");
subplot(3,2,4); plot(t,m4); title("Message Signal 4");
subplot(3,2,5); plot(t,m5); title("Message Signal 5");
subplot(3,2,6); plot(t,m6); title("Message Signal 6");

figure(2);
plot(t, s_total); title("Multiplexed FDM Signal");

figure(3);
subplot(3,2,1); plot(t,dm1); title("Recovered Signal 1");
subplot(3,2,2); plot(t,dm2); title("Recovered Signal 2");
subplot(3,2,3); plot(t,dm3); title("Recovered Signal 3");
subplot(3,2,4); plot(t,dm4); title("Recovered Signal 4");
subplot(3,2,5); plot(t,dm5); title("Recovered Signal 5");
subplot(3,2,6); plot(t,dm6); title("Recovered Signal 6");

```

# __Output__:
<img width="1920" height="1200" alt="a11 1" src="https://github.com/user-attachments/assets/d90a5415-d4d3-4d2b-9ca0-0bc86435fa37" />
<img width="1920" height="1200" alt="a11 2" src="https://github.com/user-attachments/assets/cf18ed98-d8c1-4ffc-8af6-3dd0d2034115" />
<img width="1920" height="1200" alt="a11 3" src="https://github.com/user-attachments/assets/849eaa56-685c-4a4c-99d1-73bf0d6d26cc" />
# __Result__:
The Frequency Division Multiplexing (FDM) technique was successfully implemented using SCILAB. Five different message signals were modulated onto five separate carrier frequencies, combined to form a single FDM composite signal, and then individually recovered using demodulation.

Use Control + Shift + m to toggle the tab key moving focus. Alternatively, use esc then tab to move to the next interactive element on the page.
No file chosen
Attach files by dragging & dropping, selecting or pasting them.
Editing Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python/README.md at main · sathish-git-tech/Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python
