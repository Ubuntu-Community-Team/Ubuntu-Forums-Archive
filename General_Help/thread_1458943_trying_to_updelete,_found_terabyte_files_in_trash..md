---
title: "trying to updelete, found terabyte files in trash?.."
date: 2010-04-20
forum: General Help
---

### Post by JohnnyC35 on 2010-04-20
[FONT=Verdana][SIZE=2]hey, being not to bright I cancelled a partition resize accidently and the restarted it and it went on it's merry way. after it had resize my 500G partition into a 100 and 400 I noticed that most of my files were gone. I have my Documents folder, but my Music, Kids TV shows, wallpapers, and Pictures are gone. I starting going thru [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) to try an fix this as well as trolling the forums. At the moment I have 1 program going thru the drive's image, and another going thru the actual drive. While still waiting for this I looked in the trash. lots of files, I attempted to copy them out. Apparently on my 500G drive I have 14Tb of files.
After sudoing Trash I was able to get in and I see that there are some odd sized files. The largest of them are:
File name   file size
#6463091    2.7Tb
#14114451  2.5Tb
#6461878    2.1Tb

And these are about the size of I had on there, the largest being more or less what I had before I moved off some data:
File name   file size
#6461059     544G
#6462620     52G
#14106973    7.9G
#3467474     3.9G

Also using ddrescue I made and imagine file, sadly I can't mount it as an iso. when I try to mount it following the datarecovery guide it says no file system found.[FONT=monospace] I have e2fsck going thru it atm. if anyone can give me any sot of guidance as to what to do going forward that would be great. Thanks :)
[/FONT][/SIZE][/FONT]

---

### Post by JohnnyC35 on 2010-04-20
running 'recover' right now. On a positive note, with my horrible filing system I found a backup of all my family pictures. I have an off-site backup (my mothers :) ) but I'd hate to think I wouldn't be able to recover them off the computer just in case.

---

### Post by JohnnyC35 on 2010-04-20
using ddrescue to image my hard drive and then e2fsck it and mount it was a wash. after mounting the drive  (sudo mount -t ext2 -o loop image.img /mnt) it just gave me what was on the drive before, Documents and Lost+Found (with terabytes of data ???). also recovery didn't seem to do anything. recovery gave me a bunch of dump+random number, filenames that I don't know what to do with., foremost has gotten me my pictures back. with random numbered file names. I already found a back up of my family photo's, so at least i now have my wallpapers back (I know it's silly but still). 
now trying out magicrescue
still trying to recover Kids TV shows and music. we shall see :)

---

### Post by JohnnyC35 on 2010-04-20
well I now have about 30 thousand randomly numbered pictures to go thru. no joy otherwise. trying gparted

---

