---
title: "WINDOWS 7 is better than Ubuntu 11.04 !  :D"
date: 2011-05-12
forum: General Help
---

### Post by g35celicaz on 2011-05-12
soo i guess windows is better than ubuntu because you dont have to deal with having to fix the 'GRUB' startup menu -_-

LAST week i posted a forum on how to fix my GRUB and NOBODY has a real solution to my problem yet.. so i guess im gonna have to install Windows and wipe out ubuntu! 

if you CAN help, here is the forum i posted last week: 

[http://ubuntuforums.org/showthread.php?t=1752117](http://ubuntuforums.org/showthread.php?t=1752117)

oh yea, and you guys do know that im just joking about windows being better than ubuntu (i like ubuntu more than windows for several resons :D). i just had to attract some users to help me solve this problem!... Although i am considering reinstalling windows 7 again and wiping out ubuntu 11.04 :(

PLEASE HELP!!!!!!!!

---

### Post by Thewhistlingwind on 2011-05-12
Try holding shift at startup. I normally don't get a grub menu unless I do.

Also, threatening to go back to windows is childish and immature, but it did get me here.

---

### Post by Thewhistlingwind on 2011-05-12
In fact, hold it until you actually get a boot menu, stopping before then will cause bootup to resume as normal.

---

### Post by Blasphemist on 2011-05-12
The request for you to press shift immediately after the bios message may work. If not, I think your system is having a problem due to the change to kernel mode settings in natty. You may get a message that grub can't be displayed because of this but it isn't that clear of a message, it doesn't say that.

Since you can get into natty, please do this.
> _How to permanently set kernel boot options on an installed OS (not wubi)_

To permanently change the default kernel boot options, press ALT+F2 or open a terminal from system > accessories > terminal. Type in the following command:
```
gksudo gedit /etc/default/grub
```
a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]nomodeset[/COLOR]"
GRUB_CMDLINE_LINUX=""
```
Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""
```
Now in the terminal, run the following command to update your grub configuration with the new default settings:
```
sudo update-grub
```
I think the nomodeset change shown above in red will work for you. Here is it's description.
[QUOTE]nomodeset
The newest kernels have moved the video mode setting into the kernel. So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a black screen. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded.
Should that not work for some reason, you'll notice when editing the grub file that you can uncomment the following line to set a resolution.
```
GRUB_GFXMODE=640x480
```
I believe the grub menu is trying to come up at the same resolution you are using for your monitor in natty. It may be giving you a message that it can't display grub at that resolution but I bet it can at 640x480.
Do be sure to remember the update of grub
```
sudo update-grub
```[/QUOTE]
For more description on kernel mode settings, see this post that was the source of most of this.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sparkler on 2011-05-12
heh beat me too it

---

### Post by g35celicaz on 2011-05-12
i tried that shift method but it only said 'grub loading' and then "..." and nothing ever loaded! :(

---

### Post by sparkler on 2011-05-12
do what Blasphemist posted

---

### Post by YesWeCan on 2011-05-12
I replied in your original thread.

---

### Post by g35celicaz on 2011-05-12
ok so i turned to the terminal method and i got this as the result:

techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo update-grub
[sudo] password for techgeek: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo update-grub

i will let you know what the results are in a few bits after i restart.. hopefully it goes well :D

---

### Post by drnick79 on 2011-05-12
Posts get buried so quickly on this forum-makes me wonder if the "General Help" could be subdivided so new posts wouldn't sink deep into the heap so quickly. I guess it wouldn't be general help then...
 
It appears that many a post goes unanswered here, but I just assume it's often because they end up on page 15 after a few hours. Perhaps you've got the right idea by resorting to blasphemy in your post title.

---

### Post by wojox on 2011-05-12
Download the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") run it from a live cd and post the results.

---

### Post by g35celicaz on 2011-05-12
i did what Blasphemist said but i still dont get the GRUB! im thinking i might have played around too much with the partitions that i might have deleted the wrong one...

could it be possible that by removing a partition i could have not more GRUB?

---

### Post by Thewhistlingwind on 2011-05-12
> **g35celicaz said:**
> i tried that shift method but it only said 'grub loading' and then "..." and nothing ever loaded! :(

Don't stop holding until you get the menu, I already told you.

---

### Post by g35celicaz on 2011-05-12
i did hold it -_______________________- 

AND like i SAID i got: 'Grub loading...'

---

### Post by Thewhistlingwind on 2011-05-13
> **g35celicaz said:**
> i did hold it -_______________________- 

AND like i SAID i got: 'Grub loading...'

Thats the best I can give you, however, I remember there being initialisation and config files that would help us greatly.

---

### Post by Blasphemist on 2011-05-13
Well, ain't that a kink in the a__. Please do as Wojox asked and post the results of the boot info script.

And did you try both of my recommendations?

---

### Post by g35celicaz on 2011-05-13
will do Blasphemist ;) 

thanks for all of your guys help! i will get started on the Boot Info Script ASAP! (& i will post up the results) :D

---

### Post by g35celicaz on 2011-05-13
actually no i havent Blasphemist, but i will try the second option later on tonight once i finish my homework lol.

---

### Post by g35celicaz on 2011-05-13
i now have access to WINDOWS 7!!!!!

the following commands solved my problem thanks to 'YesWeCan'! :D

sudo lilo -M /dev/sda mbr

sudo reboot

simple as that! :)

---

