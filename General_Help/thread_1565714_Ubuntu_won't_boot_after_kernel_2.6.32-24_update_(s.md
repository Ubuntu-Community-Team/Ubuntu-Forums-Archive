---
title: "Ubuntu won't boot after kernel 2.6.32-24 update (sticks on boot initramfs)"
date: 2010-09-01
forum: General Help
---

### Post by StewartM on 2010-09-01
Hello all,

This morning, I booted into my administrator account and checked for updates. There were a number (bogofilter, for one) but also a update to the 2.6.32-24 kernel. I installed the updates and rebooted the system.

When I rebooted, the thought occurred to me (from reading another thread) that one of the reasons my Zareason desktop boots slower than my laptop (55 seconds vs 35) was that I have an external floppy drive attached, and perhaps the delay was a difference in my system checking for a bootable floppy. So I went into the BIOS when it was booting to check to see if the floppy was enabled (it wasn't). Then I selected "Exit without saving" and resumed booting.

What happened next was instead of seeing the Ubuntu icon and the six dots, I see "Ubuntu 10.04" and four dots. Then I get on the black screen these errors (sorry for any mistyping, I wrote them down on a sheet of paper as I had no other computer available to troubleshoot):

***************************************************************

udevadm trigger is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured

ALERT! /dev/disk/by-uiid/939af864-c1a8-41d7-9b24-91d25685b6 does not exist. Dropping to shell

Busybox v1.13.3 (Ubuntu 1:1.13:3-1ubuntu11 built-in shell (ash).

Enter 'help' for built-in commands

initramfs

*************************************************************

Googling around once I got into work and had computer access, it seems that the problem is GRUB has lost track of what partition I should boot from? Here is a thread which might be relevant:

[http://ubuntuforums.org/showthread.php?t=1561735](http://ubuntuforums.org/showthread.php?t=1561735)

Before I left for work, I went into the BIOS again and looked at the CMOS settings--everything looked normal. I once again exited without saving anything. I was going to try selecting an earlier kernel from the GRUB menu on boot, but couldn't remember the key to press (I found out later today, to enter GRUB 2 it's been changed to the shift key, and not the F2 key like it used to be). One poster on the aforementioned thread said his system would boot ok to the earlier kernel. 

Anyway, any advice? The thread above has as its solution to either try to tell GRUB where your boot partition is and/or re-installing GRUB. 

I have /home on a separate partition, so if I need to do a re-install I can do so without it being a major pain. Sda1 is the partition which has the OS.

[IMG]http://i211.photobucket.com/albums/bb262/netnguy01/Linux%20Support/Screenshot.png[/IMG]

StewartM

---

### Post by conor.starrs on 2010-09-01
Hi Stewart,

I've been having the exact same problem....can't boot past initramfs (after 'udevadm trigger is not permitted while udev is unconfigured').

I pressed ESC to enter grub and selected a previous version 2.6.32-24-generic which boots up fine.

Any suggestions on how to remedy would be great?

Thanks in advance folks!

PS, love this forum....very little I have left unsolved thanks to it.

:P

:popcorn:

---

### Post by StewartM on 2010-09-01
> **conor.starrs said:**
> Hi Stewart,

I've been having the exact same problem....can't boot past initramfs (after 'udevadm trigger is not permitted while udev is unconfigured').

I pressed ESC to enter grub and selected a previous version 2.6.32-24-generic which boots up fine.

Any suggestions on how to remedy would be great?

Thanks in advance folks!

PS, love this forum....very little I have left unsolved thanks to it.

:P

:popcorn:

Here is something I am being told by some friends. Not had been home yet to try it out (but you can try to do so).

"If the “apt-get upgrade” does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs –u  -k command. Then run sudo dpkg –reconfigure. That should clear the upgrade flags and fix any broken packages."

If it does work, please post it.

StewartM

---

### Post by dgermann on 2010-09-01
StewartM--

That solved it for me too.

This is an old bug, raising its head again, apparently, with much the same solution: [https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654]("https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654")

Thanks!

---

### Post by lordzeus on 2010-09-01
hi!
i've tried out the same procedure...but a keep getting the same message...grub doesnt rise up so i can select the kernel...i'm pressing Shift, Esc ...all possible keys...
i get the problem message even afert shows "Grub Starting..." "Grub loading."

how do i fix this problem?

---

### Post by Tabo58 on 2010-09-01
This morning I got system updates, I allowed all packets to be updated. I have run Ubuntu 10.04 for about a month and a new linux end user. Once I rebooted after the updates I was unable to boot the system up. 

I should add that this is single OS system Ubuntu 10.04 only no duel booting and no partitions at this time.. I am very new to the command line and honestly at a complete loss at this point how to get this system back up and running without wiping and reinstalling..  with a bit of your help I'm hoping to get one of those LEARNED lessons on getting past this without having to do a junior ranger fresh install..  thx 

 info on the screen reads as such:   

udevadm trigger is not permitted while udev is unconfigured.
gave up waiting for root device. Common problems:
- Boot args ( cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
- Check root= did the system wait for the right devices?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4f517d2e-22c0-421a-86e9-97be9523720e does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
enter 'help' for a list of built-in commands

(initramfs)

this system also has a floppy drive and it's light stays on, but I don't hear it trying to access (possible useless info)

I burn another iso of 10.04 and I was able to boot into the LiveCD, hopefully I can get this system back up and running properly before I give yet another Ubuntu 10.04 disk away.  Would it be advisable/possible to attempt to partition this one drive un-partitioned system using the LiveCD ?

---

### Post by roy.nico on 2010-09-02
Hej everybody, 

i had exactly the same problem after an update this morning. I followed 

> **StewartM said:**
> You should be able to boot using the old kernel and then run the sudo update-initramfs –u  -k 2.6.32-24-generic.
StewartM

and this fixed the problem for me.
Thanks !
nicolas

---

### Post by mar00n on 2010-09-02
Hi, I had the same problem too and this fixed it :

> You should be able to boot using the old kernel and then run the sudo update-initramfs –u  -k 2.6.32-24-generic.
StewartM

;)

---

### Post by StewartM on 2010-09-02
I just want to say that holding the "Shift" key down, entering Grub 2, and booting to a previous kernel (in my case, 2.6.32-22) allowed me into my system. Then I typed:

sudo update-intramfs -u -k 

I got an error with the -k switch--I found out that this refers to the specific kernel, though "all" was an option. So I was brave an chose "all" and it updated it for all the kernels.

After that, I did:

sudo dpkg -reconfigure

And then got an error that I didn't have proper switches. Banking that nothing in my system was broken (or that I couldn't at least fix it later with Synaptic) I then rebooted.

That fixed the problem. So it works for me too.

StewartM

---

### Post by StewartM on 2010-09-02
Tabo58:

> info on the screen reads as such:

udevadm trigger is not permitted while udev is unconfigured.
gave up waiting for root device. Common problems:
- Boot args ( cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
- Check root= did the system wait for the right devices?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4f517d2e-22c0-421a-86e9-97be9523720e does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
enter 'help' for a list of built-in commands

(initramfs)

this system also has a floppy drive and it's light stays on, but I don't hear it trying to access (possible useless info)

I burn another iso of 10.04 and I was able to boot into the LiveCD, hopefully I can get this system back up and running properly before I give yet another Ubuntu 10.04 disk away. Would it be advisable/possible to attempt to partition this one drive un-partitioned system using the LiveCD ?

1) Boot the computer. Hold down the "shift" key when it's booting.

2) You will enter Grub 2. It should show you the list of kernels on your system. Select the one before 2.6.32-24. (Don't choose a "recovery mode" option.

3) Boot your system--it should boot normally.

