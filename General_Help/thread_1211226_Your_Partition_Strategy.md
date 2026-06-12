---
title: "Your Partition Strategy"
date: 2009-07-12
forum: General Help
---

### Post by masterton on 2009-07-12
For people who would dual-boot Windows and Linux/Ubuntu, how do you partition your drive(s)? What is the best way to partition the drives?

What file system do you use for Linux, ext3 or ext4? Why?
(For Windows I believe most should use NTFS now)

Do you share the user data between Windows and Linux, or each OS has its own data?

---

### Post by fallingleaf on 2009-07-12
I recently set up my wife's computer to dual boot and am trying to slowly transition her to Ubuntu from WinXP.  I set up her Windows partition to mount in fstab and then set up a symlink to "My Documents" in her home folder.  I also set up a symlink for her firefox profile on Windows and it worked great.  Only thing is you have to rename the firefox directory in Windows with a lower-case "f".  Now if she gets frustrated with Ubuntu she can just boot into windows and everything is up to date.

It was a bit tricky getting the Windows NTFS partition to mount read/write and allow trashing files instead of permanently deleting them. I can't remember what the trick was though :(

---

### Post by fallingleaf on 2009-07-12
Oh, yeah.  That was the data sharing part.  Partitioning is kind of a matter of preference.  I think a /home partition is a good idea.  As for file system I have used reiserfs, ext3 and ext4 and never had any problems with any of them.

---

### Post by Wim Sturkenboom on 2009-07-12
I have 5 partitons for a simple dual boot
Windows OS
Windows My Documents
Linux Swap
Linux OS (/)
Linux /home

I used to have a 4GB FAT32 partiton for sharing, but nowadays use external HD or memory stick for that.

---

### Post by jskandhari on 2009-07-12
I have SIX OS running on my laptop and more in virtualization

namely

1) Ubuntu 9.04 desktop Edition
2) Ubuntu 9.04 Netbook remix
3) Windows 7 build 7100
4) Windows Vista Home Premium
5) Windows Server 2008
6) Mac OSX Leopard

So basically i used my Win Vista for first partitions that i wanted for manually selecting the partions for required for then.

I use a mix of windows diskpart ( command promt powerfull tool of windows) and gpart of ubuntu for the rest.

Eventually i shrunk Vista to 50GB from 122GB which windows won't let me do.

---

### Post by masterton on 2009-07-12
> **fallingleaf said:**
> Oh, yeah.  That was the **data sharing part**. 
What do you mean by that? How did you setup to share data? Would you explain a bit more?
By the way, isn't ubuntu able to read/write from NTFS now?

> **fallingleaf said:**
> Partitioning is kind of a matter of preference.  I think a /home partition is a good idea. 
So you are using one partition for root (/), one partition for /home right now, aren't you?

> **fallingleaf said:**
> As for file system I have used reiserfs, ext3 and ext4 and never had any problems with any of them.
Which file system do you prefer, and why?

---

### Post by fallingleaf on 2009-07-12
> **masterton said:**
> What do you mean by that? How did you setup to share data? Would you explain a bit more?
By the way, isn't ubuntu able to read/write from NTFS now?]

For instance, if you want to have your Windows "My Documents" folder show up in your home directory, assuming the windows partition is mounted at /windows
```

cd
ln -s "/windows/Documents and Settings/USER/My Documents
```
similarly you can link the firefox prefs folder in Windows with something like:
```

cd ~/.mozilla
ln -s "/windows/Documents and Settings/USER/Application Data/Mozilla/Firefox" firefox
```

Yes, Ubuntu can read/write ntfs by default.  Normally you have to manually mount the partition every boot but I wanted it mounted all the time so I put it in fstab.

> So you are using one partition for root (/), one partition for /home right now, aren't you?

Yeah, that's my setup. I have another partition available in case  I want to experiment with another distro.  That's also handy if you want to do a clean install instead of an upgrade, then you have the old version of Ubuntu as a fallback in case something goes wrong.
> Which file system do you prefer, and why?

 I don't really have a favorite filesystem.  I have tried those 3 and I haven't noticed any particular difference.  I haven't researched it too much.  I guess the time you most notice your FS is when it fails :)

---

### Post by Shazaam on 2009-07-12
Mine...

Original setup-
One hard drive, 80gig.
1. Windows first, NTFS.
2. Dedicated swap partition (Primary).
3. Extended partition to fill the hard drive.
4. Multiple Logical partition(s) INSIDE of the Extended partition for Linux (ext3) sharing the dedicated swap partition and one Fat32 (or NTFS) Logical partition.

Current setup-
Two hard drives.
1. One drive used entirely by Windows (80gig).
2. Other drive (320gig) same as 2-4 above (minus the shared NTFS partition).

---

### Post by itsjareds on 2009-07-12
This is my setup.

- Windows XP on partition 1
- Windows 7 on partition 2
- Ubuntu Jaunty on partition 3
- Dedicated swap partition

I originally had Jaunty under the ext4 filesystem when I first installed, but then I heard about its instability. I also could not find a Windows driver that reads ext4 filesystems. So I re-installed Ubuntu as an ext3 filesystem and then went back to Windows to add some fs readability. I installed [Ext2fsd]("http://ext2fsd.sourceforge.net/") on both of my Windows partitions and I'm now able to work with my Ubuntu partition completely fine, except for adding items to trash rather than delete.

Installing Ext2fsd on my Windows 7 boot created a BSoD when I rebooted, but I just figured this was because I put a driver on it that wasn't made for Win7. I could still read the partition fine when I opened Explorer, then when I opened a file I got a blue screen. I restarted, booted back into Win7 and everything has been fine since then.

So, I only have 3 physical partitions, each with its own operating system. I can read all of my partitions from each OS seamlessly. Works for me.

---

