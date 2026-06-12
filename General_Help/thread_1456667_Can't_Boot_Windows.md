---
title: "Can't Boot Windows"
date: 2010-04-17
forum: General Help
---

### Post by Hman242 on 2010-04-17
I just installed GRUB along with Ubuntu. When I boot and access GRUB and try to boot Win7, it starts but after a few seconds it reboots. I really don't want to loose Windows, please help.

---

### Post by chris.jericho on 2010-04-17
what version of Ubuntu do you use??

---

### Post by Hman242 on 2010-04-17
I'm using Ubuntu 10 Beta 2.

---

### Post by chris.jericho on 2010-04-17
due to the beta version you may be getting some problems.... I am assuming you have used Grub2 and not the legacy version right?
just check if you've installed the right version... if no then.. update it and restart.

---

### Post by Hman242 on 2010-04-17
I don't think updating GRUB will help, and yes I have GRUB2. GRUB can boot Windows, but after being on the starting screen for a few seconds, it reboots. I believe this is more of Ubuntu's fault.

---

### Post by chris.jericho on 2010-04-17
check this thread..... you may get some help from here...

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by garvinrick4 on 2010-04-17
> **Hman242 said:**
> I just installed GRUB along with Ubuntu. When I boot and access GRUB and try to boot Win7, it starts but after a few seconds it reboots. I really don't want to loose Windows, please help.
Here is a link to help you out. Did you install manually? Or did you let gparted do it for you? I have installed a lot of partitions with 7 installed and no problems. Last page of install has a advanced tab make sure you pick sda as choice if you do manually.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by chris.jericho on 2010-04-17
> **garvinrick4 said:**
> Here is a link to help you out. Did you install manually? Or did you let gparted do it for you? I have installed a lot of partitions with 7 installed and no problems. Last page of install has a advanced tab make sure you pick sda as choice if you do manually.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
hey... yeah bro that will help...... that was the same thread that I had started  ;)

---

### Post by wilee-nilee on 2010-04-17
I would post the famous bootscript so that those that are the best helpers in this area can get you where you want to be.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This script will give you all the information needed in one shot.

---

### Post by Hman242 on 2010-04-17
When I put in 
```
bootrec.exe /fixboot
``` repair Win7, it says
```
This volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and  that the volume is not corrupted.
```What do I do? Before having the  option of choosing Command Prompt, it didn't pick up my OS. I didn't  load any driver and just clicked next. If I did need to do that, then  where would I find the one(s?) I need to load?

---

### Post by wilee-nilee on 2010-04-17
> **Hman242 said:**
> When I put in 
```
bootrec.exe /fixboot
``` repair Win7, it says
```
This volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and  that the volume is not corrupted.
```What do I do? Before having the  option of choosing Command Prompt, it didn't pick up my OS. I didn't  load any driver and just clicked next. If I did need to do that, then  where would I find the one(s?) I need to load?

Post the boot script it sounds like boot is set on the wrong partition, if you mess around to much you may create a unbootable W7 be careful.

Although the links for fixing are good information, if your computer has some things wrong those instructions may not work until you fix some things.

