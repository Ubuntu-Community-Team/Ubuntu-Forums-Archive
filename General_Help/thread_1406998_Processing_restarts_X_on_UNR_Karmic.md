---
title: "Processing restarts X on UNR Karmic"
date: 2010-02-14
forum: General Help
---

### Post by penguintutor on 2010-02-14
Is anyone using [Processing]("http://www.processing.org/") on UNR? Please let me know your experience good or bad and what hardware you are running on.

I am having problems running processing on my netbook, but could do with some more info to submit a bug report to the developers.

Whenever I try and run a windowed processing application in UNR on my EeePC 1000H I lose my session and end up at the login prompt. I assume X is crashing and being restarted. This only appears to happen on my Netbook and only when on UNR. It also only works when it's a windowed application. If I run the same application in fullscreen mode without the title bars etc. then it works fine.

It's not a problem with my code as this is happening using the Examples that are shipped with the PDE (Processing Development Environment) as well.

Processing works on 

Ubuntu desktop
Ubuntu Netbook Remix (UNR) running on my laptop as a Virtualbox VM
Fedora running on the same EeePC netbook as the problem is in UNR 

but not UNR on EeePC.

I am running processing 1.0.9 from the processing.org binaries.



I have searched the log files, but can't find anything meaningful. 

There are no messages for processing or X.org in the syslog.

I do have X.org logs, but they appear to be just giving X.org startup information, I can't see anything that jumps out as a problem with X.org. Maybe I'm missing something, but there doesn't appear to be any timestamps in the log so I'm not sure what I should be looking for.

Please let me know if anyone knows of any way of any issues or just of a way to get debug messages from either X or from Processing so I can submit a more meaningful bug report.

---

### Post by penguintutor on 2010-02-20
I've found a solution to the problem. 

Processing is designed for Java 1.5 and does not work correctly with JDK 1.6 (although it appears to work on the rest of my computers on 1.6).

To get it working I had to install JDK 1.5 and then link to that instead.

you have to jump through a few hoops to get to the appropriate download page on the Java site which I found at: [https://dct.sun.com/dct/forms/reg_us_0809_958_0.jsp]("https://dct.sun.com/dct/forms/reg_us_0809_958_0.jsp")

I then had to register to get a link to actually download the JDK (note must be JDK  - JRE is not sufficient).

Once downloaded I ran the .bin file as root into the /opt directory. Then deleted the java directory in processing and replaced it with the  following symlink:
sudo ln -s /opt/jdk1.5.0_21/ /opt/processing-1.0.9/java 

Now processing appears to work correctly.

My first attempt at processing programming is an interactive diode demonstration available at: [http://www.penguintutor.com/electronics/interactive-diode1]("http://www.penguintutor.com/electronics/interactive-diode1")

---

### Post by mlwalla on 2010-10-01
Having this same problem in the Desktop version and it is super frustrating!  Especially because it was fine for about half an hour of running sketches and examples, and then started rebooting X for no apparent reason. Are you sure it's a java6 problem?

---

