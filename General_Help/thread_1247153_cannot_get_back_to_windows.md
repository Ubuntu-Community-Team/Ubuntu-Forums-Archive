---
title: "cannot get back to windows"
date: 2009-08-22
forum: General Help
---

### Post by fboxall on 2009-08-22
I had windows xp pro, I partitioned my hard drive, windows on one half ubuntu 9.04 on other half.  On start up I would get a screen to choose ubuntu or windows.  I used both and everything worked well for several months.  However, I have managed to screw it up.  Now the start up screen does not give me the windows choice, so I cannot get to windows.  I typed c and got grub> prompt, so I typed "run windows" and got "error 27 unrecognized command".  I typed "boot windows" and got "error 8 kernel must be loaded before booting".  I don't know how to do that.
I need some kind soul to tell me how to get back to windows.  Please bear in mind that I my computer skills are rudimentary.

---

### Post by Yossi Gil on 2009-08-22
Can you provide your "menu.lst" file?

---

### Post by JOHNNYG713 on 2009-08-22
Hi, boot into repair mode (your second from the top ubuntu boot option on your grub screen) and click update grub boot loader, see if that will reset your windows access.

---

### Post by gastly on 2009-08-22
Please post your 'menu.lst' file.
Open up a terminal (Applications->Accessories->Terminal) and type:
```
cat /boot/grub/menu.lst
```
Then paste the output of the command here.

---

### Post by apparle on 2009-08-22
We will help you fix it but for that we need the following information
The output you get when you open terminal and enter 'sudo fdisk -l' and press enter

Also post/attach the contents of file  /boot/grub/menu.lst

---

### Post by fboxall on 2009-08-22
to JohnnyG713 - I tried "update grub boot loader" Did not work. Thanks anyway.
To Yossi Gil, gastly, apparle - attachment A is the response to cat /boot/grub/menu.lst.  attachment B is the response to sudo fdisk -l.

---

### Post by AmerNewbieInDE on 2009-08-22
looks to me, when you partitioned your hard drive, you wiped out your windows.

---

### Post by michy99 on 2009-08-22
From the look of your menu.lst file, you should get a choice for windows at the bottom of you grub menu. When the menu comes up, keep pushing the down arrow until it won't go any further. you may just have so many entries in your menu that it is below the bottom of your screen.

---

### Post by apparle on 2009-08-23
Its possible that there are so many ubuntu entries( for each kernel upgrade) that you are not seeing the windows enry even though it is present.

Delete some old ubuntu kernel entries that you don't need, and you will be able to see the windows entry.

Else you can try to execute following commands in sequence at the grub prompt
```
root (hd0,0)
savedefault
makeactive
chainloader	+1
boot
```

If both of them don't work then you seem to have screwed your windows partition

---

### Post by fboxall on 2009-08-23
to michy99 and apparle -- you got it right, the windows choice was really there all along.  It was hidden below the bottom of the window because of too many choices above it. I just didn't scroll far enough.  Thanks so much for solving my problem.  I often say that owning a computer is a continual learning experience.  From this incident I learn that there is no limit to my own stupidity.  I am hugely embarrassed and hugely grateful that this forum was available.

---

