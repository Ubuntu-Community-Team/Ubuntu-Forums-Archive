---
title: "Grub problem"
date: 2009-11-29
forum: General Help
---

### Post by gramsyn on 2009-11-29
I am using Ubuntu 9.10. Suddenly, the screen froze and I shut the PC down. From that time, when I try to enter, the grub loads, but I have no keyboard at that screen and the system sticks there. Ubuntu should load automatically, but it doesn't. This is not a problem of keyboard. When I enter BIOS, it is working properly.

I have an installation CD and from there, I can load Ubuntu and everything works fine. Can I perform any settings in the Grub from there to solve the problem

Thanks in advance

---

### Post by sensay on 2009-11-29
[]("http://ubuntuforums.org/showthread.php?t=224351")[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Tried there?

---

### Post by gramsyn on 2009-11-29
Thanks for the link. However it isn't working.

I load the LiveCD. I type in the terminal sudo grub but it cannot recognise it. I typed grub (without sudo) and it asked me to install grub. I followed directions and was installed. Then I had a "grub" prompt. I print:
find /boot/grub/stage1 and it returns: "file not found"

what should I do?

---

### Post by Leppie on 2009-11-29
At the Gentoo forums they seem to have an extensive troubleshooting guide for GRUB issues. Have a look at [this page]("http://forums.gentoo.org/viewtopic.php?t=122656"). There's 7 sections for GRUB issues, listed at the beginning of the thread.

---

### Post by gramsyn on 2009-11-29
I am sorry, but is there any easier way to give me some advise. I cannot follow these instructions!

---

### Post by sensay on 2009-11-29
Sounds like your using grub2, the procedure is somewhat different for that than for grub1. I dont know off hand the commands to reinstall grub2. I can have a look or you could google/someone else may post with the commands.

Cheers

---

### Post by gramsyn on 2009-11-29
The Grub I am using is 1.97~beta4 if it helps. Thanks anyway

---

### Post by sensay on 2009-11-29
Yep, thats grub2

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I think simply reinstalling grub from the live cd should be sufficient

---

### Post by gramsyn on 2009-11-29
It was a very good link. Thank you. I re-installed the Grub, but the same thing happens when I restarted. Any more ideas???

---

### Post by sensay on 2009-11-29
Sorry, i dont really have a good knowledge of grub2 problems, i really hoped that thread would have the solution for you. Guess its up to someone else now :)

Good Luck

---

### Post by gramsyn on 2009-11-29
Thank's a lot for your help. One last question. can I install the older version of Grub (maybe it is working?)

---

### Post by sensay on 2009-11-29
I saw a thread today about downgrading grub2 to grub1 but it wasnt for the fainthearted, other than that i wouldnt really know.

At this point, is reinstallation of ubuntu itself out of the question? If you wanted grub1 you could just install 9.04 then manually upgrade to 9.10 if you chose.

---

### Post by gramsyn on 2009-11-29
Is there any way to install Ubuntu 9.10 over ubuntu 9.10 without affecting my files and settings? I tried from the install icon in LiveCD, but it will install from scratch

---

### Post by sensay on 2009-11-29
Is your home folder a seperate partition? Mine is and thusly i can reinstall ubuntu and keeping the same partitioning my files stay intact. The paths change slightly (youll find them alongside /home not inside /home) but as long as you dont format the /home partition before you select it for use it should be fine

Pretty sure you'd have to change your settings again though.

Please bare in mind im a pretty new linux user too and am just giving you the knowledge i have acrued since i started, it goes without saying that there are probably other better ways, im just telling ya what i know

---

### Post by gramsyn on 2009-11-29
Thanks for your time. You were very helpful

---

### Post by oldfred on 2009-11-29
I had a problem with old grub where keyboard & mouse worked in BIOS and Ubuntu but not in grub. It turned out to be the USB settings in BIOS for the keyboard & mouse. I would check them just to be sure.

---