4) Run from the terminal:

sudo update-initramfs –u -k 2.6.32-24-generic

(assuming that is the problem kernel for you. You can always check your kernel by typing "uname-r")

5) Reboot

If your problem is the same as everyone else's here, it should be fixed.

IF you have no other kernels on your system, you can also fix it using a Live CD. This is from a friend:

- chroot in your broken system from a liveUSB/CD (cd into /boot)
- sudo update-initramfs -u -k [enter kernel ID here]
- reboot

StewartM

---

### Post by StewartM on 2010-09-02
lordzeus

> hi!
i've tried out the same procedure...but a keep getting the same message...grub doesnt rise up so i can select the kernel...i'm pressing Shift, Esc ...all possible keys...
i get the problem message even afert shows "Grub Starting..." "Grub loading."

I think your problem goes beyond ours. 

Which version of Grub do you have? 1.5 or 2? Is this 32-bit or 64-bit Ubuntu?

You might be able to fix your problem by booting from the live CD. There are several tutorials online on how to fix Grub, but I've never done it before.

StewartM

---

### Post by conor.starrs on 2010-09-02
> **StewartM said:**
> Tabo58:

Run from the terminal:

sudo update-initramfs &#8211;u -k 2.6.32-24-generic

(assuming that is the problem kernel for you. You can always check your kernel by typing "uname-r")

