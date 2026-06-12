---
title: "Lost 22GB of files in a fraction of a second"
date: 2011-10-13
forum: General Help
---

### Post by ve2ebp on 2011-10-13
Hello,

Tonight, I erased everything that was in my documents 22GB worth of stuff. I had previously copied all my files in the Dropbox folder and as I didn't want to keep any duplicates, I clicked on the link that referred to the documents folder! So I deleted my documents folder, not what I thought was the copy of documents in dropbox. :(

The folders were in there but whenever I clicked to open any of them, they were empty in the trash can. A guy on the chat told me to shut down my system which I did.

Later on, I was told that I should I kept my system up and running by doing a ls -a ./ or something like that but it's too late now. My system is off :(

I have dual boot. I have windows XP on a different partition. 
I guess if I could find a Windows software that could read ext3 or ext4 partitions (I was using Kubuntu 10.04 I believe), I guess that would be the best way to go about it?

My system will not boot up on a USB key! Just CD.

I don't know much about these things but one would think that if I run the recovery software from XP, it would minimize the linux partition to be tampered with?

I also read about UbuntuRescueRemix1104.iso or testdisk...

Which do you think would be my best bet?

Thanks you all in advance,


Pete.

---

### Post by ve2ebp on 2011-10-13
I checked it from WinXP. The FS is ext4 and it looks like the kubuntu is on the same physical hard drive as my XP OS at 90% chance. I also have another ext4 partition on sdb but there is no swap partition on sdb so I figured sda is the right partition. More to come.

---

### Post by ve2ebp on 2011-10-13
Would it be safe to create image of those two drives using Norton Ghost 10 (from the WinXP side) so that when I attempt to recover the files, if something goes wrong, I will be able at least to restore the .ng files. I guess it cannot hurt, right?

---

### Post by WasMeHere on 2011-10-13
Hi ve2ebp,

It is not convenient, but it is possible to recover erased files as long as 'only' the address is deleted and the data is still sitting on the hard drive. Search in the Ubuntu Forums for similar threads, and browse the internet to find out what can be done and which tools are available!

Do you still have copies of your files in the dropbox folder, or any other backup? If not you have to be very careful so that nothing will be written to your disk because it might overwrite your file data, that you want to retrieve.

I suggest that you use a rescue live system. There are many of them, browse the internet and select one. Make a boot CD, boot from it and do the work. But first, **read the relevant tutorials** that you can find on the internet! **Photorec** might be the tool for you.

Good luck :-)
Olle

---

### Post by WasMeHere on 2011-10-13
> **ve2ebp said:**
> Would it be safe to create image of those two drives using Norton Ghost 10 (from the WinXP side) so that when I attempt to recover the files, if something goes wrong, I will be able at least to restore the .ng files. I guess it cannot hurt, right?
Yes an image is a good idea, or if you have a whole spare disk, a cloned copy.

---

### Post by carranty on 2011-10-13
Hi there,

I'm having trouble understanding exactly what's happened. Am I right in thinking you have deleted the ' my documents' folder from your windows partition whilst booted into kubuntu? If do how did you delete it, did you right click on the folder and choose delete, or did you use the rm command? if you didn't use rm, have a look on your windows partition for a folder called .Trash , the my documents folder might be in there. 22Gb is large though, so it may not have been sent to trash, but removed entirely.

Whether you rebooted or not probably didn't matter.

I don't follow why you need a windows program that reads ext3. However you deleted it, it was on you windows partition, which won't be ext3.

---

### Post by ve2ebp on 2011-10-13
Thanks for your replies!
Just found out that Norton Ghost won't image ext4. So I will try to take a snapshot using acronis this time. 

How did it happen? Well, I'm mostly a Win user for the time being. But I like Ubuntu a lot. Learning curve is harder at 46!

Anyway what happened is that under Windoze, the dropbox folder is actually a folder (separate folder). In the Dolphin integration, I found out too late that the dropbox is just a link that points to the documents folder.

So when I had made sure that all my documents had been copied to the dropbox folder (so I thought, it was just a link pointing back to the original documents folder), I wanted to delete the originals because now I thought I had everything in dropbox. 

Often times, I keep too many files and at the end, I forget what is what.. That makes backups of backups of backups that pile up....

So that's what happened! I should have noticed the little arrow that told me this was a link, not an actual folder. I thought it was weird but didn't get to think much of it.

When I went back to my dropbox (what I thought was a folder), found out at my dismay that everything was there too! Few minutes later, I realized my mistake.

Out of 22 GB, only 1/2 GB survived in Dropbox.

Very frustrating. These things always seem to happen at night. This experience has shaken my world. I had a lot of important files in there.

Yesterday I tried to copy to an external hard drive, of course it didn't work... So from worse to worse... Seems to be how it works.

