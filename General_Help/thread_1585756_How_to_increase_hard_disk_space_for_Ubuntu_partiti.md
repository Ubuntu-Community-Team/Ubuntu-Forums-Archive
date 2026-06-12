---
title: "How to increase hard disk space for Ubuntu partition?"
date: 2010-10-01
forum: General Help
---

### Post by Richiegs on 2010-10-01
My computer has Windows and Ubuntu operating system and each is located in separate partition (dual boot). Now the disk space of Ubuntu partition is about to run out. I wonder how I can increase the disk space of Ubuntu partition. Thank you very much in advance.

---

### Post by andrewthomas on 2010-10-01
If you have XP you can shrink the windows partition with gparted, but if you have Vista or 7, then you need to do the shrink from within windows and then expand your ubuntu partition with gparted.

---

### Post by Richiegs on 2010-10-01
> **andrewthomas said:**
> If you have XP you can shrink the windows partition with gparted, but if you have Vista or 7, then you need to do the shrink from within windows and then expand your ubuntu partition with gparted.

Is there a Windows Vista version for Gparted?

---

### Post by ali999 on 2010-10-01
I jsut did this recently on my windows 7 and ubuntu 10.04 dual boot setup. Wanted to expand ubuntu size because initially i had set it too small. 

- First off backup all your important files just in case. 
- Use the installation disc to boot the live version of ubuntu.
- Run gparted and use it to resize the partitions as needed. This can take a while.

And that is it. Everything should be good to go. This method should work regardless of what operating systems you have installed.

---

### Post by Quackers on 2010-10-01
I've found that the easiest (and safest) way to resize a Vista partition is to go to Start > Right-click on Computer > select Manage, then on the left of the window that opens up select Disk Management. A new window opens up showing your disks and partitions. Just right-click on the Vista partition and select Shrink. A window then opens up with the available shrink space.

---

### Post by ali999 on 2010-10-01
I like my method because I feel that trying to resize a partition while it is being accessed by the operating system is not a good idea. Some files might be opened by the OS at that time and so moving them could be difficult.

---

### Post by Quackers on 2010-10-01
Normally I would absolutely agree with you, ali999. My experience with Vista and GParted is not good, however. There have been a number of cases where the partition has been corrupted.

---

### Post by ali999 on 2010-10-01
Quackers I agree with you about vista there. I remember a year or so ago trying to use gparted to resize a vista and ubuntu dual boot setup to enlarge the ubuntu partition and my vista got corrupted. Had to reinstall it. However, I have used this method multiple times on windows 7 and ubuntu setups and it has worked perfectly every time. Perhaps theres a new version of gparted now that fixes whatever the problem was.

---

### Post by Quackers on 2010-10-01
The same thing happened to me. To be honest it's so quick using the shrink function in Vista/7. It takes about 20 seconds to do the job.
I use GParted Live cd for everything else though.

---

### Post by Richiegs on 2010-10-01
> **Quackers said:**
> I've found that the easiest (and safest) way to resize a Vista partition is to go to Start > Right-click on Computer > select Manage, then on the left of the window that opens up select Disk Management. A new window opens up showing your disks and partitions. Just right-click on the Vista partition and select Shrink. A window then opens up with the available shrink space.

It didn't work when I tried to shrink from Windows. It said Access Denied! By the way, there was a warning sign next to Windows partition when I used Gparted .

---

### Post by Quackers on 2010-10-01
Hmm, it did allow you to click on "shrink" but then said access denied? Were you logged in as an administrator?

---

### Post by Richiegs on 2010-10-01
> **ali999 said:**
> I jsut did this recently on my windows 7 and ubuntu 10.04 dual boot setup. Wanted to expand ubuntu size because initially i had set it too small. 

- First off backup all your important files just in case. 
- Use the installation disc to boot the live version of ubuntu.
- Run gparted and use it to resize the partitions as needed. This can take a while.

And that is it. Everything should be good to go. This method should work regardless of what operating systems you have installed.

It didn't work and there was a warning sign next to Vista paritition.

---

### Post by Richiegs on 2010-10-01
> **Quackers said:**
> Hmm, it did allow you to click on "shrink" but then said access denied? Were you logged in as an administrator?

Yes, it allowed me to click on "Shrink", but said access denied later. I am the only user for this laptop, so I guess I'm an administrator.

---

### Post by Richiegs on 2010-10-02
I was able to shrink the Windows Vista partition using Gparted. The problem is I have one allocated NTFS partition and I can't merge it with the Ubuntu partition using Gparted or Windows software. Please help! Thank you

---

### Post by Quackers on 2010-10-02
You would need to delete the NTFS partition then extend the Ubuntu partition into the resulting unallocated space. It is safer to run one job at a time, while no system is running. I use GParted Live cd and boot from it, then there are no system files in use.

Edit If you have shrunk the Windows partition you should have some unallocated space showing.

---