5) Reboot



Works for me except my broken kernal was 2.6.32-24-386. So:

sudo update-initramfs &#8211;u -k 2.6.32-24-386

and Reboot.

Thanks folks, particularly StewartM.

):P

---

### Post by lordzeus on 2010-09-02
Grub 2 it's not entering...
goes to the same message..."udevadm trigger is not permitted while udev is unconfigured..."

what can i do to fix this?

> **StewartM said:**
> Tabo58:

1) Boot the computer. Hold down the "shift" key when it's booting.

2) You will enter Grub 2. It should show you the list of kernels on your system. Select the one before 2.6.32-24. (Don't choose a "recovery mode" option.

3) Boot your system--it should boot normally.

4) Run from the terminal:

sudo update-initramfs –u -k 2.6.32-24-generic

(assuming that is the problem kernel for you. You can always check your kernel by typing "uname-r")

5) Reboot

If your problem is the same as everyone else's here, it should be fixed.

IF you have no other kernels on your system, you can also fix it using a Live CD. This is from a friend:

- chroot in your broken system from a liveUSB/CD (cd into /boot)
- sudo update-initramfs -u -k [enter kernel ID here]
- reboot

StewartM

---

### Post by StewartM on 2010-09-02
> Grub 2 it's not entering...
goes to the same message..."udevadm trigger is not permitted while udev is unconfigured..."

First of all, the simple thing--do you have Grub 1.5, or Grub 2?

Grub 1.5 uses the ESC key, as I recall. Grub 2 uses the shift key (and this morning I found out the first time I tried it you have to ***keep*** the shift key pressed down and hold it, not just press it and release it).

I thought you had a GRUB problem but the fact you get to the udevadm trigger alert seems to indicate that you're booting into grub and that it's not hanging.

StewartM

---

### Post by Tabo58 on 2010-09-02
StewartM

Thank you for the _[COLOR=black]very detailed[/COLOR]_ instructions: at least I can boot into the install, unfortunately I do only have the one kernel (2.6.32-24) I will have to wait for the weekend to try your Live CD fix. I will post my results.

Great forum, excellent members!

> **StewartM said:**
> Tabo58:



1) Boot the computer. Hold down the "shift" key when it's booting.

2) You will enter Grub 2. It should show you the list of kernels on your system. Select the one before 2.6.32-24. (Don't choose a "recovery mode" option.

3) Boot your system--it should boot normally.

4) Run from the terminal:

sudo update-initramfs –u -k 2.6.32-24-generic

(assuming that is the problem kernel for you. You can always check your kernel by typing "uname-r")

5) Reboot

If your problem is the same as everyone else's here, it should be fixed.

IF you have no other kernels on your system, you can also fix it using a Live CD. This is from a friend:

- chroot in your broken system from a liveUSB/CD (cd into /boot)
- sudo update-initramfs -u -k [enter kernel ID here]
- reboot

StewartM

---

