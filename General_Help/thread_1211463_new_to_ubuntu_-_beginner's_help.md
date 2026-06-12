---
title: "new to ubuntu - beginner's help"
date: 2009-07-12
forum: General Help
---

### Post by skryzak on 2009-07-12
hey, this is my first time in the forums! i ordered an hp pavilion dv6z (coming on july 25th) but was going to wipe off vista and instead put on ubuntu. (YEAH!) i was just wondering what suggestions you guys have for essential programs i need. anything for doing schoolwork, possibly playing a couple of pc games, just everyday things.   

hopefully if i have more specific questions in the next few weeks, i can get them answered here!  ):P   thanks!

---

### Post by sablefoxx on 2009-07-12
Ubuntu comes pre-installed with just about everything you'll need to begin with, word processor, web browser, etc.  I may recommend the Ubuntu restricted extras, Amarok, VLC, and XBMC.

---

### Post by skryzak on 2009-07-12
thanks! i'm definitely getting amarok, i can't deal with itunes anymore. i liked songbird, but it was buggy with recognizing my ipod.

---

### Post by whole.grains on 2009-07-12
You may want to consider dual booting if you think your school might require you to do some Windows based task for class. Or at least try and get your money back for Windows.

---

### Post by raymondh on 2009-07-12
+1 ... I would dual-boot until at least I was comfortable in/with Ubuntu.

I would also try the livecD first and see how my system reacts with the distro.  It (the liveCd) is a good indicator of things to come.

Some references should you decide to dual-boot:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)  (check the release notes)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Have fun.

---

### Post by skryzak on 2009-07-12
thanks! i have a seasoned ubuntu user who's helping me set up, i can ask him to dual boot at least for the first few weeks.

---

### Post by TeamJ on 2009-07-12
wine
vlc
compiz fusion

---

### Post by windy81 on 2009-07-12
dual boot onto an external hard drive, thats what i did. 
then if you decide you don't like it, just re format. 

if you need to set up the grub to start windows and had a problem this thread i made might help you a bit. not that im plugging here. Just friendly advice.

[http://ubuntuforums.org/showthread.php?t=1209834](http://ubuntuforums.org/showthread.php?t=1209834)

---

### Post by gamerchick02 on 2009-07-12
Like sablefoxx said, Ubuntu comes with many programs you need to start out.

I'd recommend getting: 

Xchat (if you do IRC chat; very helpful group of people in the rooms) 
Banshee (for music organization) 
Tasque (for task list management)
Gwibber (for microblogging; use the PPA set up by the Gwibber team) 
Dropbox or UbuntuOne (to backup your files)

and

Picasa (to organize your photos)

That's what I use.  Some are PPAs and some are in the repos.

Good luck with your Ubuntu adventure!

Amy

---

### Post by skryzak on 2009-07-15
Great! I needed a program to back up my data. Now I want my laptop to come ASAP!!  ;)

---

### Post by t4thfavor on 2009-07-15
Mostly use tar and rsync to backup stuff, if your looking for a gui prog, I don't know of any off hand.

Also on the dual boot, I see that as just a crutch, but I have more than one machine so I have one Ubuntu, and one windows/ubuntu. I only use the Ubuntu only one, and since I can't just reboot it it gives me incentive to find an Ubuntu solution for my problem instead of just going to Windows and doing a task.

Over the last 3 months, I have used Windows exactly 3 times, when I go to my office and use my workstation which has Vista on it.

It also helps me to learn alot more about Linux, which I personally feel will be very useful sonner than later.

---

### Post by SonicSteve on 2009-07-15
> **skryzak said:**
> thanks! i have a seasoned ubuntu user who's helping me set up, i can ask him to dual boot at least for the first few weeks.


One thing that would be helpful to know is that it's much easier to setup the dual boot by installing windows first!

Ubuntu can recognize a windows installation but windows is clueless to anything but other windows installs. What works best is to setup the partitions you want to end up with, install windows, then linux on the remaining partitions.

---

### Post by raymondh on 2009-07-15
> **SonicSteve said:**
> One thing that would be helpful to know is that it's much easier to setup the dual boot by installing windows first!


I have to disagree, sorry :)  

Whilst it's true that installing after windows, GRUB will set-up and overwrite on the MBR hence make it seem much easier..... what happens if GRUB mis-fires or installs wrong (which you know happens)? Then the operator will still need to re-install/fix/re-edit GRUB.

Which is really easier?  I say either method.  We can install either OS first.  Great if GRUB sets-up well. If not, or we install windows last, it also is a easy fix.....even for beginners. 

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Sorry ... just my thoughts on the matter.

---

### Post by t4thfavor on 2009-07-15
Hence the reason I say not to install Windows in the first place. You will never have to worry about saving your Windows partition if its not there...

---

### Post by lisati on 2009-07-15
> **SonicSteve said:**
> One thing that would be helpful to know is that it's much easier to setup the dual boot by installing windows first!

Ubuntu can recognize a windows installation but windows is clueless to anything but other windows installs. What works best is to setup the partitions you want to end up with, install windows, then linux on the remaining partitions.

And then again, there's always "Wubi", but that occasionally misfires too....



Edit: Don't be scared to make backups of important data before making changes to your system!

---

### Post by raymondh on 2009-07-15
> **t4thfavor said:**
> Hence the reason I say not to install Windows in the first place. You will never have to worry about saving your Windows partition if its not there...

:lol:

I'm about to reconfigure my test machine again (for the nth time) to simplify.  I'll keep your saying in mind:)  

Am thinking of still multi-boot....but this time sda will be Ubuntu 8.04 with virtualbox and XP (and other distros) as guest whilst sdb will be 9.04 with virtualbox and win7RC as guest.  For the heck of it, I might also put Karmic in sdb to start the tweaking process.

back to the OP and his thread ......

---

### Post by selittl on 2010-07-25
When you get your system post how the setup went (or PM me).  I just ordered a dv6z myself.  I know nothing about the Phenom II processors and just want to know how things go.

---