### Post by Richiegs on 2010-10-02
> **Quackers said:**
> You would need to delete the NTFS partition then extend the Ubuntu partition into the resulting unallocated space. It is safer to run one job at a time, while no system is running. I use GParted Live cd and boot from it, then there are no system files in use.
 
Quackers, there are two NTFS partitions in my hard disk. One contains Windows Vista and the other is an allocated NTFS partition. Did you mean to delete the allocated NTFS partition? Thanks

---

### Post by Quackers on 2010-10-02
Please see the edit to my previous post. Do you have any unallocated space showing on the disc?

---

### Post by Richiegs on 2010-10-02
Actually I can't delete the allocated NTFS partition! Do you mean I should delete the Windows NTFS partition?

---

### Post by Quackers on 2010-10-02
No.
Can you boot into Ubuntu and then post a screenshot of what Gparted shows please?

---

### Post by Richiegs on 2010-10-02
> **Quackers said:**
> Please see the edit to my previous post. Do you have any unallocated space showing on the disc?
 
Yes, there is an unallocated sNTFS pace showing in my harddisk. I can't do anything with this partition except do a New Simple Volume.

---

### Post by Quackers on 2010-10-02
If it's "unallocated" it can't be "NTFS" :-(

---

### Post by Richiegs on 2010-10-02
> **Quackers said:**
> If it's "unallocated" it can't be "NTFS" :-(
 
This unallocated space came from shrinking of NTFS partition. Can I merge the unallocated partition with Ubuntu partition?

---

### Post by Quackers on 2010-10-02
The unallocated space can be merged with the Ubuntu partition if it is physically next to it on the disc. You would do this by extending the Ubuntu partition. You should not do this while the system is loaded.

---

### Post by Richiegs on 2010-10-02
> **Quackers said:**
> The unallocated space can be merged with the Ubuntu partition if it is physically next to it on the disc. You would do this by extending the Ubuntu partition. You should not do this while the system is loaded.
  Yes, the unallocated partition is right next to the Ubuntu partition. Should I use the Ubuntu Installation Disk to merge them together?

---

### Post by Quackers on 2010-10-02
I haven't used the Ubuntu live cd for that purpose (I use GParted Live cd) but it can certainly be used for that. Be careful! :-)

---

### Post by Richiegs on 2010-10-02
> **Quackers said:**
> I haven't used the Ubuntu live cd for that purpose (I use GParted Live cd) but it can certainly be used for that. Be careful! :-)
 
Gparted Live CD? Do I have to download Gparted onto a CD?

---

### Post by Quackers on 2010-10-02
You can do. That's how I use it, but in these circumstances if you boot into the Ubuntu live cd (not your normal system) and then run Gparted from the menu you will be able to do what you want to.

---

### Post by Richiegs on 2010-10-02
> **Quackers said:**
> You can do. That's how I use it, but in these circumstances if you boot into the Ubuntu live cd (not your normal system) and then run Gparted from the menu you will be able to do what you want to.
 
Thanks, I will try again. I am just curious why I can't merge an unallocated partition with the Ubuntu partition in Windows.

---

### Post by Quackers on 2010-10-02
I don't know, but to be honest I wouldn't even try it! Using Windows to mess with Ubuntu files doesn't sound too appealing to me. :-(

---

### Post by luqmanawawi on 2010-11-10
Here is my situation. I have an unallocated space reside next to ubuntu partition. Instead of using live cd, may i use the Gparted on current ubuntu to extend the partition?

---

### Post by Tangbuntu on 2011-02-26
EDIT:  Did I mention that I'm a complete noob?  I'm sorry guys - I just realised what I was doing wrong.  Right-clicked on the light blue outline (rather than the dark blue ubuntu partition) and opened Resize/Move.  I could increase that section fine.  So sorry.  I will leave this embarrassing gaff up though, since it seems I'm not the only one.  I hope my noobness helps another noob out.  =)

> 
Help!  I can't increase the size of my Ubuntu partition either.

I have resized (shrunk) the Windows partition - no problem there.  I then unmounted the swap partitions, but the blue outline is still around ubuntu and swaps  I can't increase the size of the ubuntu partition (from within Resize/Move for that partition - is that the correct place?),  only decrease it (which is not what I want).  I've included a screenshot link of gparted - can someone please help?  What am I doing wrong?

[http://i828.photobucket.com/albums/zz205/WrongWriter/Screenshot.png?t=1298781150](http://i828.photobucket.com/albums/zz205/WrongWriter/Screenshot.png?t=1298781150)

PS - I am  running gparted from the ubuntu 9.10 live cd.  I have 9.10 on the hdd (but obviously aren't using it to partition the disk).  That partition's status is 'unmounted' in the information box.

PPS - I am using wireless internet, which didn't work (without madwifi) on the installed 9.10 but is now working.  Is running this, or firefox, what is preventing me from changing the partition?  It seems unlikely, but I'm trying to include as much info as possible.  Cheers!

PPSS - please give me as much detail as possible (including code and step-by-step instructions for terminal operations) as I am a complete ubuntu noob.  Thanks!

---

