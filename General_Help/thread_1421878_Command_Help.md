---
title: "Command Help"
date: 2010-03-04
forum: General Help
---

### Post by neu5eeCh on 2010-03-04
Hi folks. I'm running Ubuntu 9.10 on a USB/Live stick (with persistence). Whenever I try to run package manager, I get the following:

> W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)/dists/karmic/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)/dists/karmic/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ sudo apt-cdrom
apt 0.7.23.1ubuntu2 for amd64 compiled on Oct 15 2009 19:26:37
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp



Ubuntu is telling me everything I need to know, but I don't quite have enough experience to fit it all together.

Can anyone help me with the apt-cdrom syntax?

---

### Post by wojox on 2010-03-04
Could you copy and paste you /etc/apt/sources.list up here? The command you be:

```
cat /etc/apt/sources.list
```

And put them in the # Wrap [Code] tags please.

---

### Post by neu5eeCh on 2010-03-04
Here it is. Not sure what info is and isn't important so I've pasted it all.

> deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse



deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

---

### Post by neu5eeCh on 2010-03-04
Unless I'm mistaken. Isn't Ubuntu asking me to point the package manager to the USB?

---

### Post by 2hot6ft2 on 2010-03-04
> deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
Is telling it to look at the livecd. Comment it out by adding the # to the beginning like this
> #deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
Might want to uncomment these by removing the # from the beginning of each and any space while you're at it.
> # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


To be like this
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


---

### Post by pastalavista on 2010-03-04
It looks like a SoftwareSources problem. You aren't using a "LiveCD" copy are you? It looks like your repositories are very restricted. 

Or did you do a full install to the flash drive?

---

### Post by neu5eeCh on 2010-03-04
Damn!

Like magic. I look forward to the day when this comes as naturally to me, as to you.

I see everything you've done and it makes perfect sense. Note to self: Remember location of apt sources list.

---

### Post by 2hot6ft2 on 2010-03-04
> **pastalavista said:**
> It looks like a SoftwareSources problem. You aren't using a "LiveCD" copy are you? It looks like your repositories are very restricted. 

Or did you do a full install to the flash drive?
That's one of those usb startup disk creator deals with changes (persistance) System > Administration > USB Startup Disk Creator

Or one of the other apps that do it that way. Basically it copies the iso to usb, makes it bootable, and uses a file to save changes.

---

### Post by neu5eeCh on 2010-03-04
> **pastalavista said:**
> It looks like a SoftwareSources problem. You aren't using a "LiveCD" copy are you? It looks like your repositories are very restricted. 

Or did you do a full install to the flash drive?

I'm using a LiveCD copy (burned from an ISO with persistence). Maybe this isn't such a great idea?

Problem is, I don't know how to do a full install from Windows 7? My Linux Box is 32 Bit. And I wasn't sure that I could do a 64 bit install on a 32 bit box - but maybe it doesn't matter (since I'm only running Ubuntu off a USB drive for now). My 64-bit box runs Win7 and I'm not yet ready to partition that drive. If I do, I will lose some of 7's recovery features.

On second thought... maybe I could install AMD64 on a temporary USB key. Boot from that, then do a complete install on my other 8 Gig USB key?

Here's the question: How do I prevent the procedure  from installing GRUB on the Hard Drive? I'm being very cautious.

---

### Post by wojox on 2010-03-04
That is weird. Universe and multi are commented out. I'll have to make one of those usb sticks one day.

---

### Post by 2hot6ft2 on 2010-03-04
> **VTPoet said:**
> I'm using a LiveCD copy (burned from an ISO with persistence). Maybe this isn't such a great idea?

Problem is, I don't know how to do a full install from Windows 7? My Linux Box is 32 Bit. And I wasn't sure that I could do a 64 bit install on a 32 bit box - but maybe it doesn't matter (since I'm only running Ubuntu off a USB drive for now). My 64-bit box runs Win7 and I'm not yet ready to partition that drive. If I do, I will lose some of 7's recovery features.

On second thought... maybe I could install AMD64 on a temporary USB key. Boot from that, then do a complete install on my other 8 Gig USB key?

Here's the question: How do I prevent the procedure  from installing GRUB on the Hard Drive? I'm being very cautious.
I did a full install on a usb stick but 9.10 wouldn't boot right it kept dropping me to the inramfs prompt and I couldn't find a solution so I ended up installing 8.10 on it.

I removed my hard drive in the laptop and booted from the livecd.
Once that was up and running I inserted the usb flash drive and ran the installer.

When it gets to the last step you have to click on the Advanced button and choose the /dev/sdb or whatever it is for your usb stick to make sure that grub gets installed there because by default it will be pointing to hd0 which is not the usb stick.

That way there was no way it was going to mess with my hard drive.
Once it was installed I rebooted removing the livecd in the process and it booted to the usb stick.

I ran all the updates and rebooted again.
Installed my graphics driver and rebooted again.
Then I shut the pc down and put my hard drive back in.
Works great. Just wish 9.10 would have worked.

---

### Post by pastalavista on 2010-03-04
You really shouldn't try and run 64 bit software on 32 bit hardware. Bad idea all around. You could do a full install on the 8gig drive if you make sure to manually set the partitioner to install the boot sector on the same drive.

---

### Post by neu5eeCh on 2010-03-04
Great 2hot! Thanks for all that advice.

I may try 9.10 just to see if it works. At the very least, we'll know if it's a computer specific problem. The LiveUSB is ok, but it's becoming apparent that a complete install would be better.

---

### Post by 2hot6ft2 on 2010-03-04
I should add I used the 32 bit OS, formatted the USB to ext2 and gave it about 700 MB of a swap partition.

