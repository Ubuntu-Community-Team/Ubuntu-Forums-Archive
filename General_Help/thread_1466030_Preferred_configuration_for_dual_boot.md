---
title: "Preferred configuration for dual boot"
date: 2010-04-29
forum: General Help
---

### Post by Myth123 on 2010-04-29
Hi,
    I got a new laptop having windows 7 preinstalled. Now I want to dual boot it by installing ubuntu as second os. I will be using ubuntu as primary, and windows 7 only if its absolute necessary.
How can i make home folder common for both os?
I mean (Users/mithun in windows 7 should be mapped to my home folder in ubuntu). I would also like to know what others do (hd partitioning etc) while dual booting.

---

### Post by carl4926 on 2010-04-29
You can't
Windows is unable to read linux ext4 file systems.

But you can sync your Documents or whatever from Linux to Winders.

---

### Post by 2hot6ft2 on 2010-04-29
I know where there is a guide for what you want. I'll be back in a minute with a link to it.

Here it is
[Dual-Boot Windows 7 and Ultimate in Perfect Harmony]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=570")

P.S. Ultimate is Ubuntu Ultimate Edition

---

### Post by Myth123 on 2010-04-29
> **carl4926 said:**
> You can't
Windows is unable to read linux ext4 file systems.

But linux can read ntfs. Can we use that route?

---

### Post by wilee-nilee on 2010-04-29
> **Myth123 said:**
> But linux can read ntfs. Can we use that route?
 Yes it can.

---

### Post by carl4926 on 2010-04-29
> **Myth123 said:**
> But linux can read ntfs. Can we use that route?
Yep, no problem
I just copy my documents directly in to My Documents in winders and whatever else to wherever...

---

### Post by Myth123 on 2010-04-30
> **2hot6ft2 said:**
> 
Here it is
[Dual-Boot Windows 7 and Ultimate in Perfect Harmony]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=570")

Thanks for the link. 
Its very good for keeping your documents, pictures etc folders common.
Actually I was thinking of mounting home folder of ubuntu directly to Users folder of windows 7. So that whatever goes to home, goes to Users as well. Is it possible? How safe it will be?

---

### Post by 2hot6ft2 on 2010-04-30
> **Myth123 said:**
> Thanks for the link. 
Its very good for keeping your documents, pictures etc folders common.
Actually I was thinking of mounting home folder of ubuntu directly to Users folder of windows 7. So that whatever goes to home, goes to Users as well. Is it possible? How safe it will be?
You're welcome.
Sounds pretty risky to me. If I'm understanding you right then if windows crashed you would lose everything both windows and your home folder since it would be in windows.
Also I don't know if it would work right since linux uses ntfs-3g to read the NTFS file system if it's not loaded early enough during boot then it wouldn't be able to load your settings, profiles and everything since almost all of it is in the home folder.
Home is very important. That's why people like to protect it by having it on a separate partition or at least back it up regularly.

Windows at least some versions can read some versions of linux file systems with an application. I don't know if it will work with win 7 yet and I'm pretty sure it wont work with ext4.

[Ext2fs Utilities]("http://e2fsprogs.sourceforge.net/ext2.html")
> The following Ext2fs Utilities are available:

    * e2fsprogs, which consists of e2fsck, mke2fs, debugfs, dumpe2fs, tune2fs, and most of the other core ext2fs filesystem utilities.
    * dump, which will allow you to make backups of your ext2 filesystems. It uses a format which is compatible with the BSD dump and restore programs.
    * defrag, which will defragment your ext2 filesystem
    * ext2ed, which is a text/windows (curses) interface for examining and editing an ext2 filesystem. It unfortunately is limited to filesystems smaller than 2GB, and is heavily Intel byte order dependent, and has apparently been abandoned by its original author. (So for those people who were used to seeing ext2ed in older Linux distributions, and wondered where it went to, that's the explanation.)

      It has been integrated into e2fsprogs version 1.28, but its limitations mean that it should only be used by developers who need to generate test cases.
    * **Ext2fsd, An ext2 filesystem driver for Windows NT/2K/XP. The most recent version has read-write support.** 

Hope that will help you with the choices you have.
:popcorn:

---

### Post by sgage on 2010-04-30
I have been dual-booting Linux and Windows for years now. Basically, any data that you want to access in Windows has to be in the Windows partition (or some ntfs or fat partition).

I use Thunderbird and Firefox on both platforms, with the message store on Windows. You simply point Thunderbird to the right directory in the account preferences, no problem. That and a few symlinks, and TB and FF are totally transparently usable under both platforms. Address book, bookmarks, cookies, passwords etc. - the same files are used.

Similarly, I use OpenOffice on both platforms - I just keep documents on the Windows partition. No problem.

Ditto my music collection.

I almost never boot into Windows, but I do occasionally need to for work purposes (although Crossover Office is just about to take care of that need). And when I do boot into Windows, I hardly even notice - it's just another funky window manager or something :P

I generally use the Windows boot loader, and install grub on my root Linux partition. Some Windows system tools really like to see an orthodox MBR. It's easy to install grub into the Ubuntu root partition - it's right at the end under "advanced".

I use the free EasyBCD to set up an entry in the Windows boot loader for Ubuntu. Use the latest version of EasyBCD - it can handle grub2, and make sure the root Ubuntu partition is a primary partition.

I've been doing it this way for a long time without ever a problem. It's really quite nice, and once it's set up, totally effortless.

---

### Post by 2hot6ft2 on 2010-04-30
> **Myth123 said:**
> 
**How can i make home folder common for both os?**
I mean (Users/mithun in **windows 7 should be mapped to my home folder in ubuntu**).

> **sgage said:**
> 
Thunderbird and Firefox on both platforms, Address book, bookmarks, cookies, passwords etc. - the same files are used.
Similarly, I use OpenOffice on both platforms - **I just keep documents on the Windows partition.** No problem.

**Ditto my music collection.**

Those are all applications that are started after the OS loads, and things accessed by them after it loads.
Not quite the same as having the home folder in common for both OSes.
Good information just the same.
It's along the same lines as the guide that I linked to earlier where both operating systems have access to things. Only difference is instead of using another partition from both OSes it just links from ubuntu to windows.
Still less secure due to the fact everything would be stored in windows. In my opinion.

---

### Post by sgage on 2010-04-30
Life is full of uncertainties. :)

