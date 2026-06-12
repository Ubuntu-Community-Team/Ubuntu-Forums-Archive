---
title: "GRUB 99 problems"
date: 2011-03-25
forum: General Help
---

### Post by JungleFish on 2011-03-25
I know there are other threads, and I did look through them but did not find anything that works.

3 things. First of all boot order. I dual boot windows and ubuntu. I am happy that ubuntu is first however, how the **** do I change the order of the rest of the partitions. For example ubuntu first, windows second, then all the memory testing and safe-mode stuff. Maybe editing the grub.cfg? But then again doesn't that fine get generated on the go anyway?

Second the time before it auto boots something. I don't want a timer. If I set it to 0 will it just sit there or count from 0.

And lastly how do I get custom background for grub. Or for starters a pre build image of somesort.
This is my edited line from 05_debian_theme file.
```
for i in {/boot/grub,/usr/share/images/grub/}Windbuchencom.{png,tga} ; do
```And when I go update-grub it says Found linux image: /boot/vmlinuz-2.6.35-28-generic
But when I boot there are NO changes. Why why why  :cry:

Thanks in advance!

---

### Post by oldfred on 2011-03-25
If you want to eliminate some parts:

From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

after all changes"
sudo update-grub

---

### Post by drs305 on 2011-03-25
For changing the order of the entries, you can try the GUI app Grub Customizer. Click on the "Customizer" link in my signature line. You can also set the timer with it, as well as the background.

If you want to manually change the files:
Which version of Grub2 are you using? 
It could be 1.99, which has made some changes to the way Grub selects the background image. For that matter, even versions of 1.98 changed the way the wallpaper is set. I think, without looking it up, the "for i..." was from 1.97

You can find the Grub version with "grub-install -v".

For recent versions of G2, all that is necessary to set the background is to add this line to /etc/default/grub:
```
GRUB_BACKGROUND="/path/filename"
```

Don't forget to update grub (sudo update-grub) if you edit the files yourself.

---

### Post by JungleFish on 2011-03-26
Thanks everybody, I'll try when I get back from lab

---

