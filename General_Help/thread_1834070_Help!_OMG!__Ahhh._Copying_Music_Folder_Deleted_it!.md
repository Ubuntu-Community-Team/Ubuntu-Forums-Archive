---
title: "Help! OMG!  Ahhh. Copying Music Folder Deleted it!!"
date: 2011-08-27
forum: General Help
---

### Post by RideTheSpiral on 2011-08-27
I switched my windows 7 lenovo y560 w/ 32GB SSD and 500GB HDD over to ubuntu. I copied my music folder to an ntsf file partition on an external hdd (120GB music) and resized partitions on my laptop (15gb ubuntu ssd / 200gb /home partition) 

Copied my music back to the hdd on my laptop and nothing happened! restarted and nothing appears! WTF WTF WTF!!!! WTF! NO!


Now I tried 'restoring' trash bin and nothing! on my 1.5tb (about 1TB before backup, 670GB after backup).. It still says that onlu 670GB is there WTF!

I know some of you smarty pants out there know how to fix this, I don't want to go any further before I **** this up! I have faith!! LOL =[

:guitar:

TLDR (GTFO..): Copied music backup off ntsf hdd and nothing seemed to happened, restart, and nothing appears on laptop, only empty folders on external hdd

---

### Post by artantaaa on 2011-08-27
Are you sure everything was successfully copied in the first place? I mean, were you able to play your songs from the external drive before you formatted your 500GB drive? I would first check to see if a windows machine can still see the music on your external drive. If not, I would look into using testdisk or some other data recovery program on your 500GB drive. Your files are most likely still there.

---

### Post by RideTheSpiral on 2011-08-27
I have a windows machine downstairs. I have not plugged the external hdd intothe downstairs computer. I also have windows 7 successfully running in a virtualbox machine within ubuntu. I'm able to give it 1 core of my i5 cpu and half my ram along with max 3d & 2d video card settings. 

Everything copied to the external hdd correctly, it took about 2hrs, where as when I tried copying back the the laptop, nothing showed up. I was able to play stuff from the external and still can play videos I have transferred. 

if it plays on the downstairs computer, are my only options listed using a recovery program as you have stated? If it does, the computer in question only has an 80GB HDD so what would I do to make the files accessable

Though I'm a newb I should be able to figure things out once I'm in the correct direction. I've had this problem before and forgot about it for the few years I have left linux aside.. this is not the first time

trying testdisk right now

---

### Post by artantaaa on 2011-08-27
I didn't read your first post carefully enough. I was imagining that you had installed Ubuntu on the whole 500GB drive and had about 495GB of free space. If you have already overwritten the spot on your 500GB drive where your music used to be, you won't be able to retrieve your files from it. If they were on your external drive at one point, you might be able to find them there with testdisk. If your music is readable on that other windows machine downstairs, then the issue is getting Ubuntu to read them. I have encountered problems like this in the past, and solved them by installing packages related to NTFS filesystem support. For quite a while now, Ubuntu has been reading NTFS by default without any trouble, but it might be worth thinking about. The first thing I would try is running testdisk on the external drive. Good luck.

---

### Post by RideTheSpiral on 2011-08-27
why not read the posts then.. alll wrong

32gb ssd = "/"

500gb was only 40gb to "/home"

resized to ~250gb for "/home"

transfered "MUSIC" from external

nothing seemed to copy... no longer visible on external OR laptop

externel does not show loss of original music files (only 45% free still_

---

### Post by nothingspecial on 2011-08-27
The question is

How did you "transfer the music"?

File browser, command line | which file browser, which command?

---

### Post by RideTheSpiral on 2011-08-27
I used nautilus. Control + a, control +c, right click paste in /home/user/music

---

### Post by saltmarshlamb on 2011-08-27
> externel does not show loss of original music files (only 45% free still_Just a thought here. If the drive still appears to show them perhaps they are in it's trash.

Open nautilus - navigate to the drive. Make sure hidden files are shown - Ctrl+H - have a look in the .Trash-xxx/files folder

EDIT - I would though be careful about what I did to the external, especially writing to it - makes getting hold of the files with testdisk if they are 'gone' less likely

---

### Post by RideTheSpiral on 2011-08-27
they were in the trash, I put an icon on my desktop and restored the files from there, but they just keep ending up back in the trash. checked hidden files and they show up in the trash folder on the external hdd as well

I won't write to the external hdd until this gets fixed, but I just don't have the time right now. It took long enough to get ubuntu configured perfect :(


accepting all other tips :lolflag:

---