Also 9.10 would boot up fine AS LONG AS THE HARD DRIVE WAS NOT IN THE PC.
Once I put the hard drive in it would fail like I said dropping to the inramfs prompt.

---

### Post by neu5eeCh on 2010-03-04
> **2hot6ft2 said:**
> I should add I use 32 bit, formatted it to ext2 and gave it about 700 MB of a swap partition.

Also 9.10 would boot up fine AS LONG AS THE HARD DRIVE WAS NOT IN THE PC.
Once I put the hard drive in it would fail like I said dropping to the inramfs prompt.

Interesting... wouldn't that point to a BIOS issue?

---

### Post by 2hot6ft2 on 2010-03-04
> **VTPoet said:**
> Interesting... wouldn't that point to a BIOS issue?
No I did a lot of searching and it seems that 9.10 creates a .lz where it should be creating a .gz file or something like that (I don't recall exactly now). I don't recall off hand where it was but a google search for ubuntu 9.10 bootable usb inramfs problem or some variation of that will lead you to others that have had the same problem.

Remember you're looking for those that did FULL USB Installs.

---

### Post by neu5eeCh on 2010-03-04
Hmmm... looks like I'm bumping into more limitations. When I try to install packages, I get:

> installArchives() failed: dpkg: unrecoverable fatal error, aborting: 
 fgets gave an empty string from `/var/lib/dpkg/diversions'

I'll bet this is another easy solve.

---

### Post by 2hot6ft2 on 2010-03-04
> **VTPoet said:**
> Hmmm... looks like I'm bumping into more limitations. When I try to install packages, I get:



I'll bet this is another easy solve.
That one beats me but I'll bet it's because it can't actually change the files in the iso on the usb. All the persistent changes does is write stuff to a file to save changes but not the iso file itself.

---

### Post by 2hot6ft2 on 2010-03-04
Here's a pic of the desktop on the USB Install I did.
:popcorn:

---

### Post by neu5eeCh on 2010-03-04
Drats. Oh well... it keeps me learning.

Either that, or I may partition my Windows 7 drive. From what I've read, one should use win7's own partition manager and even then it can get dicey.

---

### Post by neu5eeCh on 2010-03-04
> **2hot6ft2 said:**
> Here's a pic of the desktop on the USB Install I did.
:popcorn:

Very nice! This is 8.10? Looks like you've moved the Gnome Panel to the bottom and you're using Gno-Menu. Sweet. 

Have you been tempted to needlessly upgrade 8.10 to 9.10 with a -d switch just to see what happens?

---

### Post by 2hot6ft2 on 2010-03-04
> **VTPoet said:**
> Drats. Oh well... it keeps me learning.

Either that, or I may partition my Windows 7 drive. From what I've read, one should use win7's own partition manager and even then it can get dicey.
Yeah it's always best to use windows disk cleanup and defrag then the windows partitioner to resize the windows partition. Then if it doesn't let you shrink it as much as you wanted reboot then try again. Windows doesn't like a small partition since windows expands to fill any partition it's on.

---

### Post by 2hot6ft2 on 2010-03-04
> **VTPoet said:**
> Very nice! This is 8.10? Looks like you've moved the Gnome Panel to the bottom and you're using Gno-Menu. Sweet. 

Have you been tempted to needlessly upgrade 8.10 to 9.10 with a -d switch just to see what happens?
Yes it's 8.10. I themed it to look pretty close to windows 7 just for a laugh and the shock effect. Besides if you're using someone elses pc they see it looks like win7 so they don't realize you're running linux. That's pretty good you caught the Gno-Menu, it's version 1.6 of Gno-Menu.

And no I don't want an upgrade to make it not work like the 9.10 install. Maybe they will fix that issue in 10.04.

---

### Post by neu5eeCh on 2010-03-04
> **2hot6ft2 said:**
> And no I don't want an upgrade to make it not work like the 9.10 install. Maybe they will fix that issue in 10.04.

My thinking was that since it's already installed, an upgrade might not cause the same issues as a straight 9.10 install. In other words, an upgrade, rather than a straight install, might be a work around.

---

### Post by 2hot6ft2 on 2010-03-04
> **VTPoet said:**
> My thinking was that since it's already installed, an upgrade might not cause the same issues as a straight 9.10 install. In other words, an upgrade, rather than a straight install, might be a work around.
I may get a wild hair and try it sometime but I put a bit of work into getting it like that and would hate to go back to square 1. I could use some of the features in 9.10 like getting the windows to snap like win7 which I can't do with the compiz manager that 8.10 has.

---

### Post by neu5eeCh on 2010-03-04
I'll play around and try it. When I do, I'll let you know.

---

### Post by 2hot6ft2 on 2010-03-04
> **VTPoet said:**
> I'll play around and try it. When I do, I'll let you know.
Sounds good, and good luck with it. Most of all have fun with doing it.

---

### Post by neu5eeCh on 2010-03-06
> **2hot6ft2 said:**
> Sounds good, and good luck with it. Most of all have fun with doing it.

Right... so... I experimented this afternoon. I took out the hard drive and, based on your experience, installed 8.04. However, 8.04 doesn't support 1080P and it didn't recognize my wireless device. The computer was usable, but not passably so.

I started my upgrade path (all with the hard drive still out). It took about an hour to download the new packages (for 8.10), and then... (drum roll) I was informed that the upgrade would take 16 non-stop hours.

Wow.

I would have had to wait 16 hours for each upgrade (Ubuntu claims that one can't jump from 8.04 to 9.04 or 9.10). Three hours into it, I pulled the plug. 

After that, I reinstalled 9.10 on the stick and was able to boot into 9.10 even with the hard drive in place. For some reason, it just worked.  So... for now, I'm happy. When I want to use 9.10 on my Win7 laptop, I can.

---

