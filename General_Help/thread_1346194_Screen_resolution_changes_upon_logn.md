---
title: "Screen resolution changes upon logn"
date: 2009-12-04
forum: General Help
---

### Post by kchaturani on 2009-12-04
I am using nvidia card and the resolution when booting is setup for 1024x768. When I type the password and enter the screen gows black and the resolution changes to 800x600 when screen reappears. I have to manually setup the resolution every time. I have tried using *sudo*: *nvidia*-*xconfig and saving the xorg.conf but it does not solve the problem. I have attached the current xorg.conf for ref. Please help.*

---

### Post by madverb on 2009-12-04
I had the same problem quite some time ago. What I found fixed it was that the Gnome Display settings were interfering with the Nvidia Display settings.
I'm pretty sure to fix it I just went to System > Preferences > Display and selected Yes when it asked if I wanted to use the graphics card vendor's tools.
There might be more to it. I'll find the thread if you still have problems.

---

### Post by kchaturani on 2009-12-06
I am using nvidia settings tool only but that does not help.

---

### Post by madverb on 2009-12-06
Found how I fixed it.

[QUOTE=madverb]Even better! Just removed the ~/.config/monitors.xml and now it completely ignores the gnome settings! Login is also much smoother now. This is really damn annoying.[/QUOTE]

---

### Post by kchaturani on 2009-12-06
Thanks a ton, it worked like a charm!!!!!

---

### Post by Uadebisi on 2009-12-12
Hi,

Can one of you explain to me exactly how to implement what has been suggested? I have been having the same problem & can't seem to find the solution & am new to Ubuntu.

Also, found gucharmap.desktop in my rash but didn't put in there but seems to be related. Can either of you offer an explanation?

Thanks!

---

### Post by madverb on 2009-12-13
Open a terminal and type
```
rm ~/.config/monitors.xml
```

---

### Post by Uadebisi on 2009-12-13
Hi,

Happy to hear back from you :)

I have learned some more of my machine & its issues. I am hoping you can still help me.

I learned that I do not have an Nvidia card but a:
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

So, apparently the Nvidia commands will not help me...from what I gather. So does this mean that this won't help me either? 

> rm ~/.config/monitors.xml

I am having a heck of a time finding an answer to my problem. 

Thanks!

---

### Post by Uadebisi on 2009-12-14
Here's what I did to fix my problem... keeping in mind that I use Grub2 so all I had to do was download "Startup Manager" from the "Software Center" & adjust the settings in the GUI:

> originally posted by** trx64: **I've solved the problem by disabling KMS (Kernel Mode Setting) in Intel driver, leaving the detection of my screen resolution just with X. There is no need to change xorg.conf, just leave it at default values.

Edit the file /boot/grub/menu.lst (if you have GRUB 2, use [Startup Manager]("apt:startupmanager")). In the end of the "kernel" line of the OS entry, add "nomodesetting":

     Code:
     title           Ubuntu 9.10, kernel 2.6.31-14-generic
root            (hd0,4)                              
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=92583a31-1693-438c-ae3f-61ab9b8ca13a ro quiet splash locale=pt_BR **nomodesetting**                                       
initrd          /boot/initrd.img-2.6.31-14-generic                                   
quiet 



See [http://ubuntuforums.org/showthread.php?t=1308745](http://ubuntuforums.org/showthread.php?t=1308745)

---

