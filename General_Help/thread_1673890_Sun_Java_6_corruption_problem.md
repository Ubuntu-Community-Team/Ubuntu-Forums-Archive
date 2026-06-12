---
title: "Sun Java 6 corruption problem"
date: 2011-01-23
forum: General Help
---

### Post by carusoswi on 2011-01-23
Have recently installed Ubuntu Desktop 10.10.  Could not make Logmein work, and had, in the past, solved this by stepping back in Java to previous versions.  Tried to remove Java 6 with Synaptic, but the process stalled when Java through up a window containing a user license agreement that ended with <OK> acceptance that cannot be clicked or otherwise acknowledged.  The top right area of this window shows that Java is working (I forget the exact text, but the indication is that the routine is running).

Clicking to close this window changes that upper-right-hand message to an admonition that the process cannot be stopped while in process.

I can x-kill it or restart to kill it, but, now Synaptic shows Java 6 corrupted.  It offers a line of code to fix the problem which, when run in the terminal, does allow synaptic to open, and I can install/uninstall other aps as I wish.  However, Java 6 is showing a state that needs to be updated.  If I try to update it in Synaptic, the same Java acceptance screen appears, and the process starts all over again.

I know I could run a clean install to fix this, but would prepare not to do this.

Can anyone offer advice for a fix?

Is it possible for me to drop back to Java 5?  I see on Sun's site that it is no longer supported.

My only issue (if even valid) with Sun Java 6 is that I cannot get Logmein to run (I seem to have this problem whenever I move to the next Ubuntu release).

Thanks in advance for any suggestions.

Caruso

---

### Post by gandaran on 2011-01-23
> . If I try to update it in Synaptic, the same Java acceptance screen appears, and the process starts all over again.

you have a problem with the synaptic graphical sun-java licence acceptance window? this is the first time I see a post with this problem, normally users encounter and post this problem with the 'OK' button when installing sun-java using the command line apt-get but never using the graphical way which you just use the mouse to tick the licence box or click the button
ins't there any chance you are using apt-get to install and not synaptic?
sorry if this didn't help but I have no other solution to the problem.

---

### Post by carusoswi on 2011-01-23
> **gandaran said:**
> you have a problem with the synaptic graphical sun-java licence acceptance window? this is the first time I see a post with this problem, normally users encounter and post this problem with the 'OK' button when installing sun-java using the command line apt-get but never using the graphical way which you just use the mouse to tick the licence box or click the button
ins't there any chance you are using apt-get to install and not synaptic?
sorry if this didn't help but I have no other solution to the problem.

No, I am using Synaptic.  I was hoping for someone to post some code that I can use in the terminal to correct my problems.

Thanks for your reply.

Caruso

---

### Post by gandaran on 2011-01-23
> **carusoswi said:**
> No, I am using Synaptic.  I was hoping for someone to post some code that I can use in the terminal to correct my problems.

Thanks for your reply.

Caruso
okay,
try the command line to install sun-java then to see what happens
```
sudo apt-get install sun-java6-plugin
```
post the errors if any or if you get to the licence window use the keyboard to highlight the 'OK' button and press enter.

---

### Post by carusoswi on 2011-01-23
> **gandaran said:**
> okay,
try the command line to install sun-java then to see what happens
```
sudo apt-get install sun-java6-plugin
```
post the errors if any or if you get to the licence window use the keyboard to highlight the 'OK' button and press enter.


Running in the terminal, after a bit, I am presented with a y/n choice to proceed, then, after a bit more, a grey box with a blue outline appears.  Center of top text is in red - configuring sun-java6-jre.

Then, in black text, 'Operating Distributor License for Java v1.1 (DLJ)'

and then, the same message repeated except 'v' is replaced with spelled out 'version'.

Then, a blurb about acceptance followed by <ok> centered at the bottom of the box.

There is no clicking this <ok> since it is text in the terminal.

No other input from me possible.

The only action available to me is to close the box.  I get a message that doing so will end the operation.

. . . and then, although I haven't tried it, I am certain I will have a broken package when I try to open Synaptic.

Thanks again for your help.
Caruso

---

### Post by carusoswi on 2011-01-23
Actually, Synaptic will not open because 'another packaging manager' is running.  I will have to re-boot.

Caruso

---

### Post by carusoswi on 2011-01-23
Opening Synaptic after reboot gives this warning:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

which I have seen in past passes through this 'circle'.

If I run the code suggested, then, Synaptic will open, and Sun Java will be on my list of packages needing an upgrade.

I've tried marking it for complete removal, but the process will not complete.

Caruso

---

### Post by carusoswi on 2011-01-23
Ok, I gave up on this problem and re-installed Ubuntu 10.10 cleanly.  
Thanks for your assistance.
Caruso

---

