---
title: "GRUB2 not loading new Operating System (PClinuxOS)"
date: 2010-08-06
forum: General Help
---

### Post by joehoward on 2010-08-06
Hello
I've been using Ubuntu 9.10 for a while now, and i've started to look at other distros of linux. I found PClinuxOS which seemed decent and decided to install it alongside my Ubuntu 9.10 and Windows Vista. The bootloader that came with PClinuxOS recognised my Vista OS, but not my Ubuntu.
long story short, i recovered Ubuntu's GRUB becasue i had already edited it to my liking. GRUB found the PClinuxOS partition and added it to the menu. Vista and Ubuntu start fine, but when i try to select the PClinuxOS option, i get this message-type-thing:
 
[linux-bzImage, setup=0x3a00, size=0x1f9110]
vga=788 is deprecated. useset gfxpayload=800x600x16, 800x600 before linux command instead
error: no such partition
 
I don't really know, but it almost sounds like GRUB is trying to find the linux kernel, but it cannot connect to the partition for some reason.
 
I have been extremely pleased with Ubuntu, so I really don't *need* another distro, but I'd like to know how to fix this.
 
thanks!

---

### Post by Rubi1200 on 2010-08-06
I can't give you an exact answer, other than to say that I once had a similar problem trying to boot with PCLOS and Ubuntu.
 
I never sorted it out and ended up getting rid of PCLOS.
 
You might want to consider asking on their forums.

---

### Post by corrytonapple on 2010-08-06
You could uninstall it and then try reburning it on a quality CD. The CD could be bad.

---

### Post by uncleV on 2010-08-07
> **joehoward said:**
> Hello
I don't really know, but it almost sounds like GRUB is trying to find the linux kernel, but it cannot connect to the partition for some reason.
 thanks!
GRUB[COLOR=Red]2[/COLOR] is trying... But can't find it... :cry:

Look at (hdx,y) in your */boot/grub/grub.cfg*

GRUB counts partitions starting from (hdx,0) and GRUB2 starts from (hdx,[COLOR=Red]1[/COLOR]).
GRUB2 broke the count convention and does silly things trying to boot other distros.
Find the PCLinusOS sections and look at mismatch addresing. Here is an example of my *grub.cfg*:

-------------------------
     [FONT=DejaVu Sans]menuentry "linux-nonfb (on /dev/sda[COLOR=Black]2[/COLOR])" {[/FONT]
 [FONT=DejaVu Sans]    insmod ext2[/FONT]
 [FONT=DejaVu Sans]    set root='(hd0,[COLOR=Blue]2[/COLOR])'[/FONT]
 [FONT=DejaVu Sans]    search --no-floppy --fs-uuid --set f546398b-c833-45a5-9be8-83b8c4949b05[/FONT]
 [FONT=DejaVu Sans]    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=f546398b-c833-45a5-9be8-83b8c4949b05[/FONT]
 [FONT=DejaVu Sans]    initrd (hd0,[COLOR=Red]1[/COLOR])/boot/initrd.img[/FONT]
[FONT=DejaVu Sans]-------------------

[/FONT]Of course *it* can't boot PCLOS this way.
You have to change GRUB's addressing (hd0,1) to GRUB2's (hd0,2) in order Ubuntu's loader to find a kernel of a distro that's using GRUB.
But I didn't bother fixing it, simply replaced by the loader of PCLOS. If you fix *grub.cfg* the next time Ubuntu updates your kernel the error will be back!

Otherwise boot PCLOS LiveCD and try "Redo MBR" or "Remaster MBR"... oh, you better visit pclinuxos forum, there are many similar solved threads in "Hard drive installation". It is now down for hackers attacks but soon will be up.

Or get rid of a beautiful distro because of the one that's making the silly fault, as you were wisely advised here ;)

Good luck!

---

### Post by joehoward on 2010-08-08
Hi
I wanted to thank everyone up front for your quick responces. I was not expecting somehing the day after:o!
 
i did what uncleV said and changed the number...now it works perfectly!:D
i didn't use PClinuxOS's bootloader becasue it does not recognise my ubuntu OS. 
 
so now just two more questions:
 
1. will i have to change this file EVERY time update-grub runs? if so, is there some sort of script i could write to automatically fix this problem? I'm somewhat new to linux and stuff, but i have written DOS and C# code before for Windows.
 
2. where did you figure this out uncleV? i searched the web for hours and when nothing came up, i finally posted here. I am amazed that you could figure that out
 
again, thank you all so much. yet another thing great about linux: great help. almost every question i've had has been answered.

---

### Post by oldfred on 2010-08-08
Copy the  entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

Then if you do not want duplicate entries turn off osprober. You can turn it on if you add another system but you do not need it on every update.

I added this :
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

grub2 info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

### Post by uncleV on 2010-08-25
> **joehoward said:**
> Hi
where did you figure this out uncleV? i searched the web for hours and when nothing came up, i finally posted here.

I figured it for myself :)
It's not so hard looking in *grub.cfg* to realise that there is an address mismatch in the not booting sections.

Actually I was comparing the PCLOS's *menu.lst* and Ubuntu's *grub.cfg* when couldn't boot to PCLOS.
A saw there GRUB2 simply copied the boot address from Grub's *menu.lst* and put it to *grub.cfg*. Hence the mismatch.

I'm glad you are OK now :)

---

### Post by joehoward on 2010-08-27
Cool.  Thank you everyone again.
One of the coolest things i've found with linux is how many people are willing to help when there are problems.  i look foward to learning more and convincing my friends that linux is more than a legitimate OS.

---

