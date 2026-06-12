---
title: "coop with other unix-systems??"
date: 2006-02-12
forum: General Help
---

### Post by riwa on 2006-02-12
I want to have another unix system to coop with ubuntu. I tried it once with netBSD but couldn't bott ubuntu after that. Had to reinstall ubuntu and remove BSD. I'm wondering how i can if i can do this...

/RIchard

---

### Post by dcstar on 2006-02-12
[QUOTE=riwa]I want to have another unix system to coop with ubuntu. I tried it once with netBSD but couldn't bott ubuntu after that. Had to reinstall ubuntu and remove BSD. I'm wondering how i can if i can do this...

/RIchard[/QUOTE]
If you mean a dual-boot system, then you must have separate disk partitions set aside for each O/S you want to install, then you need to either have a boot manager that respects all the pre-installed systems, or re-install Ubuntu's GRUB after all the other install have been completed.

Do a forum search for "dual boot" and "restore grub".

---

### Post by hw-tph on 2006-02-12
I have a dual boot machine that runs Ubuntu and OpenBSD. I installed OpenBSD after Ubuntu, but the latter was rude enough to overwrite my mbr. Solution: Boot Ubuntu LiveCD and chroot to the existing Ubuntu installation and rerun grub-install from there (**grub-install /dev/hda** in my case) to restore the Grub bootloader. Then, for OpenBSD, I set up a simple chainload section in /boot/grub/menu.lst like you will find in tons of posts regarding Linux/Windows dual boot setups.


Håkan

---

### Post by riwa on 2006-02-15
Ok. Didn't really get all that but I look around some more... Respekt Sweden!

---

### Post by riwa on 2006-02-21
Ok. Ive been considering the thing about: ```
grub-install /dev/hda
```
Anyways I´ll try installing BSD a nd   then launch the liveCD and reinstall the grub loader from there...

Wouldn´t it be possible to start an expert installation and do it  from there? Becasue i don´t really know where to install grub..

A step by step explanation would be greatly appreciated.. Can´t afford to loose all my data again...

/Richard

---

### Post by alan.mckinnon on 2006-02-22
[QUOTE=riwa]Ok. Ive been considering the thing about: ```
grub-install /dev/hda
```
Anyways I´ll try installing BSD a nd   then launch the liveCD and reinstall the grub loader from there...

Wouldn´t it be possible to start an expert installation and do it  from there? Becasue i don´t really know where to install grub..

A step by step explanation would be greatly appreciated.. Can´t afford to loose all my data again...

/Richard[/QUOTE]

It's not hard, you just gotta know a thing or 10 about disks and partitions. These are generic grub instructions - Ubuntu is my secondary distro and is booted from a grub from another distro. I may miss some Ubuntu tweaks but the gist of it is the same.

If you are not 100% comfortable with it all, it's always best to with the first operating system to install the boot loader to the MBR of the first disk. Instruct all subsequent operating systems to install their boot loader to the boot sector of the disk that OS is using. Then edit the config file of the original boot loader and chainload the second OS. Confused yet? Example:

Install Ubuntu onto a clean disk. Grub will go into the MBR of the first disk - /dev/hda, it's support files will be found at /boot/grub/ and the config file will be /boot/grub/menu.lst or /boot/grub/grub.conf

Now install ?BSD, let's say you put it on /dev/hda5. Hopefully the BSD will ask you where to put the boot loader - tell it to put it in the boot sector of /dev/hda5. Note that this isn't the disk MBR it's going in, so the grub that Ubuntu put there will still work.

Once the BSD is installed, you need to tell Ubuntu's grub about the BSD (otherwise it won't boot). As root, edit grub.conf and add a new stanza that looks like this:

title   BSD
root   (hd0,4)
chainload +1

The file is well commented so you shouldn't go wrong. IIRC there's also instructions in there that tell you how to translate Linux's /dev/hda5 to grub's (hd0,4) notation.

Save and reboot. Ubuntu's grub will appear with an extra entry for BSD.

About grub-install: this command can cause serious grief and much head scratching. On a functioning system, you do this:

sudo grub-install /dev/hda

And it mostly works out fine. It usually works just fine on a LiveCD too. If ?BSD overwrites your MBR you'll have to add some more options to the command to get it to work. The reason why and how to do it are not trivial, so if you need this, post back to this list with a full description of what OS's and directories are on which disk partitions and we'll see you right.

Last tip: Back up your partition table, or even make a pen and paper copy of the output of 'fdisk -l'. If you make a mistake with partitions and delete the wrong one, you can recover everything as long as you don't do the next step of formatting the partition and writing to it

---

### Post by riwa on 2006-02-24
*Sob sob* 

I was brave and tryed it out again... Couldn´t find the grub thing.. Now that you mention it i remember doing the s ame thing  with windows..T Too bad i didn´t remember it ;/. Well well, reformatting the whole system and will this time try installing BSD first... 

Let´s see if its any progress...

Thanks for the help anyway... Ill keep this copy close if it doesn´t work...

---

### Post by riwa on 2006-02-25
Well it got messed up again... I tried to re-install a server-ubuntu on a separate partition to recover my files but got this: failure on loading initrd.. or  something.

I used to get that by last time i installed but just kept trying until it worked... No luck this time though...

I couldn't find the grub.config file anywhere on the system and for some reason i couldn't access the other ubuntu partition (i hate to say that the whole system is on a single partition ;/) even if i opened a shell from the install disk. 

Running Windows XP now... Would love a step-by step instruktion to recover my files and keep my three O/S. (Cant use wireless on linux for some reason)..

It's Windows XP, Ubuntu, netBSD installed in that order...

By the way the grub-install /dev/hda or whatever it was didn't work.. Some list weren't found but could be created with root access and update-grub. No success here neather though...

Thanks for the  help so far...

/Richard

---

### Post by riwa on 2006-03-02
Ok. now i got the three systems installed.. only to of them are working though... Trying out most of the things in your helpful little guide I began to realise where the problem is... (i think)

Considering the bootloader and what it is i first thought that it was just a program to launch the OS (bear with me). However considering the  effect of chainloading and what it can do i believe that the bootloader is essential to every OS and it cannot start without it... If its true im screwed.. I didnt install any boot loader for netBSD. It only asked me about MBR and i said no.

I believe chainloading means loading another bootloader am i correct?

So now what???

---

