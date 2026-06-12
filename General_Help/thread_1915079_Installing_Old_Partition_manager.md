---
title: "Installing Old Partition manager"
date: 2012-01-25
forum: General Help
---

### Post by OooBuntuRox on 2012-01-25
[SIZE=2]Ok, I already tried searching but I'm not really even sure what I am searching for is called.

Can anyone help with installing the old installation/ partition manager that made dual boot installation a little more customizable? It was before Unity came along, I believe it was before Ubuntu 10 and may have been way back in 8.04 or 9.

I don't mind doing a little leg work, but have no idea where to begin on this one. 

Thanks,
[/SIZE] [SIZE=3]**OooBuntuRox**[/SIZE] :guitar:

---

### Post by sudodus on 2012-01-25
Maybe you are remembering Gparted. It is still around :-)

Actually is is included in the iso file, so when you download it you get it and it is available when you have booted a live session from the CD or USB drive.

You can also install it into your installed system from the repositories with
```
sudo apt-get install gparted
``` but remember that you should always run it from another drive, not the drive that you plan to edit.

---

### Post by OooBuntuRox on 2012-01-25
OK,

So if I boot with a live demo USB drive, then go online, type in the code that you mentioned below while in terminal, allow the USB to be updated, then when I choose to do the install it will run  gparted? And it will do that as long as I use that USB drive? I mean after reboot... at least until I upgrade and create a new USB live demo right?

Thanks, OooBuntuRox :guitar:


_**QUOTE: **_
Maybe you are remembering Gparted. It is still around :smile:

Actually is is included in the iso file, so when you download it you get  it and it is available when you have booted a live session from the CD  or USB drive.

You can also install it into your installed system from the repositories with
     [COLOR=Red][B]Code:
     sudo apt-get install gparted [/B][/COLOR]

 but remember that you should always run it from another drive, not the drive that you plan to edit.

---

### Post by dcstar on 2012-01-25
> **OooBuntuRox said:**
> Ok, I already tried searching but I'm not really even sure what I am searching for is called.

Can anyone help with installing the old installation/ partition manager that made dual boot installation a little more customizable?
..........

Partition Managers have nothing to do with dual boot installations, they simply manage the partitions on the disk(s).

If you are referring to the Grub boot manager then there are various packages and tools to change the setup of that.

---

### Post by sudodus on 2012-01-26
> **OooBuntuRox said:**
> OK,

So if I boot with a live demo USB drive, then go online, type in the code that you mentioned below while in terminal, allow the USB to be updated, then when I choose to do the install it will run  gparted? And it will do that as long as I use that USB drive? I mean after reboot... at least until I upgrade and create a new USB live demo right?

Thanks, OooBuntuRox :guitar:

Sorry for a bad explanation. No, Gparted is there on the live Ubuntu USB drive from the beginning. You need not install it.

But if you want it in your regular installed Ubuntu on the hard disk drive, you need to install it. That would make it easier to edit the partitions on external USB drives.

---

### Post by cryptotheslow on 2012-01-26
dcstar is correct.

You are referring to configuring / customising the boot up options screen. You would not use a partition manager to achieve that.

Search the forum for "Customise GRUB 2"

This is a good resource:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


Ensure any instructions or tutorials you find are intended for GRUB2 rather than the earlier GRUB.

---

### Post by sudodus on 2012-01-26
Well, [OooBuntuRox]("http://ubuntuforums.org/member.php?u=860037"),

Maybe I gave you the wrong answer. I use Gparted to edit the partitions on a [hard disk] drive before installation. But the other guys might be right, that you are actually asking about configuring the settings for the boot procedure of the operating systems installed on your drive, and that is something else ...

---

### Post by OooBuntuRox on 2012-01-26
[SIZE=2]I would like to say thanks to all for the input. Perhaps I need to clarify what I mean.

OK, when you are doing any new install of Ubuntu, not an upgrade but a new install and it just so happens, a dual boot machine (Windows XP existing), you must partition the drive to some degree.[/SIZE] [SIZE=2]

At minimum, I believe you need a linux partition and a swap partition (something like type 83 and type 84). Those are specs I've seen but I am sort of clue less about the rest. I can't say I can confidently and manually position, size, and format those partitions. If I guessed at the values, I may overwrite the exisiting partitions.[/SIZE] [SIZE=2]

Since The Unity interface came along, you can't simply select "install Ubnutu in the largest freespace" while doing a dualboot install. It gives you the option to manually lay out the partitions or install Linux next to Windows. I believe that means that windows and Linux wind up on the  same partition. I don't want that. I want windows in a partition on the front of the Hard drive and Linux in a partition at the end of the hard drive.[/SIZE] [SIZE=2]

So what is the application, or utility, or installer, or even interface that I am referring to? For all I know, this process is part of the Gnome interface. I would like to be able to partition the whole hard drive that already has an [/SIZE] [SIZE=2]***active primary/ boot partition with windows*** on it, then create a Linux boot partition in the hard disks extended partition. I also want to have other logical drives in that extended partition that can be used by either windows or linux depending on what I have select from Grub during boot. I believe Grub is becomes the boot strap loader once the system is set up for multi-OS booting.

So that is what I am trying to do, as best I know how to explain it.

So what do I need to search for and read up on? I'm not sure where to begin. Especially since I have conflicting answers.

