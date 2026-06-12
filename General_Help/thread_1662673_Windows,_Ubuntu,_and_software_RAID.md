---
title: "Windows, Ubuntu, and software RAID"
date: 2011-01-08
forum: General Help
---

### Post by man-man on 2011-01-08
I've just set up a software RAID5 array using dynamic disks under Windows XP. This was to replace a smaller spanned volume, but I wanted to use one of the drives from that spanned volume (which can't be broken up without data loss). NB, this is all purely a data volume, the OS is on a separate physical disk.

So, my original plan was
[LIST=1]
[*]RAID together 3 discs
[*]Transfer the data across
[*]Break up the spanned volume
[*]Extend the array onto the 4th disc
[/LIST]

I reached the end stage, and realised I'd been mistaken when I thought it was possible to extend a RAID5 array using the Windows DiskPart tool. So I now have 3 discs in RAID5, a 4th disc I'd like to be in RAID5, and enough backup space to store everything if I need to trash the array and start over. I could just rebuild the array from scratch with 4 discs, but the initial setup took rather a while the first time around and I'd be kinda screwed if I ever want to extend it in the future. 

I think I'm right in saying (read: [this guy]("http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/") said so) that mdadm on Linux is able to do the kind of extend operation I'm looking for (correct me if I'm wrong) but exactly which combinations of OS and RAID format will play nicely together I'm less sure on, so I'm hoping someone can tell me whether it's possible to do any of the following.

[LIST]
[*]Extend the array using some other Windows tool. If there is such a tool. which I'm not holding out a lot of hope for.
[*]Install Linux on some spare space on the OS drive, extend the array using mdadm, then return to Windows and use the extended volume. But this relies on Linux being able to mount and extend a Windows-flavoured RAID array, and without breaking compatibility with Windows.
[*]Break up the current array and use Linux to set up a shiny new one that spans all 4 disks (I'm assuming I'd then be able to extend that at will in the future), then access that array from Windows. But this relies on Windows being able to use a Linux RAID array.
[*]Some sort of hybrid solution I've not considered, if it ends up with an extensible RAID5 array that I can use from Windows. All suggestions welcome
[/LIST]

I have considered the "to hell with Windows, this is a Linux box from now on" option, or dual booting, but I'm quite attached to my Steam games and certain software and dual booting is always a pain. Might turn out to be a choice between that, or living with an inextensible Windows array, but I'm hoping there's something else to be done.

Then there's this past thread that looked useful but didn't add up to a conclusive answer:
[can I mount my WinXP software RAID 0 array in Ubuntu/Kubuntu?]("http://ubuntuforums.org/showthread.php?t=833653") - includes a method for mounting Windows RAID under Linux, but the last post suggests it doesn't work for RAID5. 
[chrysocome.net "Virtual Volumes"]("http://www.chrysocome.net/virtualvolumes") - linked to from that thread, claims to give Windows access to EXT2/EXT3/others, including RAID0/1/5, but it's in beta ... anyone have any experience with it?

---

### Post by man-man on 2011-01-08
If anyone were to know things about the current state of support for Dynamic Disks, even. 

Google only seems to find articles/advice threads from years ago, some of which suggest there's a kernel module or a driver to install, but the links for more information are now either dead or end up redirecting to the homepage of 'Tuxera' (devoid of anything useful as far as I can see)

---

### Post by man-man on 2011-01-10
Ok, to hell with it, I'll just try things to see what works and document the results here for posterity.

Current state of play: Looks pretty unlikely that I'm going to find a way to work with a dynamic-disks based RAID5 in Linux, although supposedly the actual RAID format is the same as mdadm and just lacks superblocks (or maybe that's only true of RAID0, who knows, apparently no-one, or at least no-one who's easy to Google on the subject).

In any case, if reports are to be believed, mdadm doesn't want to know about RAID5 (or any other RAID that includes redundancy... so all of them except RAID0 and 'linear') without the superblocks.

So I'm thinking of following [this guide]("http://a1.blogspot.com/2005/08/step-by-step-to-windows-raid-using.html") to setting up coLinux (running in a co-operative VM so both OSs run side by side) to set up a RAID array and serve it up via Samba. Then maybe I'll see if I can use [virtual volumes]("http://www.chrysocome.net/virtualvolumes") to access that array well enough to not need the VM.

That should end up with me in a position where I
[LIST=1]
[*]Have a RAID array
[*]Can resize it in the future
[*]Can access it from either Linux or Windows
[/LIST]
Which is all I ever really wanted for Christmas.

---

### Post by psusi on 2011-01-10
Neither system understands the others' software raid, so you are left with the "to hell with windows" option.

---

### Post by man-man on 2011-01-24
For anyone who comes after me looking for info on this stuff, I reached the point of trying to get coLinux to network nicely with the host OS and hit a wall. 

Partly due to the opacity of Windows networking, partly due to my own unfamiliarity with Linux networking, partly due to the relative oddity of my pre-existing network configuration (which is set up to allow me to move easily from home to university network connections, and attach my laptop to a second ethernet port for a shared internet connection).

Probably nothing insurmountable given time and expertise, but I had neither and retreated grudgingly back to Windows-land to set up a fresh (dynamic disks based) RAID5 on the 4 discs.

So that's that.

---

