---
title: "Ubuntu installation error"
date: 2010-01-20
forum: General Help
---

### Post by cisco21c on 2010-01-20
Here's my story, I have a HP Pavilion dv1000 running WinXP Home. I wanted to bring some life into this thing as its over 5 years old so I decided I'd start off fresh with Ubuntu. 

Downloaded the latest version of Ubuntu, burned on a DVD since for some reason my laptop can't boot from CD's. Followed all the on screen instructions. However, upon installing Ubuntu, at around 80% or so I recieved an error message saying something. I don't remember exactly what it said but, I remember one of the last sentences saying "This can be due to overheating.." something like that. The screen went completely black, I could do nothing but shut it off and try again.

Since then, I've always been getting this error every single time I try to install Ubuntu:

[COLOR=Red]mountall: error while loading share libraries: /lib/libudev.so.0: cannot read file data: Input/output error

init: mountall main process (1075) terminated with status 127[/COLOR]

[COLOR=Black]I've tried erasing my laptops hard drive completely clean with [/COLOR]Dariks Boot and Nuke but, nothing seems to fix it. So as of right now I'm left with a laptop with no OS.

Any suggestions? :(


EDIT: My specs are as follows


[LIST]
[*]Microsoft(R) Windows(R) XP Home Edition with SP2 (not anymore)
[*]Intel(R) Pentium(R) M Processor 740 (1.73 GHz)
[*]14.0" WXGA BrightView Widescreen
[*]768 MB DDR SDRAM (2700) Upgradeable up to 2 gig
[*]60 GB 5400 RPM Hard Drive
[*]LightScribe 8x DVD+/-RW&CD-RW Combo w/Double Layer
[*]Intel(R) Graphics Media Accelerator 900 - Pentium
[*]Intel(R) PRO/Wireless 2200BG & Bluetooth(TM)
[*]6 Cell Lithium Ion Battery
[*]HP Mobile Remote Control
[/LIST]

---

### Post by PRC09 on 2010-01-20
After downloading do the following to ensure no corrupt files in the download.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then burn the iso to a CD-R (some older machines have problems with CD-RW)using your burning software at the lowest possible speed.

When you have achieved this and install the cd in the machine select the Check CD for defects first.This will test the cd for any file errors that could occur during the burn.

Once all this checks out you should enable you to install Ubuntu.This is assuming that your cd drive is working properly.....

---

### Post by PRC09 on 2010-01-20
Sorry just re-read but the same applies to dvd,having a problem with cd and not dvd doesnt sound good for the drive tho.....

---

### Post by synapsys on 2010-01-20
1. What speed did you burn cd at?

2. Did you use the "check for defects" option at boot menu?

---

### Post by cisco21c on 2010-01-20
I managed to get help in the IRC room, it seems I will be needing a IDE to USB cable to install Ubuntu on there off my main computer.

To answer questions: I burned at the slowest I could go (x4) and yes I did check for any errors and showed none.

---

