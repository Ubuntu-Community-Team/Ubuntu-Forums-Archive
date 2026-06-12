---
title: "How to recover lost data"
date: 2012-04-13
forum: General Help
---

### Post by L.E.n on 2012-04-13
Hi.
Today, I have accidentally reinstalled Ubuntu (I had the latest version, though I couldn't boot to Windows and I didn't want to reinstall them), despite the fact I don't have any backup at all. I had so many files on that partition... over 2 years of work, pictures, memories, etc... and I would really like to get them back. Is there any way how to recover these files? 
I have formatted the partition, still - any way how to recover it?

If you know about any software I could use for this, it would be better if it had GUI since I'm not a big fan of typing the commands.
Thanks for your help!

---

### Post by The Cog on 2012-04-13
Don't boot that Ubuntu again - every time you use it, you will be overwriting more of your old data.

There is a program called photorec that will scan a hard disk or partition, and save any files it finds to another drive. I think this is available in a system rescue CD that you can download and burn using a different computer. 

I guess you will need to out an external hard drive on your broken computer (to save the files to), and boot the rescue CD to run photorec. You will need to google for the CD download and the instructions how to use.

Photorec will find lots of files, many intact, some corrupt, and names them with sequential numbers - no clue which directory they were in. Expect to find an awful lot of thumbnails and small images from your browser cache - you have a lot of sorting out to do, I'm afraid.

Good luck.

---

### Post by lolpenguin on 2012-04-13
You can't really do it, especially since you formatted the drive.
It is possible, but you will require police forensics and/or the skills of forensics scientists tools to get something back, and it won't be much.

Just to let you know, when you delete in most file systems, the data is not actually deleted; the sectors are marked as 'free' to let the kernel know that the data can be overwritten. When you create new files, then it is deleted and will be pretty much gone. If you ever 'permanently' delete something, (as The Cog said) stop using your computer and plug the hard drive into another computer or boot into a different OS on a different drive, then use a file recovery tool to get your stuff back.
(This also causes problems with disk fragmentation, you might delete some small file less than 100MiB, for example, then download a 600MiB disc image. The system will attempt to write to the first free sector, but since it is not big enough, the rest will be written to the next empty sector and so on.)

Good luck on it though.

---

### Post by eric_1982 on 2012-04-13
I came across this article a week or two ago that may help you out. 

[http://sajeelirkal.wordpress.com/2012/03/15/recover-deleted-files-in-linux/](http://sajeelirkal.wordpress.com/2012/03/15/recover-deleted-files-in-linux/)

---

### Post by callmemahavir on 2012-04-14
You may try Ultimate Boot CD...

Download it from 

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Boot from this disc and rescue the system.

It may help great.

---

### Post by L.E.n on 2012-04-15
Thanks guys.
I've used PhotoRec and it actually recovered loads of files though there is nothing originally named, and I got here around 2000+ folders named "recup_dir*NUMBER*" and I kind of don't know where to start.

Gotta get to the former /home/ directory where I had my data stored.

---

### Post by dragonfly41 on 2012-04-15
Problem with PhotoRec is that you lose the file structure and names as you have found.
So with PhotoRec you have to deduce what the contents are.
Other recovery utilities (usually not free) can recover original file names.


I suggested use of TEXTstat in this thread ..
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

TextSTAT analyses the corpus of hundreds of files with random names.

After installing TEXTstat create a corpus of your PhotoRec recovered files.

Then apply word frequency list from corpus.
Then search for key words in word frequency list to narrow down your search.
You can inspect the concordance of files so you might be able to find clues to the contents.

...

Another approach you might try is to write a bash script to scan through your recovered files and inspect metafiles.

...

You appear to be on Windows so I would consider the option lolpenguin wrote above ..

physically removing your hard drive
place it in a USB drive container
go to another windows PC and attach the USB drive (to be recovered) .. your working PC will have to have enough space to take any recovered files since you can't copy recovered files into the same USB drive you're trying to recover.

download Recover My Files from here .. [http://www.recovermyfiles.com/](http://www.recovermyfiles.com/)

do a trial run (which only analyses the external USB drive to first test if files can be recovered before buying)

If they _can_ be recovered you will need to consider purchasing a licence for RecoverMyFiles.

There are other similar recovery utilities which you can try out.

---

### Post by L.E.n on 2012-04-15
No, I am using Ubuntu since I formatted the drive and I have a laptop, so it's not physically possible to remove a hard-drive.

I have recovered the files using PhotoRec though and tried searching all the folders by Nautilus looking for .mp3 files. To my surprise, I found out that all of the files have been recovered to completely different folders, and even though file A was formerly in the same folder as file B, now they are separate. 
It will take me ages to get through that.

Unfortunately, I don't think I can work with that software, dragonfly.

---

### Post by blackangelpr on 2012-04-15
> **L.E.n said:**
> Hi.
Today, I have accidentally reinstalled Ubuntu (I had the latest version, though I couldn't boot to Windows and I didn't want to reinstall them), despite the fact I don't have any backup at all. I had so many files on that partition... over 2 years of work, pictures, memories, etc... and I would really like to get them back. Is there any way how to recover these files? 
I have formatted the partition, still - any way how to recover it?

If you know about any software I could use for this, it would be better if it had GUI since I'm not a big fan of typing the commands.
Thanks for your help!

when you fix it do not forget to u se your ubuntu one  so you can save at least your documents on the cloud  you have 5gs for free ):P

---

