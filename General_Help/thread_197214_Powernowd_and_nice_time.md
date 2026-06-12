---
title: "Powernowd and nice time"
date: 2006-06-15
forum: General Help
---

### Post by Ramses de Norre on 2006-06-15
Just a quick question: why doesn't powernowd raise the cpu frequency while the usage is 100% in nice time? For some reason prelink runs in nice (in fact I don't know what this nice thing is) and uses 100% cpu, but my cpu stays scaled at the lowest frequency.. user or sys time running processes make the frequency raise as it should.
Any ideas or explication why this is configured like it is?

---

### Post by gotthardt on 2006-06-15
This is by design. A process running at 'nice' (even 100% usage) should not cause the processor speed to advance to full. For example a screensaver kicks in as a 'nice' process - you don't need full speed for that. 

Now, if you do want powernowd to include 'nice' processes you can easily add an option -n when starting powernowd. Or, set the options that you want in a file called : /etc/default/powernowd

Example contents:
OPTIONS="-q -n"


Available Options:
	-h	print help message
	-d	don't detach from terminal (default is to
		detach and run in the background)
	-v	Increase output verbosity, can be used more than once. 
	-q	Quiet mode, only emergency output.
	-n	Include 'nice'd processes in calculations
	-m #	Modes of operation, can be 0, 1, 2, or 3:
		0 = SINE, 1 = AGGRESSIVE (default), 2 = PASSIVE, 3 = LEAPS
	-s #	Frequency step in kHz (default = 100000)
	-p #	Polling frequency in msecs (default = 1000)
	-u #	CPU usage upper limit percentage [0 .. 100, default 80]
	-l #    CPU usage lower limit percentage [0 .. 100, default 20]

---

### Post by Ramses de Norre on 2006-06-15
Oh I see, and is it possible to stop prelink running in nice? Because I see the sense of the powernowd behaviour but prelink is quite a heavy process and I'd like it to run at full cpu power to finish as soon as possible.

---

### Post by gotthardt on 2006-06-15
There are some specifics about using nice or renice in here:
[http://www.ubuntuforums.org/archive/index.php/t-1971.html](http://www.ubuntuforums.org/archive/index.php/t-1971.html)

From the link:
Have a look at /etc/cron.daily/prelink. There is a line right at the beginning which says:
renice +19 -p $$ >/dev/null 2>&1
You can change the "+19" into -5 and that will make it not so nice ;)

---

### Post by Ramses de Norre on 2006-06-15
Ok, it's set to -5 =)
What exactely does this value indicate?

---

### Post by gotthardt on 2006-06-15
I don't know the exact definition, but positive values make the process run 'nice' so they don't hog the processor time and let other processes run - negative values make the process get more CPU time.

see this handy link:
[http://linux.about.com/library/cmd/blcmdl1_nice.htm](http://linux.about.com/library/cmd/blcmdl1_nice.htm)

---

### Post by Ramses de Norre on 2006-06-16
Hmm I noticed -5 is way too high, most other processes run with 0.
So I've set prelink to +1 to not disturb things like amarok (very annoying when music stops..)
I'm going to be testing and tuning this value =)

---

