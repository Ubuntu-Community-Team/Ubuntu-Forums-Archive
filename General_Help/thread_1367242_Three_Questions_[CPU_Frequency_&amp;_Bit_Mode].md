---
title: "Three Questions [CPU Frequency &amp; Bit Mode]"
date: 2009-12-29
forum: General Help
---

### Post by systemous on 2009-12-29
I have three questions. 

1) Every time i start the computer, i have to set the cpu frequency mode to Perfomance (from the CPU Frequency Scaling Monitor) for the two cores in order to work at max speed (3.0 ghz). Is it possible to make it run **only** at Performance?

2) I can see in the Sysinfo that the speed of my two cores are 3.0 ghz. I o/ced my cpu to 3.22. Why i can't see that speed in Sysinfo and why i can't set it in CPU Frequency Scaling Monitor? (it shows max speed 3.0 ghz)

3) In Ubuntu, the x86 means 32 bit and the x86_x64 means 64 bit?

---

### Post by ibuclaw on 2009-12-29
> **systemous said:**
> I have three questions. 

1) Every time i start the computer, i have to set the cpu frequency mode to Perfomance (from the CPU Frequency Scaling Monitor) for the two cores in order to work at max speed (3.0 ghz). Is it possible to make it run **only** at Performance?

2) I can see in the Sysinfo that the speed of my two cores are 3.0 ghz. I o/ced my cpu to 3.22. Why i can't see that speed in Sysinfo and why i can't set it in CPU Frequency Scaling Monitor? (it shows max speed 3.0 ghz)

3) In Ubuntu, the x86 means 32 bit and the x86_x64 means 64 bit?

1) Not sure what you mean - but if your workstation is like pretty much every other workstation out there, your CPU will spend most it's time in an idle state. Setting it to performance will have no benefit over the default value of ondemand.

2) Not sure what Sysinfo is - but there is a CPU Scalar applet for the Gnome Panel that should tell you what clock speed the CPU is currently working at (CPU's have what is called "states". The most common state it runs in is the the idle state - which is usually around 400-800MHz - but is very dependent on CPU type/model).

3) Yes - 64bit is just an extension of 32bit. (and it is x86_64)

---

### Post by dandnsmith on 2009-12-29
> **systemous said:**
> I have three questions. 

1) Every time i start the computer, i have to set the cpu frequency mode to Perfomance (from the CPU Frequency Scaling Monitor) for the two cores in order to work at max speed (3.0 ghz). Is it possible to make it run **only** at Performance?
I assume that this is in the BIOS settings? - if so, I don't know how to do it

> 2) I can see in the Sysinfo that the speed of my two cores are 3.0 ghz. I o/ced my cpu to 3.22. Why i can't see that speed in Sysinfo and why i can't set it in CPU Frequency Scaling Monitor? (it shows max speed 3.0 ghz)
If this is sysinfo provided by Ubuntu, I would expect it to accurately reflect whatever the real settings were - unless the BIOS doesn't report the adjusted settings.

> 3) In Ubuntu, the x86 means 32 bit and the x86_x64 means 64 bit?
That is correct.

---

