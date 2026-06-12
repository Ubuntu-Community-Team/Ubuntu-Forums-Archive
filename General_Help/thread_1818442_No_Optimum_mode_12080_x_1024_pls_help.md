---
title: "No Optimum mode 12080 x 1024 pls help"
date: 2011-08-04
forum: General Help
---

### Post by Art_88 on 2011-08-04
Greetings ubuntu members. I have recently been trying to install ubuntu 11.04 on my old computer and I installed ubuntu with no problems but everytime it takes me to grub, the monitor will turn black in 2-3 mins with a message saying Not Optimum mode 12080 x 1024. I suspect that this maybe a video card problem? I have a Radeon 9250 video card. I'm new to Linux and I would really appreciate some advices. Thanks in advance!

---

### Post by xdominex on 2011-08-04
Have you tried booting into safe graphics mode and installing the proprietary graphics driver for ATI?

With regards,
XDomineX

---

### Post by Art_88 on 2011-08-05
I can't even get past grub because everytime I click the OS to boot the screen just goes blank.. Is there a way to boot to safe graphics mode in GRUB?

---

### Post by xdominex on 2011-08-05
The "(recovery mode)" option for Ubuntu in the GRUB menu should have a fallback graphics option when you boot into it. If not, select the option to drop to a root terminal with networking (you may need to use an ethernet cable for this), install the proprietary graphics driver there, and try to reboot normally (the command "reboot" gets the job done in terminal). This is the command for installing the proprietary ATI driver:
```

apt-get install fglrx fglrx-amdcccle

```

Let me know how things work out.

With regards,
XDomineX

---

### Post by jwbrase on 2011-08-05
> **Art_88 said:**
> Greetings ubuntu members. I have recently been trying to install ubuntu 11.04 on my old computer and I installed ubuntu with no problems but everytime it takes me to grub, the monitor will turn black in 2-3 mins with a message saying Not Optimum mode 12080 x 1024. I suspect that this maybe a video card problem? I have a Radeon 9250 video card. I'm new to Linux and I would really appreciate some advices. Thanks in advance!

Just making sure: Is it actually saying "12080 x 1024" and not "1280 x 1024"? I don't want to lead you down a rabbit trail because you mistyped "1280" as "12080", but if it is actually trying to get a horizontal resolution of 12080, something is badly misconfigured, as I don't think any monitor or any video card will handle that. The question is which configuration file the bad setting is coming from.

Just to make sure I'm understanding this right: You *are* getting a grub menu screen, but as soon as you try to boot anything you get the "Not Optimum mode" problem, right?

In that case, when you get to the menu, select an entry and hit "e". You should get a screen something like this: [IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.menu.edit.png[/IMG].

If you see "12080x1024" anywhere, change it to "1280x1024". Don't change anything else. Then hit Ctrl-X to boot. If you don't "12080x1024" anywhere, or if "12080" in your original post was a mistype, then this won't help you.

If that works, when you get to your desktop, hit Alt-F2 and type "gksudo gedit /boot/grub/grub.cfg". Look through the file, and, anytime "12080x1024" appears, replace it with "1280x1024". Do *not* change anything else, or you may cause other problems. That should fix it.

---

### Post by Art_88 on 2011-08-05
I do apologize for the mistake. It does say 1280 x 1024 and not "12080". It doesn't give me an option to change the settings on GRUB and I've spent countless hours finding a solution for this problem. Even when I choose the 2nd option which is the recovery mode, it will execute a bunch of commands but when its done, I just end up having a distorted screen. I don't want to spend mopney on another graphics card if there is a solution for this problem. Thank you for replying and pls let me know any suggestions.

---

### Post by Art_88 on 2011-08-05
> **jwbrase said:**
> Just making sure: Is it actually saying "12080 x 1024" and not "1280 x 1024"? I don't want to lead you down a rabbit trail because you mistyped "1280" as "12080", but if it is actually trying to get a horizontal resolution of 12080, something is badly misconfigured, as I don't think any monitor or any video card will handle that. The question is which configuration file the bad setting is coming from.
 
Just to make sure I'm understanding this right: You *are* getting a grub menu screen, but as soon as you try to boot anything you get the "Not Optimum mode" problem, right?
 
In that case, when you get to the menu, select an entry and hit "e". You should get a screen something like this: [IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.menu.edit.png[/IMG].
 
If you see "12080x1024" anywhere, change it to "1280x1024". Don't change anything else. Then hit Ctrl-X to boot. If you don't "12080x1024" anywhere, or if "12080" in your original post was a mistype, then this won't help you.
 
If that works, when you get to your desktop, hit Alt-F2 and type "gksudo gedit /boot/grub/grub.cfg". Look through the file, and, anytime "12080x1024" appears, replace it with "1280x1024". Do *not* change anything else, or you may cause other problems. That should fix it.
 
Also, I don't know if this will matter but when I boot with my live CD, I'm able to boot into desktop by hitting f6 and placing an "x" on nomodeset.

---

### Post by wildmanne39 on 2011-08-05
Hi, here is a link for nomodeset options, you will need to use it to boot so you can install your driver or find out what the problem is.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by xdominex on 2011-08-06
Is the distorted screen in recovery mode a usable one, though? If so, have you tried my suggestion of installing the proprietary graphics driver?

---

### Post by Art_88 on 2011-08-06
> **xdominex said:**
> Is the distorted screen in recovery mode a usable one, though? If so, have you tried my suggestion of installing the proprietary graphics driver?
 
Hi sorry for the late response. I tried what you suggested but no success. But I got it working by editing the boot option and deleting "splash vt.handoff=7" and replacing it with "nomodeset" without the quote. When I got to the desktop, I went to the grub file by following the instructions on the link provided by the other poster and deleting splash and replacing it with nomodeset and updating grub to make it permanent everytime I log in. NOw my ubuntu is working fine. Thank you all for your help with this you guys are awesome :)

---

### Post by wildmanne39 on 2011-08-06
Hi, your welcome! I am glad you got it working,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