### Post by zukrup on 2010-09-03
im facing kinda same problem here. ubuntu doesnt boot after 2.6.32-24 update. i installed ubuntu once with wubi-installer, and running as dual boot with win7. during boot screen i see both 2.6.32-23 and 2.6.32-22 kernels to select.  however none of those kernels seem working. it still stucks during boot. saying same error "drive / is not ready or present" etc. (or sometimes oldkernels pass that screen but right after it gives video card driver error and stuck again.) 
i can manage to reach to terminal with recovery mode, or by hitting M when it throws the error. but that doesnt work neither.
(strange notice for me here. as i said, it stucks with "no drive is present" error but when i jump into bash. i see all my drives, folders, files.. all of them are right there. this is bugging me for real :p pls correct me if i'm wrong cause im total linux noob)

 whatever on terminal when i try update-initframs magic it throws another error stating  "read-only file system. cannot update /boot/ etcetc.." (even if i'm root user)

any suggestions pls. for example may i modify boot commands and disable video drivers,start the system with terminal screen only.
tx in advance
sorry for my engrish

---

### Post by lordzeus on 2010-09-03
It works! There is hope after all...
i hold esc and entered the grub menu...
and then  on the old kernel a i run the command you gave...
after reboot the system started fine...
thabks StewartM!

[]'s

> **StewartM said:**
> First of all, the simple thing--do you have Grub 1.5, or Grub 2?

Grub 1.5 uses the ESC key, as I recall. Grub 2 uses the shift key (and this morning I found out the first time I tried it you have to ***keep*** the shift key pressed down and hold it, not just press it and release it).

I thought you had a GRUB problem but the fact you get to the udevadm trigger alert seems to indicate that you're booting into grub and that it's not hanging.

StewartM

---

### Post by changke on 2010-09-03
Thanks a lot, this saved my ***! :)

I actually have no kernel version smaller than 2.6.24, but I did keep a 2.6.24-generic-pae kernel, luckily it is still bootable.

---

### Post by StewartM on 2010-09-03
Zukrup

> im facing kinda same problem here. ubuntu doesnt boot after 2.6.32-24 update. i installed ubuntu once with wubi-installer, and running as dual boot with win7. during boot screen i see both 2.6.32-23 and 2.6.32-22 kernels to select. however none of those kernels seem working. it still stucks during boot. saying same error "drive / is not ready or present" etc. (or sometimes oldkernels pass that screen but right after it gives video card driver error and stuck again.)
i can manage to reach to terminal with recovery mode, or by hitting M when it throws the error. but that doesnt work neither.
(strange notice for me here. as i said, it stucks with "no drive is present" error but when i jump into bash. i see all my drives, folders, files.. all of them are right there. this is bugging me for real pls correct me if i'm wrong cause im total linux noob)

whatever on terminal when i try update-initframs magic it throws another error stating "read-only file system. cannot update /boot/ etcetc.." (even if i'm root user)

I've never used wubi, so I'm of little help here. 

But googling I found this thread:

[http://ubuntuforums.org/showthread.php?t=1378614](http://ubuntuforums.org/showthread.php?t=1378614)

Don't know if it will help you. 

I am going to mark this thread "SOLVED" as I think yours is a somewhat different issue. I would post it under a new thread with [WUBI] in the title so it will attract people with experience with wubi.

StewartM

---

### Post by zukrup on 2010-09-03
thank you for the link. 'ill try it.  and i may ask it again in another thread  as y suggested if i fail again. 
ty

---

### Post by Tabo58 on 2010-09-04
Tried this:  

 from a Live CD 

cd /boot
- sudo update-initramfs -u -k 2.6.32-24-generic  (enter)

Response is:

update-initramfs is disabled since running on read only media

Not giving up yet,   I did remove grub-pc and installed grub and tried, (hey I'm so new I'm still in shrink-wrap).. and tried both from terminal after booting into grub with shift key same msg, then with Live CD and yet another fail.

back to grub-pc, for me I'm not so sure of the difference between the two.

Not giving in just yet, but further searching for something else to try has me empty handed.

only kernel 2.6.32-24-generic and a single partition drive.

Still having fun, but am hopeful I can move on soon :p

Question: When I do use shift to boot into grub, I do get this msg

Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA (O): Failed to load the NVIDIA kernel module!
(EE) NVIDIA *** Aborting ***
(EE) Screen(s) found. but none have usable configuration.


This is probably a separate issue and if so, low priority. Graphic's still very crisp and clear



I have moved on and tried the suggestions found at

[http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/](http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/)

May help some of you who like me are still struggling with this problem.    After I followed the instructions my error has changed to:

Check rootdelay=
Check root
Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/4f517d2e-22c0-421a-86e9-97be9523720e does not exist. Dropping to shell!

busyBox v1.13.3 ubuntu 1:1.13.3-1ubuntu11

my  GNU GRUB v 1.98-1ubuntu7

Can still boot thru holding shift down and selecting kernel, so no better off,  worse off ?

---

### Post by Francis 24/24 on 2010-09-05
It's very helpful to have a workaround which, more or less easily, works for several persons,but I would prefer the bug to be fixed and the update
to run smoothly.
Is the bug assigned to someone ?
Cheers !

---

### Post by virsto on 2010-09-05
> **StewartM said:**
> Here is something I am being told by some friends. Not had been home yet to try it out (but you can try to do so).

"If the “apt-get upgrade” does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs –u  -k command. Then run sudo dpkg –reconfigure. That should clear the upgrade flags and fix any broken packages."

If it does work, please post it.

StewartM

I believe that I am having the same problem with 32-24. Could you please be a little more specific on the commands I need to execute to recover from this mess.

---

### Post by virsto on 2010-09-05
> **virsto said:**
> I believe that I am having the same problem with 32-24. Could you please be a little more specific on the commands I need to execute to recover from this mess.


This is what happens on my system.

```
sudo dpkg -reconfigure
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by necrosymbiont on 2010-09-07
> **StewartM said:**
> 
1) Boot the computer. Hold down the "shift" key when it's booting.

2) You will enter Grub 2. It should show you the list of kernels on your system. Select the one before 2.6.32-24. (Don't choose a "recovery mode" option.

3) Boot your system--it should boot normally.

4) Run from the terminal:

sudo update-initramfs –u -k 2.6.32-24-generic

(assuming that is the problem kernel for you. You can always check your kernel by typing "uname-r")

5) Reboot


This did not work for me until I used the suggestion from this thread:

[http://ubuntuforums.org/showthread.php?t=1427204](http://ubuntuforums.org/showthread.php?t=1427204)

Namely,


[LIST=1]
[*]Use the shift key when booting to obtain the grub menu and choose a bootable kernel, as previously described.
[*]Run ```
dpkg --get-selections | grep linux-image
``` to get a list of packages to choose from for the next step.
[*]Run ```
sudo apt-get install --reinstall [choice of packages]
``` Just reinstall the problematic ones, and in particular I suspect it would be a bad idea to reinstall the safe one you are currently booted into.
[*]Run ```
sudo update-grub
```
[*]Reboot
[/LIST]

Note that after reinstalling the linux-image packages, apt-get appears to run update-initramfs automatically. Therefore, these steps could be seen as subsuming StewartM's fix.

---

### Post by Francis 24/24 on 2010-09-08
For those who have not yet installed the last updates, or went back to this
state, as I did, here is how to save time and efforts :

- install updates with Update Manager as usual

- DO NOT accept to reboot right now 

- as root :

# cd /boot
# sudo update-initramfs -u -k 2.6.32-24-386
# sudo update-initramfs -u -k 2.6.32-24-generic

- reboot

Worked fine for me.

Cheers !

---

### Post by StewartM on 2010-09-08
> **Tabo58 said:**
> Tried this:  

 from a Live CD 

cd /boot
- sudo update-initramfs -u -k 2.6.32-24-generic  (enter)

Response is:

update-initramfs is disabled since running on read only media



Sorry, I did not flesh that out (it was from an email from a friend). Here may be a better description of what you need to do (Sorry, I've not tried it, been consumed by work of late):

[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)

> Let's say your system just melted down after an upgrade, or your new kernel won't boot. You can't fix the problem with apt-get, because you can't even get to a command line; the kernel just spews out errors and hangs on bootup. Thankfully, with a live cd, you can repair your system and get it up and running. You have 2 options for the live cd: Knoppix or the Ubuntu live cd. Since Knoppix generally has better hardware detection, this will be used as an example.
First, download the iso from [http://www.knoppix.org/](http://www.knoppix.org/) and burn it to a disk.
Get your BIOS set up to boot from the cd, pop in the Knoppix disk, and boot.
Your hard drive should show up on the KDE desktop as hda1 or sdb2 or something, depending on your system.
Click on it to mount it, then right-click, actions -> change to read-write mode. It'll pop open a dialog; click yes.
Now, open a root terminal, found in the Knoppix menu (the one next to the K on the panel).
Enter: chroot /mnt/hda1 or whatever the icon for your harddrive says on the desktop.
You can now use all the commands on the hard drive, including apt-get.
If you ever get this error: /dev/null: Permission denied, do this: rm /dev/null and it should go away.
Now, use apt-get to upgrade your kernel (apt-get install linux-386) (or whatever processor you're using), udev (apt-get install udev), or anything else that's messing up your system.
Reboot, and enjoy your newly rescued system!


If your problem is that you can't write to your HD with the LiveCD, this seems to be a way of fixing that.

StewartM

---

### Post by StewartM on 2010-09-08
> **necrosymbiont said:**
> This did not work for me until I used the suggestion from this thread:

[http://ubuntuforums.org/showthread.php?t=1427204](http://ubuntuforums.org/showthread.php?t=1427204)

Namely,


[LIST=1]
[*]Use the shift key when booting to obtain the grub menu and choose a bootable kernel, as previously described.
[*]Run ```
dpkg --get-selections | grep linux-image
``` to get a list of packages to choose from for the next step.
[*]Run ```
sudo apt-get install --reinstall [choice of packages]
``` Just reinstall the problematic ones, and in particular I suspect it would be a bad idea to reinstall the safe one you are currently booted into.
[*]Run ```
sudo update-grub
```
[*]Reboot
[/LIST]

Note that after reinstalling the linux-image packages, apt-get appears to run update-initramfs automatically. Therefore, these steps could be seen as subsuming StewartM's fix.

Thank you! I posted some shorthand versions in my original post, this fleshes them out.

StewatM

---

### Post by StewartM on 2010-09-08
> **Francis 24/24 said:**
> It's very helpful to have a workaround which, more or less easily, works for several persons,but I would prefer the bug to be fixed and the update
to run smoothly.
Is the bug assigned to someone ?
Cheers !

Anyone can submit it via Launchpad. Obviously, not everyone who runs this kernel update is hitting this problem, so there may be a hardware or software commonality among us all.

StewartM

---

### Post by bcbc on 2010-09-08
Here's a bug for it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/628084](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/628084)

---

### Post by AndresM on 2010-09-11
> **StewartM said:**
> Tabo58:



1) Boot the computer. Hold down the "shift" key when it's booting.

2) You will enter Grub 2. It should show you the list of kernels on your system. Select the one before 2.6.32-24. (Don't choose a "recovery mode" option.

3) Boot your system--it should boot normally.

4) Run from the terminal:

sudo update-initramfs &#8211;u -k 2.6.32-24-generic

(assuming that is the problem kernel for you. You can always check your kernel by typing "uname-r")

5) Reboot

If your problem is the same as everyone else's here, it should be fixed.

IF you have no other kernels on your system, you can also fix it using a Live CD. This is from a friend:

- chroot in your broken system from a liveUSB/CD (cd into /boot)
- sudo update-initramfs -u -k [enter kernel ID here]
- reboot

StewartM

Thanks for the shift trick to get in GRUB, I'm able to choose a different version. the sudo update-(...) seems to do something but when I reboot it still hangs the same way.


EDIT:did the sudo update comand but with PAE at the end... it was the one on the top of the grub list. The next one is recovery mode and then generic. So using the instrucions above:
Shift to get the grub
I loaded the  2.6.32-24. generic (there are two above this one: PAE and recovery)
ran the  sudo update-initramfs &#8211;u -k 2.6.32-24-generic-PAE (or similar)
rebooted
Ubuntu netbook remix loaded but battery died, will need to wait until tomorrow. But, does this mean it is running by default the recovery mode?

---

