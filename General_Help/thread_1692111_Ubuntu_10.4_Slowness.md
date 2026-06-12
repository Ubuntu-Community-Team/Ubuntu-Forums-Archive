---
title: "Ubuntu 10.4 Slowness"
date: 2011-02-20
forum: General Help
---

### Post by Highlander0689 on 2011-02-20
I just recently installed Ubuntu 10.4 on my EEE PC. However, it has been running very slowly. Whenever I scroll up and down a page, there's massive tearing, and the pages lag very noticeably behind my movements with the scroll bar.  Also, when I'm viewing flash videos on a site like youtube (in chrome and FF), there is massive tearing there too. Are there any solutions to this issue?

Specs:

Processor: 2x Intel(R) Atom(TM) CPU Z520 @ 1.33GHz
Memory:    1016MB
Operating System: Ubuntu 10.04.2 LTS
Video:     Intel Graphics Accelerator 


-The tearing is driving me nuts, please help.

---

### Post by Highlander0689 on 2011-02-20
bump... Please help.

---

### Post by Bucky Ball on 2011-02-20
Are you using a graphics driver? System>Administration>Additional Drivers.

---

### Post by steve161 on 2011-02-20
Not familiar with your system, but sytem-preferences-system monitor, and see what process may be using a lot of cpu or memory.  Also, system-preferences-appearance-visual effects, and check "none".  If there is no change, at least you can rule out compiz for the slowness.

---

### Post by CHRSB on 2011-02-21
[FONT=Courier New]I have 10.10 running on my 1001p (1.6ghz) and Firefox runs fine. I do get the tearing and lagging in Debian until I upgrade the kernel. It seems to be worse when there is a flash element on the page.

How about installing 10.10 on a small slice of your drive to see if that fixes it?

You can also try and install the 2.6.36 kernel on 10.10
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)

You need to download the image and two header .debs for your architecture.

But yes, I would try 10.10.
[/FONT]

---

### Post by Highlander0689 on 2011-02-21
I just checked and I am not using a graphics driver... 


Also, the visual effects option was set to none to start with. 


There is no "system monitor" option under preferences. 


I actually had 10.10 installed earlier, but it was just as slow if not slower than 10.4 has been.

----Hopefully this information is sufficient, and thanks for all your help.

---

### Post by Highlander0689 on 2011-02-21
Bump... Please help, the tearing is killing me.

---

### Post by keithpeter on 2011-02-21
Hello Highlander

Which EeePC is it? I have the 1000 (SSD drives, Atom processor) and am not seeing these things. I have Puredyne 9.11 on there at present but can boot off a USB and get hardware profiles if that would help.

---

### Post by CHRSB on 2011-02-21
> **Highlander0689 said:**
> Bump... Please help, the tearing is killing me.

I did help you. Why are you ignoring what I said? Upgrade to 10.10 and upgrade the kernel. You might have had 10.10, but did you have the 2.6.36 kernel? The 2.6.36 kernel has updated drivers for the video.

[http://ubuntuforums.org/archive/index.php/t-1591565.html](http://ubuntuforums.org/archive/index.php/t-1591565.html)

And can you give us the terminal output of these two commands:

lsmod |grep video
lspci

and 
sudo apt-get install mesa-utils
and run
glxgears
in a terminal and tell us the frame rate.

---

### Post by CHRSB on 2011-02-21
Jeez, I am getting ready to leave this forum because it is just filled with people who do not know how to use Google and who do not know how to write information down to get help from others.

This might help your video issue. I found it using google. I am assuming, since you never told us, that you have an Asus EEE PC 1201HAB? 

[http://www.google.com/search?q=eeepc+1201hab+ubuntu&hl=en&prmd=ivnsfd&ei=C9JiTf_eMYS4sQPXsbCqBA&start=10&sa=N](http://www.google.com/search?q=eeepc+1201hab+ubuntu&hl=en&prmd=ivnsfd&ei=C9JiTf_eMYS4sQPXsbCqBA&start=10&sa=N)

revealed 

[http://code.google.com/p/gma500/wiki/PPARepository](http://code.google.com/p/gma500/wiki/PPARepository)

---

