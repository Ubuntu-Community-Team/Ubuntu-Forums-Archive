---
title: "Ubuntu wont load"
date: 2010-02-27
forum: General Help
---

### Post by uShafee on 2010-02-27
Hai. I av just installed Ubuntu on my system using wubi along side Windows 7. But i cant get to load Ubuntu. The installation went through perfectly and after the reboot, I get the dual boot screen -> i choose ubuntu -> it shows another screen with options to select ubuntu, ubuntu on recovery mode and some other options -> i chose ubuntu.

Then it loads for a while and then just displays the background. (the one that was set as the background even while loading). I also have the pointer but nothing else. shouldnt there be other stuff?

What gives?

---

### Post by spiderbatdad on 2010-02-27
try booting with safe graphics. From the menu screen where you select to boot ubuntu, press f6.

---

### Post by uShafee on 2010-02-27
pressing F6 on that menu had no effect :/ I tried this on the first and the second dual boot menu (second one being the one with option to boot ubuntu in recovery mode).

---

### Post by spiderbatdad on 2010-02-27
I'm still trying to understand your installation. I have never used wubi, but having two boot menus seems very strange.
So, you use a boot loader to select wubi at startup, and when wubi/ubuntu starts, you get another grub menu. Sorry for the questions. Wubi support isn't as great as it could be here because few people use it. But hang in there and maybe your post will be found by the right person...Google is your friend, as well.

---

### Post by spiderbatdad on 2010-02-27
Does your installation offer a login screen at any time? I believe there, after selecting your username...there should be an options button (not labeled) on the bottom panel...from the options you might be able to select safe graphics.

---

### Post by uShafee on 2010-02-27
Yes. first it shows the default windows styled boot loader and then another menu.  I cant get to a login screen. I have yet to see anything of ubuntu except for the boot menus and the loading screen.

---

### Post by jmszr on 2010-02-27
uShafee,

I found this in another thread: [http://ubuntuforums.org/showthread.php?t=1417034](http://ubuntuforums.org/showthread.php?t=1417034) 
                           
Post #4
oldfred:

After you install it you will want to run this fix.

Fix for grub2 problem with wubi:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

It seemed like it might have some bearing on your issue.
__________________

---

### Post by uShafee on 2010-02-27
I m not so sure about that... It says i might face symptoms like

> The booting problems come in many different forms:
The Grub menu does not appear at boot up. Instead you get a "rescue: grub>" or "sh:grub>" prompt
The Grub menu appears, but trying to boot Wubi results in a kernel panic.
The Grub menu appears, but trying to boot Wubi results "file not found".

I faced none of the above. and i boot "okay".. Its just that where i believe a login screen should be, i get nothing. just the background and a pointer.

---

### Post by uShafee on 2010-02-27
I think i kinda figured the problem. My computer is ridiculously slow when booted with ubuntu. I waited for something like 5 minutes at the welcome screen to see if anything happens and i finally see the login screen.

Then i played around and found that it was just unacceptably unresponsive. It took a solid minute when i click 'other' on user select menu. Also when I hit the back button. same thing with everything else.

I m on an acer aspire 5580 - with ram upgraded to 1.5 GB. I think its a driver problem. If anyone else has had any luck.. do let me know. thanks

---

### Post by spiderbatdad on 2010-02-27
wubi installation is not a fair example of how ubuntu will run on your system. I use an acer aspire and ubuntu runs excellently on the hardware.
Perhaps you would consider a live cd of the desktop edition rather than wubi. You can install along side windows from the live cd. While testing Ubuntu from the live cd (without any changes to your computer) it will run slower because it is reading from the cd the whole time. But with a full desktop installation, I find windows cannot compete.

---

### Post by uShafee on 2010-02-28
solved.

---

### Post by uShafee on 2010-02-28
bump

---

