---
title: "Urgent: Help needed.  Ubuntu can no longer read files burned while using Ubuntu!"
date: 2010-11-30
forum: General Help
---

### Post by Emporata on 2010-11-30
I burned these very important data files on the large DVD discs and now Ubuntu can no longer see them.  It can only see the file folders but the files are still there.  I took a bad screenshot with a camera but you can still see that the files are still there.  Please help!

---

### Post by bobcollard on 2010-11-30
> **Emporata said:**
> I burned these very important data files on the large DVD discs and now Ubuntu can no longer see them.  It can only see the file folders but the files are still there.  I took a bad screenshot with a camera but you can still see that the files are still there.  Please help!
Silly question, but, did you try to open the folders by double clicking or right clicking, perhaps using a file manager?

---

### Post by Emporata on 2010-11-30
Yes I have done that but to no avail.

---

### Post by pricetech on 2010-11-30
How can you be sure the files are there if you can't see them ??

Have you tried looking for the files in a terminal ??  If you can see them that way, then copy them somewhere like your home folder.

---

### Post by Emporata on 2010-11-30
> **pricetech said:**
> How can you be sure the files are there if you can't see them ??

Have you tried looking for the files in a terminal ??  If you can see them that way, then copy them somewhere like your home folder.

Im sorry but I don't know how.  The computer that had ubuntu on it has since died.  That was the computer I wrote about a few days ago with the "disturbing error message."  At any rate, I copied these files using my external DVD writer before it died, once before I new it was even sick.  

If you would, please, give me the instructions for looking at the files in the terminal, I would really appreciate it.  

Thanks.

I am now using a computer with Puppy Linux installed on it but I think the language for the terminal should be the same.  Also, I have one computer with Windows on it  Windows cannot see the files.

---

### Post by bobcollard on 2010-11-30
> **Emporata said:**
> Yes I have done that but to no avail.
Does the DVD show up in the left panel of your File Manager?  Like this?:

---

### Post by Emporata on 2010-11-30
> **bobcollard said:**
> Does the DVD show up in the left panel of your File Manager?  Like this?:


Yes I can see the DVD itself and the file folders but not the contents of the files themselves.

---

### Post by Emporata on 2010-11-30
> **pricetech said:**
> How can you be sure the files are there if you can't see them ??
.

I looked in the "properties" just before the Ubuntu computer died and it said there were a bunch of items on the burned disk.  You can sort of see the "properties" in the horrible picture I took with my digital camera.

---

### Post by bobcollard on 2010-11-30
Right click on one of the file folders and check Properties to see how much is inside of it, should be in the MB or GB range.  If not then you just have the folders and not the contents.  If so, then open one of the folders and go to View>Show Hidden Files in the top menu bar to see if they are hidden.

---

### Post by Emporata on 2010-11-30
> **bobcollard said:**
> Right click on one of the file folders and check Properties to see how much is inside of it, should be in the MB or GB range.  If not then you just have the folders and not the contents.  If so, then open one of the folders and go to View>Show Hidden Files in the top menu bar to see if they are hidden.

It said 173 items (which cant be all empty file folders) totaling 348 kb.  I have tried many times to get them unhidden with both Windows and Linux Puppy (as ubuntu comptuer is now dead) but to no avail.

---

### Post by bobcollard on 2010-11-30
> **Emporata said:**
> It said 173 items (which cant be all empty file folders) totaling 348 mb.  I have tried many times to get them unhidden with both Windows and Linux Puppy (as ubuntu comptuer is now dead) but to no avail.
If you have the Live Ubuntu disk you can use that.  It does not have to be installed on the computer.  Then back up the disk if you need to or copy it, whatever it is you are trying to do with the info.  Just copy the info onto your HD first.

---