If one needs to dual-boot, as I do (sort of), this can be a convenient way to do it. Basically, I'm just using an ntfs partition as my data partition - once a week or so I boot into Windows. Home partition is still in Ubuntu. 

Part of the thing is that I have a ton of old data that I'd like to have accessible wherever I am, and that means it needs to be on an ntfs (or fat) partition. 

But this thread has gotten me wondering why I boot into Windows at all. Habit? The one Windows app I "need" to access perhaps 3 times a week works fine under Crossover.

Seriously, I've been dual-booting this way for 12 years, and just always figured "gotta have a Windows installation just in case". In case of what, I wonder...

---

### Post by 2hot6ft2 on 2010-04-30
> **sgage said:**
> Life is full of uncertainties. :)

If one needs to dual-boot, as I do (sort of), this can be a convenient way to do it. Basically, I'm just using an ntfs partition as my data partition - once a week or so I boot into Windows. Home partition is still in Ubuntu. 

Part of the thing is that I have a ton of old data that I'd like to have accessible wherever I am, and that means it needs to be on an ntfs (or fat) partition. 

But this thread has gotten me wondering why I boot into Windows at all. Habit? The one Windows app I "need" to access perhaps 3 times a week works fine under Crossover.

Seriously, I've been dual-booting this way for 12 years, and just always figured "gotta have a Windows installation just in case". In case of what, I wonder...
:lolflag:same here but I may boot windows once every few months. I think I just keep it around because of the software I paid for over the years that doesn't have a linux version (media monkey, and divx converter come to mind). Guess I need to see if crossover will support them so I can free up that space widows is wasting.

It doesn't support either of those.:(

Update: I did get media monkey working in WINE by upgrading wine with the PPA. Sure does use a lot of resources though. 1/2 way there.

---

### Post by Myth123 on 2010-04-30
> **2hot6ft2 said:**
> 
Sounds pretty risky to me. If I'm understanding you right then if windows crashed you would lose everything both windows and your home folder since it would be in windows.
Also I don't know if it would work right since linux uses ntfs-3g to read the NTFS file system if it's not loaded early enough during boot then it wouldn't be able to load your settings, profiles and everything since almost all of it is in the home folder.
Home is very important. That's why people like to protect it by having it on a separate partition or at least back it up regularly.

Thanks.
Risks are real and so I have decided not to try mapping, instead going for symlink approach.


Here is my reason for dual booting laptop: I have a samsung mobile, software of which only works with windows, sometimes I do .net development, and MS Office is a must. I think most of us can agree that openoffice is not as matured as that of msoffice. My desktop runs only ubuntu and I am very happy about it.

Thanks you all for such a great information :)

---

### Post by 2hot6ft2 on 2010-04-30
> **Myth123 said:**
> Thanks.
Risks are real and so I have decided not to try mapping, instead going for symlink approach.


Here is my reason for dual booting laptop: I have a samsung mobile, software of which only works with windows, sometimes I do .net development, and MS Office is a must. I think most of us can agree that openoffice is not as matured as that of msoffice. My desktop runs only ubuntu and I am very happy about it.

Thanks you all for such a great information :)
Sounds like a good decision to me. Doing .net framework development would make it a necessity to boot windows to do that type of work as far as I know.
You're welcome for the info. glad to help.

---

