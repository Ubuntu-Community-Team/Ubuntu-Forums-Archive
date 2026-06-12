---
title: "New ubuntu user!"
date: 2012-01-23
forum: General Help
---

### Post by PadiSka on 2012-01-23
I think I have installed ubuntu on its own partition (I selected the option on the live cd "install ubuntu alongside windows"). But some program files from windows are on my ubuntu aswell. Wondering how this happened? The file I noticed on my new OS was a poker app and I have no idea how it got onto my ubuntu if windows and ubuntu are on different partitions. My question is does this mean that my two OS's are not on separate partitions or what does it mean? I really want them on seperate partitions so they dont effect one another!

Any1 have any idea? Thanks for any help that comes!

---

### Post by stefangr1 on 2012-01-23
Maybe they're not program files, but use some files that windows (and OSX as well, for that matter) put in each and every folder they come across. From windows, they're hidden, but then in Linux they're visible.

---

### Post by cortman on 2012-01-23
Sure you're not just looking at the Windows partition in Ubuntu?

---

### Post by brain7734 on 2012-01-23
The two OS are on separate partitions, but Ubuntu is able to see what files and programs are in Windows. Ubuntu knows there is another OS beside him, but Windows has no idea that Ubuntu is there. So you are able to see files that are in windows while using Ubuntu.

---

### Post by lolpenguin on 2012-01-23
Windows doesn't support EXT/EXT2/3/4 file systems, but Linux supports NTFS, so there you go.

---

### Post by nipunshakya on 2012-01-23
> **PadiSka said:**
> I think I have installed ubuntu on its own partition (I selected the option on the live cd "install ubuntu alongside windows"). But some program files from windows are on my ubuntu aswell. Wondering how this happened? The file I noticed on my new OS was a poker app and I have no idea how it got onto my ubuntu if windows and ubuntu are on different partitions. My question is does this mean that my two OS's are not on separate partitions or what does it mean? I really want them on seperate partitions so they dont effect one another!

Any1 have any idea? Thanks for any help that comes!

Doing a side by side installation means that your installation has been created on a new partition with / and swap area. So it is clear that your partitions are different.
Regarding your files being seen by ubuntu, well, ubuntu can view your NTFS partitions in which the windows was installed. And so, you can clearly see those files(but they are on different partition).
However, if you boot to windows you won't see ubuntu's partitions. thats coz windows cannot recognise ext2 or ext3 or ext4 filesystems(one of that filesystem was used by your ubuntu to get installed). Thats the main reason you don't see ubuntu's files roaming around in windows.

To make yourself clear, select My Computer, right click it, select Manage. A window will load, and on bottom left, you can see Disk Management. Click that and u will be presented with the partition scheme of your computer. Though windows can't recognise ubuntu, it will however show u the partitions under what ur ubuntu is installed. But don't mess around here. Its just for your information purpose. Goodluck

Regards,WinuxUser

---

### Post by PadiSka on 2012-01-24
I think you guys are totally right that I am just looking at windows files files through ubuntu! They are the files that u would see if you clicked into your C drive in my computer on windows! Im seeing them on ubuntu when I click into the home folder and then into the picture of a hard disk! Does this sound right to see all windows files here?


Also if I can see windows files on ubuntu, does this mean that it is possible to delete windows files on ubuntu? Or even use windows files on ubuntu? Or if one of these files got a virus on windows would it therefore travel to my ubuntu OS?


Sorry for all the questions im just new to ubuntu!ha.
Looks good tho!

Thanks for all the help guys!

---

### Post by cortman on 2012-01-24
> **PadiSka said:**
> 
Also if I can see windows files on ubuntu, does this mean that it is possible to delete windows files on ubuntu? Or even use windows files on ubuntu? Or if one of these files got a virus on windows would it therefore travel to my ubuntu OS?

a) Yes- BUT don't, unless you really have to- Windows is finicky about other OS's messing with its partitions.
b) Not sure what you mean by "use"- play music? Read documents? Look at pictures? Absolutely. Run programs? Nope.
c) Windows viruses don't affect Linux in the least, so even if you had a virus on Windows, it wouldn't do anything to Ubuntu.

Have fun with Ubuntu!

---

### Post by nipunshakya on 2012-01-25
> **PadiSka said:**
> I think you guys are totally right that I am just looking at windows files files through ubuntu! They are the files that u would see if you clicked into your C drive in my computer on windows! Im seeing them on ubuntu when I click into the home folder and then into the picture of a hard disk! Does this sound right to see all windows files here?


Also if I can see windows files on ubuntu, does this mean that it is possible to delete windows files on ubuntu? Or even use windows files on ubuntu? Or if one of these files got a virus on windows would it therefore travel to my ubuntu OS?


Sorry for all the questions im just new to ubuntu!ha.
Looks good tho!

Thanks for all the help guys!

Mate, there is nothing suspicious of you seeing the windows files on your ubuntu because unlike windows that doesn't read ubuntu's filesystem, ubuntu can perfectly mount windows partitions. So there is nothing to worry about you seeing those files.
Yes you surely can delete files those windows files. However, you must always know what you are deleting. Windows wouldn't like it at all if you mess up with its files and that might cause u a problem later on.

You can pretty much share pictures, music stuffs and videos among the windows and linux from the windows partitions, thats the advantage of having windows partitions in dual-boot thing...

However, there is no possibility that a windows virus will affect your ubuntu filesystem. Pretty much i guess everyone will agree that ubuntu doesn't need an antivirus...:)

This is where u clear out your confusions...feel free to ask anything...but about ubuntu offcourse...

Happy Linuxing.
Regards,WinuxUser

---

### Post by PadiSka on 2012-01-27
Cool so can I get all my music off windows onto my ubuntu OS! Would I have to move my music files to the My computer/ Program Files directory of windows before I move or can I get them straight out of My Documents?

Tanx again guys this has been very helpful!

---

### Post by nipunshakya on 2012-01-27
Just imagine linux using windows' filesystem as its own...just mount the c: by clicking it and then you are ready to use it as you want....

Note: in order to use a particular file from windows' filesystem, just make sure you have mounted that current filesystem, e.g. if u want a document to be accessed from My Documents, make sure you mount c:

Goodluck and Happy Linuxing

Regards,WinuxUser

---

### Post by cortman on 2012-01-27
> **PadiSka said:**
> Cool so can I get all my music off windows onto my ubuntu OS! Would I have to move my music files to the My computer/ Program Files directory of windows before I move or can I get them straight out of My Documents?

Tanx again guys this has been very helpful!

You can get them out of My Documents, but of course you'd be navigating to Documents and Settings\username\My Documents.

---

### Post by cryptotheslow on 2012-01-27
If you intend to continue dual-booting between Windows and Ubuntu while sharing media (music/vids) or docs between the two - I recommend creating a further partition for that purpose where you store the files to be used by both - ntfs format.

That way - whatever either OS does there should not effect the integrity of the other OS. 

Having your entire Windows partition mounted while in Ubuntu is mostly safe but accidents do happen - Ubuntu won't ask twice (or even once) if you ask it to delete all files in your Windows partition - it just sees it as A N Other directory and will happily do what you ask.

Just a precautionary post so your next thread is not "Shift-Delete On /media/Win - Now Windows won't boot :( "

Take Care and Have Fun :D

---