### Post by Emporata on 2010-11-30
> **bobcollard said:**
> Right click on one of the file folders and check Properties to see how much is inside of it, should be in the MB or GB range.  If not then you just have the folders and not the contents.  If so, then open one of the folders and go to View>Show Hidden Files in the top menu bar to see if they are hidden.

Okay I think I am in big trouble if what you say is right.  It is 173 items and 348 KB not MB!!  OMG!  This is six months of work gone!  I burned this to TWO DIFFERENT DISKS!  Both are behaving in the same way!  How can there be so many file folders but no documents??

---

### Post by bobcollard on 2010-11-30
> **Emporata said:**
> Okay I think I am in big trouble if what you say is right.  It is 173 items and 348 KB not MB!!  OMG!  This is six months of work gone!  I burned this to TWO DIFFERENT DISKS!  Both are behaving in the same way!  How can there be so many file folders but no documents??
Unfortunately you have learned a valuable lesson the hard way.  Always check your backups before you leave your computer.  Me?  I have two 250GB external drives and backup to each of them daily and I don't work in an office or have anything of Real value.  My computer has one 160GB drive and I don't trust any of them.  If you did not overwrite the former drive with the ubuntu system on it, you may have a professional recover the data.  I am sorry, it cannot be stated enough _***Backup!***_

---

### Post by Wobblybob on 2010-11-30
so the dvd's are duff and you say the PC the original files where on is now dead but is the hard drive still ok, if you can mount it on another PC you may still be able to get your files back.

---

### Post by ezsit on 2010-11-30
Did you happen to use Brasero to burn the data DVDs? I have had zero success getting Brasero to burn data DVDs in Ubuntu 10.10. All I got were corrupted DVDs where I could not access the files. I have since switched to GnomeBaker and have no problems with data DVD burning there.

I know this doesn't help you, but I would not trust Brasero.

Even if your hard drive doesn't boot up, you may still be able to access the files by connecting the hard drive to another computer with a SATA/PATA to USB converter. I hope you did not install anything new to the old hard drive? If you formatted and used the old hard drive again, its probably way too late for recovery.

---

### Post by pricetech on 2010-11-30
Try the drive in another computer.  If you have to, install it as the only hard drive and boot to live CD to see if you can see it.  If so, you should be able to access the files you need and back them up somewhere else.

---

### Post by Emporata on 2010-11-30
> **ezsit said:**
> Did you happen to use Brasero to burn the data DVDs? I have had zero success getting Brasero to burn data DVDs in Ubuntu 10.10. All I got were corrupted DVDs where I could not access the files. I have since switched to GnomeBaker and have no problems with data DVD burning there.

I know this doesn't help you, but I would not trust Brasero.

Even if your hard drive doesn't boot up, you may still be able to access the files by connecting the hard drive to another computer with a SATA/PATA to USB converter. I hope you did not install anything new to the old hard drive? If you formatted and used the old hard drive again, its probably way too late for recovery.

Yes it is too late for recovery there and yes I used Brasero.

---

### Post by Emporata on 2010-11-30
> **bobcollard said:**
> Unfortunately you have learned a valuable lesson the hard way.  Always check your backups before you leave your computer.  Me?  I have two 250GB external drives and backup to each of them daily and I don't work in an office or have anything of Real value.  My computer has one 160GB drive and I don't trust any of them.  If you did not overwrite the former drive with the ubuntu system on it, you may have a professional recover the data.  I am sorry, it cannot be stated enough _***Backup!***_

I did click through to look at the files and it looked as if they were there.  I thought I had backed up since I did burn this data to two separate disks.

---

### Post by bobcollard on 2010-11-30
> **Emporata said:**
> I did click through to look at the files and it looked as if they were there.  I thought I had backed up since I did burn this data to two separate disks.
I apologize if it looks like I'm saying you did something wrong, I am not there and only know what you told me, that you burned a disk in Ubuntu and tried to read it with Ubuntu.  Now that computer is down?  Anyway, I hope you can get something from the Ubuntu computer disk.

---