I'm not sure, but I think this may be it as SUDOUS mentions:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)[/SIZE]
[SIZE=2]
**Taking a guess: **Gparted= Gnome Partition Editor

So if gparted is what I need, the next trick will be to add the version of Gparted to any USB drive that I choose/ have with a live Boot Ubuntu ISO already installed on it.

Thanks for your help/ patience, OooBuntuRox :guitar:

[/SIZE]

---

### Post by sudodus on 2012-01-26
So it is Gparted you need :-) I'm cutting and pasting from a recent post of mine (about the same thing)
--
- backup your system (because it is risky to edit partitions)

- defragment the windows partition

- make new partitions with gparted. I suggest
. shrinking the windows partition to get free space and
. making an extended partition with
. one logical partition for the linux file system ext3 or ext4 and
. one logical swap partition of at least the same size as the RAM
using the free space. Run gparted from a live session booted from the Ubuntu installation CD or USB drive).

- install Ubuntu. When asked about partitions, select the manual method and tell it to select the new ext partition for the linux file system /. It will select the swap partition automatically.

Please ask if you are not sure! It is better to ask before doing something you are not sure about.

*Edit: gparted is there already (on your Ubuntu installation drive)*

---

### Post by OooBuntuRox on 2012-01-26
> **sudodus said:**
> So it is Gparted you need :-) I'm cutting and pasting from a recent post of mine (about the same thing)
--
- backup your system (because it is risky to edit partitions)

- defragment the windows partition

- make new partitions with gparted. I suggest
. shrinking the windows partition to get free space and
. making an extended partition with
. one logical partition for the linux file system ext3 or ext4 and
. one logical swap partition of at least the same size as the RAM
using the free space. Run gparted from a live session booted from the Ubuntu installation CD or USB drive).

- install Ubuntu. When asked about partitions, select the manual method and tell it to select the new ext partition for the linux file system /. It will select the swap partition automatically.

Please ask if you are not sure! It is better to ask before doing something you are not sure about.

*Edit: gparted is there already (on your Ubuntu installation drive)*

[SIZE=2]
I just installed and played with Gparted. Just to check the features and all.  I did not modify anything. I think Gparted is only part of what I am asking. Because, technically, I could set up all the partitions in windows, or at least set up a Windows extended partition with logical drives.

The portion of the install that I am having trouble with is whatever code segment looks at the partitions once they have already been completed, then makes the decision as to how those partitions should be viewed or interpreted, then installs the OS onto a partition. Whatever this software is, also allows you to select WHERE or WHAT partition the OS will be installed onto. At this point during the install,you do not have the option to create or adjust partition sizes. But, the old software could distinguish between partition sizes and if they were the largest portion freespace or not. It would next allow you to select: [/SIZE] [SIZE=2]**install on the largest segment of freespace** for Ubuntu.

Since Unity came along, or not long before Unity came along , that option does not appear anymore. Not that I notice anyway.

OooBuntuRox :guitar:

[/SIZE]

---

### Post by sudodus on 2012-01-26
> **OooBuntuRox said:**
> [SIZE=2]
... The portion of the install that I am having trouble with is whatever code segment looks at the partitions once they have already been completed, then makes the decision as to how those partitions should be viewed or interpreted, then installs the OS onto a partition ...
[/SIZE]
As I wrote before: from the live session of the 'Ubuntu install' CD or USB drive:

- install Ubuntu. When asked about partitions, select the manual method and tell it to select the new ext partition for the linux file system /. It will select the swap partition automatically.

This is something I have done several times, so I know that it works.

---

### Post by sudodus on 2012-01-26
Just to show you what it looks like when running a live Ubuntu 11.10 session:

Installation type
- Install Ubuntu alongside
- Erase disk and install Ubuntu
- [COLOR="Red"]Something else[/COLOR]
You can create or resize partitions yourself, or choose multiple partitions for Ubuntu
--
Click on the thumbnail to see the attached screenshot!

---

### Post by mcduck on 2012-01-26
The option for installing on the largest free space is in no way related to Unity (which is a desktop shell and has nothing to do with this kind of stuff). And also the option *is still there*. It will only show if you actually have some *unpartitioned*, free space on the drive, and it's actually possible to create new partitions without removing or overwriting any existing ones (so you need to have three or less primary partitions, or the free unpartitioned space must be inside an extended partition). This, by the way, is how it has always worked...

---

### Post by ottosykora on 2012-01-27
> **mcduck said:**
> The option for installing on the largest free space is in no way related to Unity (which is a desktop shell and has nothing to do with this kind of stuff). And also the option *is still there*. It will only show if you actually have some *unpartitioned*, free space on the drive, and it's actually possible to create new partitions without removing or overwriting any existing ones (so you need to have three or less primary partitions, or the free unpartitioned space must be inside an extended partition). This, by the way, is how it has always worked...

+1

if you want something to

'install on the largest segment of freespace'

you first need to have this largest segment of free space, if you have no free space on your disk it is pointless to display this choice and therefor you do not see it. 
So a free space is something where no partition exists. If you use partitioning sofware like gparted free space looks gray there, no color frames around it.

---

### Post by OooBuntuRox on 2012-06-03
Hello Everyone,

Thanks for your help. I eventually learned how to manually configure and partition the drive. Being that XP is fading away and most if not all my system errors are related to using XP, I got away from a dual boot system.

I now manually configure multiple partitions and a swap area.

OooBuntuRox :guitar:

---

