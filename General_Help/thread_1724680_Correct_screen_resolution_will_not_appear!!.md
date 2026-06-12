---
title: "Correct screen resolution will not appear!!"
date: 2011-04-08
forum: General Help
---

### Post by linuxuser12345 on 2011-04-08
Please help me! I just got a DVI cable so I can have a dual monitor setup, (one VGA, one DVI monitor), and when the DVI cable is plugged into our 20" widescreen, the correct resolution (1680 x 1050), a "No Signal" error message will appear on the monitor. When the resolution is lower with the DVI cable, it will show up, but everything will be a bit bold and blurry. 
When I plug our VGA cable into the VGA slot in this monitor, everything shows up fine.

Can somebody please help me?? Thank you!

My video card is an ATi Radeon HD 4250

---

### Post by Krytarik on 2011-04-08
Try following this guide:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

But you might need to pass the monitor's specs to the xserver by setting up a proper xorg.conf, in this case see this guide:
[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

Good luck!

---

### Post by linuxuser12345 on 2011-04-08
What do I do with the long strands of text like:
"grenage@ublt:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML..."?

Do I type it in a terninal, or do I do something else?? (sorry, I am learning! lol)

---

### Post by Krytarik on 2011-04-08
> **linuxuser12345 said:**
> What do I do with the long strands of text like:
"grenage@ublt:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML..."?

Do I type it in a terninal, or do I do something else?? (sorry, I am learning! lol)
```
lspci | grep VGA
```
is just a command to get the name of your video card/chip. You can simply run it in a terminal, but also at a console.

---

### Post by linuxuser12345 on 2011-04-09
okay. What is the difference between a terminal and a console? Also, I got this:
jeb@Kitchen-PC:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
jeb@Kitchen-PC:~$

---

### Post by Krytarik on 2011-04-09
> **linuxuser12345 said:**
> What is the difference between a terminal and a console?
The term "terminal" is usually referring to a terminal emulator *window* inside an xsession (i.e. Gnome or KDE), like "Accessories -> Terminal", whereas "console" is usually used for the command line of a VT (virtual terminal), which you get when you press Ctrl+Alt+F1, for example.

---

### Post by realzippy on 2011-04-09
..have you installed the ATI proprietary driver?

---

### Post by linuxuser12345 on 2011-04-09
Yes. I have used *both* the ATi utility to change the resolution, as well as the default utility on Ubuntu.

---

### Post by linuxuser12345 on 2011-04-09
Hey, can somebody please just take over my computer via the Remote Desktop Viewer?? This way, I can see exactly how to fix my computer.

---

### Post by Krytarik on 2011-04-09
Earlier PM-reply to a similar PM'd-request:

I'm aware that this would sometimes help to fix an issue a lot faster, or at all. And actually, I'm sometimes also eager to simply revert to that.

But not only do I not want to meddle that heavy into someone else's system (if it's not my family), but I also doubt that it would help the concerning user to learn how to fix it on her/his own. I know it from my long lasting experience in user support. If the actions are performed simply too fast for the user to
- follow
- write everthing down,
the user simply can't reproduce it on her/his own.

So, the coherent answer to your question is: I'm sorry, but no, I won't do this.

Follow the given guides and post any progress or questions in your thread, I'd love to help. And not at least it will help others, too, now and in future, by having a well documented process to solve this issue.

Best of luck and don't hesitate to post your progress/questions!

Regards
> **linuxuser12345 said:**
> Hey, can somebody please just take over my computer via the Remote Desktop Viewer?? This way, I can see exactly how to fix my computer.
Btw., I'm also fairly sure that this is against the policy of the forums, although I didn't find a reference to that right now, but I do remember having read it somewhere.

Regards

---