---

### Post by ve2ebp on 2011-10-13
No Carranty. I deleted my folder from Kubuntu. It's just that I happen to have my Kubuntu system running in a dual band combination along with a WinXP system running both on sda

---

### Post by ve2ebp on 2011-10-13
Well, though I knew all this, in the panick mode, I started fooling around in the trash bin trying to get them back... and unfortunately permanently deleting stuff int here that I thought was not important. Then I invoked xchat. The guys reminded me to shut down which i did. I didn't even shut down, I dropped the power to the box, period. I hope it's not worse?

Anyway... Pretty sad. 
I should have had a backup system installed on there.

> **Olle Wiklund said:**
> Hi ve2ebp,

It is not convenient, but it is possible to recover erased files as long as 'only' the address is deleted and the data is still sitting on the hard drive. Search in the Ubuntu Forums for similar threads, and browse the internet to find out what can be done and which tools are available!

Do you still have copies of your files in the dropbox folder, or any other backup? If not you have to be very careful so that nothing will be written to your disk because it might overwrite your file data, that you want to retrieve.

I suggest that you use a rescue live system. There are many of them, browse the internet and select one. Make a boot CD, boot from it and do the work. But first, **read the relevant tutorials** that you can find on the internet! **Photorec** might be the tool for you.

Good luck :-)
Olle

---

### Post by javierrivera on 2011-10-13
You should be able to undelete everything from the Dropbox web interface.

After that they will be synced back to every system that is linked to your account.

---

### Post by WasMeHere on 2011-10-13
> **Olle Wiklund said:**
> 

... Search in the Ubuntu Forums for similar threads, and browse the internet to find out what can be done and which tools are available!

... Be very careful so that nothing will be written to your disk because it might overwrite your file data, that you want to retrieve.

I suggest that you use a rescue live system. There are many of them, browse the internet and select one. Make a boot CD, boot from it and do the work. But first, **read the relevant tutorials** that you can find on the internet! **Photorec** might be the tool for you.

Good luck :-)
Olle

Well, there are tools for this situation. The directory structure will be lost, but the content of the files can be saved.

Cheer up and try to enjoy learning what is possible with computers ;-)
Olle

---

### Post by ve2ebp on 2011-10-13
No, I think I'm pretty much toast! Photorec won't support ext4!

---

### Post by ve2ebp on 2011-10-13
> **javierrivera said:**
> You should be able to undelete everything from the Dropbox web interface.

After that they will be synced back to every system that is linked to your account.

Yeah but not everything had synced with Dropbox unfortunately...

---

### Post by ve2ebp on 2011-10-13
> **jasonjason said:**
> One attempt that can be tried out is placing a replica image of the files and than by various recovering available one can recover the file.

Jason, what do you mean by that?

---

### Post by ve2ebp on 2011-10-13
> **Olle Wiklund said:**
> Well, there are tools for this situation. The directory structure will be lost, but the content of the files can be saved.

Cheer up and try to enjoy learning what is possible with computers ;-)
Olle

Yeah I'm really starting to get pissed off at them... Not what I used to be with computers when I was younger.

---

### Post by Kai Summers on 2011-10-13
To restore a lost partition try TestDisk available in the Ubuntu Software Centre or -

```
sudo apt-get install testdisk
```

It should also install a program called PhotoRec...

PhotoRec is file data recovery software designed to recover lost pictures from digital camera memory or even Hard Disks.

It has been extended to search also for non audio/video headers.

It searchs for following files and is able to undelete them :

[LIST]
[*]Sun/NeXT audio data (.au)

[*]RIFF audio/video (.avi/.wav)

[*]BMP bitmap (.bmp)

[*]bzip2 compressed data (.bz2)

[*]Source code written in C (.c)

[*]Canon Raw picture (.crw)

[*]Canon catalog (.ctg)

[*]FAT subdirectory

[*]Microsoft Office Document (.doc)

[*]Nikon dsc (.dsc)

[*]HTML page (.html)

[*]JPEG picture (.jpg)

[*]MOV video (.mov)

[*]MP3 audio (MPEG ADTS, layer III, v1) (.mp3)

[*]Moving Picture Experts Group video (.mpg)

[*]Minolta Raw picture (.mrw)

[*]Olympus Raw Format picture (.orf)

[*]Portable Document Format (.pdf)

[*]Perl script (.pl)

[*]Portable Network Graphics (.png)

[*]Raw Fujifilm picture (.raf)

[*]Contax picture (.raw)

[*]Rollei picture (.rdc)

[*]Rich Text Format (.rtf)

[*]Shell script (.sh)

[*]Tar archive (.tar )

[*]Tag Image File Format (.tiff)

[*]Microsoft ASF (.wma)

[*]Sigma/Foveon X3 raw picture (.x3f)