bootrec.exe /fixboot[
this should be BootRec.exe /fixmbr
this will load W7 as the bootloader if all is good then you will have to reinstall grub. But post that script or at least sudo fdisk -l

---

### Post by Hman242 on 2010-04-17
Afraid I deleted Ubuntu from the computer I am doing this on. As for 
```
bootrec.exe /fixboot
```
needing to be
```
bootrec.exe /fixmbr
```
I've tried both of those, it says the later works but I still have the problem.  I'm going to go post in the MS support forum or contact MS themselves, but I will still be watching for posts here as well.

---

### Post by wilee-nilee on 2010-04-17
> **Hman242 said:**
> Afraid I deleted Ubuntu from the computer I am doing this on. As for 
```
bootrec.exe /fixboot
```
needing to be
```
bootrec.exe /fixmbr
```
I've tried both of those, it says the later works but I still have the problem.  I'm going to go post in the MS support forum or contact MS themselves, but I will still be watching for posts here as well.

Alright, if you look through this forum though you will find many more threads on this same topic, generally it is fixed by posting more information, I am a little perplexed as to why you wont do this, oh well good luck.

Windows 7 forums is a good place.
[http://www.sevenforums.com/](http://www.sevenforums.com/)
The site admin Brink has a lot of threads on fixing and tweaking look in his thread posts.

---

### Post by Hman242 on 2010-04-17
I _can't_ add the information by typing in your terminal command as I no longer have Ubuntu on that system. As for other information, the following is all I can tell you.

When I try to boot up Windows, it start to boot but after a few seconds  it reboots the computer. After this happens, it asks if I want to boot  normally or use the startup repair. If I try to start normally, this  happens again. If I try to use the startup repair, it says to insert the  disk(which I have tried and doesn't fix the problem) and it gives me  info on the problem. It says that "The boot selection failed because a  required device is inaccessible". I am not able to do anything else.

---

### Post by chris.jericho on 2010-04-17
> **Hman242 said:**
> I _can't_ add the information by typing in your terminal command as I no longer have Ubuntu on that system. As for other information, the following is all I can tell you.

When I try to boot up Windows, it start to boot but after a few seconds  it reboots the computer. After this happens, it asks if I want to boot  normally or use the startup repair. If I try to start normally, this  happens again. If I try to use the startup repair, it says to insert the  disk(which I have tried and doesn't fix the problem) and it gives me  info on the problem. It says that "The boot selection failed because a  required device is inaccessible". I am not able to do anything else.
Your Windows partition has been destroyed.....

You have no other option other than reinstalling the OS again...

---

### Post by wilee-nilee on 2010-04-17
> **chris.jericho said:**
> Your Windows partition has been destroyed.....

You have no other option other than reinstalling the OS again...

How do you know that, that is ridiculous, you can not prove that

Okay OP the bootscript if you look at the link is run from a live cd. And is appropriate even if your just running windows.

You might also consider taking a screen shot of gparted from the live cd so we can see what the hard drive looks like.

Also if you don't want to lose anything or possibly recover from W7 a Ubuntu live CD is very useful.

---

### Post by Hman242 on 2010-04-17
> **chris.jericho said:**
> Your Windows partition has been destroyed.....

You have no other option other than reinstalling the OS again...
Haha, very funny. I know for a fact that it's not deleted/destroyed.

At Willie, on the bootscript site it says " Boot into any Linux based operating system".

At your edit, I don't have anything important on it, it's brand new. I'll take a screenshot within 30 minutes or so.

---

### Post by wilee-nilee on 2010-04-17
> **Hman242 said:**
> Haha, very funny. I know for a fact that it's not deleted/destroyed.

At Willie, on the bootscript site it says " Boot into any Linux based operating system".

At your edit, I don't have anything important on it, it's brand new. I'll take a screenshot within 30 minutes or so.

You saw this though correct
Boot into any Linux based operating system, **LiveCD** or LiveUSB.

I think in the end this can be fixed the W7 forums are very good. There is a thread on how to remove the 100mb w7 boot partition and reinstall it into the main running partition, in case that the problems may need some custom tweaking, post over there Brink is very helpful.

The one question here which is important is did you resize the W7 partition with anything other then the W7 disk management?

---

### Post by Hman242 on 2010-04-17
No, I used Disk Management to resize the Win partition and make another for Ubuntu. I was still able to use Windows too, only after installing Ubuntu did this problem arise.

---

### Post by Hman242 on 2010-04-18
I phoned HP, did all I could, and had to go to Best Buy to exchange the computer. I would still much rather use Ubuntu, but I need Windows for various things. What could have possibly gone wrong with the Ubuntu installation to make that happen? I would like to try again.

---

### Post by Native Dialect on 2010-04-18
Question. 

Does your GRUB Menu offer you multiple variations to boot into? 

E.g. 

ubuntu x86
ubuntu x86
Windows Vista (Loader)
Windows Vista (Loader)

I don't use GRUB 2, so I am not sure how the boot menu looks. And perhaps I am not understanding the scope of your issue, but it needs to be asked for clarity. If your menu looks like that, are you selecting the first Windows option repeatedly, or have you tried both? 

Second question.

Did you partition your drives, install Ubuntu, and then uninstall Ubuntu? That can also cripple your ability to boot into Windows, if you have allowed GRUB to overwrite your MBR. If that is the case, then all you have to do is put your Windows disc into your drive tray (make sure your BIOS is set to boot from disc first), and reboot. It will give you the option to repair/rewrite the Master Boot Record.

---

### Post by Hman242 on 2010-04-18
I can see multiples. I see:

Linux, Ubuntu
Linux, Ubuntu
Memtest
Windows 7
Vista Loader

or something like that. I did uninstall Ubuntu, but only before taking it back to Best Buy. This problem appeared before I uninstalled it.

---

### Post by ed-koala on 2010-04-18
I know this works in 9.10, but I'm not sure what would happen with Ubuntu 10.04 ...

If you currently have a working Windows 7 installation, and space for Ubuntu, just install Ubuntu (9.10).  On my system this resulted in only being able to boot into Ubuntu (temporarily).

You need to edit a file called /etc/default/grub after to put a Win 7  line in ... 9.10 wouldn't automatically pick it up.  You can make Grub always visible there too.

---

### Post by Serpher on 2010-04-18
My main PC running Ubuntu (This laptop isn't due to the WLAN card) is down so if anybody has a Windows 7 entry in GRUB2 could they post it?

@OP: You need to add the line to the file /boot/grub/grub.conf (or .cfg, I forget).

---

### Post by ed-koala on 2010-04-18
*@OP: You need to add the line to the file /boot/grub/grub.conf (or .cfg, I forget).*

NO!  grub.cfg is not meant to be edited.  The file you edit is in /etc/grub/grub.d.  Once done you run update-grub from the terminal and it updats grub.cfg.

Here is a copy of my /etc/grub/grub.d file called 11_Windows:

```
#! /bin/sh -e
echo “Adding Windows” >&2
cat << EOF
menuentry “Windows_7&#8243; {
set root=(hd0,1)
chainloader +1
}
EOF
```

You can make that filename XX_Windows where XX is any number. Depending on how low the number is will determine where in the boot list it shows up.

set root=(hd0,1) may need changed if your partition you boot from isn't the first one.

---

### Post by oldfred on 2010-04-18
Grub2 is very good at finding working windows. Usually there is a windows problem that prevents it from finding it. Since the UUID and parition very depending on your install you just cannot copy another windows entry without changing those parameters.

You edit  40_custom and run sudo update-grub. You do not edit grub.cfg in /boot/grub.

---

