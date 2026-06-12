---
title: "out of range message?!"
date: 2012-04-21
forum: General Help
---

### Post by geekhush on 2012-04-21
hi, i just recently installed ubuntu 11.10 on my machine, which runs a windows 7 os, i intended it to be a dual boot and did as planned, i installed ubuntu using a usb stick after i did so, i couldn't see the grub menu from where i was to select the OS i wanted to boot, so then i thought i had messed up with grub or something and searched on how to solve this problem, but then just now i noticed something that i thought was just nothing out of the normal. i.e when i boot my computer at first it loads normally but then a message pops us saying "out of range" and boots into ubuntu, i tried to press the arrows key and then the message would stay, then i pressed the "down" key for a while and pressed enter, i booted in to WINDOWS, this is utterly something new to me, why is this happening and can anyone help me solve it and also help me understand the problem. :)

---

### Post by 3Miro on 2012-04-21
"Out of range" is a message from your monitor that it has lost connection to your computer.

1. What is your video card?
2. What kind of monitor do you have?
3. What connection are you using (i.e. D-Sub, DVI, HDMI)?
4. Have you completely updated Ubuntu? This may be fixed by an update.

---

### Post by wildmanne39 on 2012-04-21
Hi, this is how you fix it.
```
gksudo gedit /etc/default/grub
```
and change this line:

```
#GRUB_GFXMODE=640x480
```

to this:

```
GRUB_GFXMODE=640x480

```
Then save and exit the document.
Then do:
```
sudo update-grub
```
reboot

---

### Post by geekhush on 2012-04-23
Hi [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") it worked, thanks a lot :)

---

### Post by wildmanne39 on 2012-04-23
Hi, your welcome! glad I could help.

---