[*]zip archive (.zip)
[/LIST]

---

### Post by WasMeHere on 2011-10-13
> **ve2ebp said:**
> No, I think I'm pretty much toast! Photorec won't support ext4!

I think Photorec can retrieve information from a hard disk or flash card or usb stick where the file system is destroyed. In such a case there might be a problem (with ext4?), if the file data is not sitting in a continuous string (fragmented file), but I think many files should be possible to recover.

One possibility that I have heard of is to make an uncompressed image of the partition with your files. You can make such an image with **dd** or with **Clonezilla** (in both cases from a live disk).

This image is a file, and Photorec can find file headers and extract the content in a systematic way.

---

### Post by ve2ebp on 2011-10-13
Problem is I was told to shut down my computer ASAP so I pulled the plug. So I guess what I need to do is to find another hard drive, install linux on it and then install testdisk on that right? 

This was the last time I will ever deal with ext4. I came across a lot of articles that says that it should have never been put out in production. Next time, it will be ext4.

[http://www.linuxinsight.com/how-to-recover-deleted-data-from-ext4-file-system-volume.html](http://www.linuxinsight.com/how-to-recover-deleted-data-from-ext4-file-system-volume.html)

---

### Post by ve2ebp on 2011-10-13
> **Olle Wiklund said:**
> I think Photorec can retrieve information from a hard disk or flash card or usb stick where the file system is destroyed. In such a case there might be a problem (with ext4?), if the file data is not sitting in a continuous string (fragmented file), but I think many files should be possible to recover.

One possibility that I have heard of is to make an uncompressed image of the partition with your files. You can make such an image with **dd** or with **Clonezilla** (in both cases from a live disk).

This image is a file, and Photorec can find file headers and extract the content in a systematic way.

Yeah but I don't think photorec will deal with ext4 though..

---

### Post by ve2ebp on 2011-10-13
I'm currently taking a snapshot of the two partitions using acronis right now. I hope it won't mess them up furthermore.

---

### Post by ve2ebp on 2011-10-13
> **Olle Wiklund said:**
> I think Photorec can retrieve information from a hard disk or flash card or usb stick where the file system is destroyed. In such a case there might be a problem (with ext4?), if the file data is not sitting in a continuous string (fragmented file), but I think many files should be possible to recover.

One possibility that I have heard of is to make an uncompressed image of the partition with your files. You can make such an image with **dd** or with **Clonezilla** (in both cases from a live disk).

This image is a file, and Photorec can find file headers and extract the content in a systematic way.

Yes I just read about that too. Next time maybe!

---

### Post by carranty on 2011-10-13
> **ve2ebp said:**
> Problem is I was told to shut down my computer ASAP so I pulled the plug. So I guess what I need to do is to find another hard drive, install linux on it and then install testdisk on that right? 


There's nothing wrong with the ext4 filesystem in my experience.  If you disconnect your computer directly from the mains while its running you can hardly blame the filesystem if you bugger up your hard disk!

If you haven't ruined your hard disk, and you can still boot into linux, just do as  Kai Summers suggested and use Photorec, it does support ext4, I promise you.

To be honest with you I think you're panicking, recovering files is not as difficult as this thread is making it out.  Just take a time out, and come back to it with a fresh mind in a few hours. Photorec should work, if it doesn't it may be that your hard drive is trashed (because of the way you turned it off), in which case recovering files may not be possible, but this is unlikely - hard disks these days are usually built well enough to withstand a power cut or two.

---

### Post by carranty on 2011-10-13
Also, reread [javierrivera]("http://ubuntuforums.org/member.php?u=689025")'spost.

The dropbox folder is not full of links.  Your files are copied to it whole, there would be no point in using dropbox if all it uploaded was links.  

Go to their website and login, you will be able to recover any files from that interface. Click on 'Show deleted files', then any files and folders that have recently been deleted will be ghosted out.  Just right click on them and then click restore.  I'm not sure how long it keeps deleted files for, but I would think 24 hours at least.

---

### Post by WasMeHere on 2011-10-13
> **carranty said:**
> ...
To be honest with you I think you're panicking, recovering files is not as difficult as this thread is making it out.  Just take a time out, and come back to it with a fresh mind in a few hours. Photorec should work,...
+1
Please take it easy now! Then read carefully all the advice in this thread. Your files may be in a trash-can at Dropbox. In that case everything is OK. Do what *carranty* writes:
> Go to their website and login, you will be able to recover any files from that interface. Click on 'Show deleted files', then any files and folders that have recently been deleted will be ghosted out. Just right click on them and then click restore. I'm not sure how long it keeps deleted files for, but I would think 24 hours at least. 
And what is not found that way can be recovered by ***Photorec***.

Good luck
Olle

---

