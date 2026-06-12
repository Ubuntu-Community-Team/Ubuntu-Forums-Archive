---
title: "Restore files from windows XP partition deleted from Ubuntu"
date: 2011-04-28
forum: General Help
---

### Post by Margaret Dumont on 2011-04-28
Hello to everyone,

I am using dual boot of Windows XP (with a NTFS partition) and Ubuntu 9.10 (Karmic Koala) in my laptop.

This  morning I mistakenly deleted from Ubuntu a folder located in the  Windows partition which contained important files from my work. I  thought I would be able to restore those files from Ubuntu's trash but  there was no trace of them. I have a partial backup but much of the  latest work is lost.

I didn't reboot because I'm afraid it may be  more difficult to recover the files if I do and I haven't "Emptied the  trash" in Ubuntu just in case the files are there somehow.

I  installed Testdisk and made it work but the files that the program finds  in the Windows partition don't look like the ones I deleted. It's hard  to tell because most of the files that I've recovered don't even have an  extension and mines did, but I don't know if it's possible that they  might have been renamed in the process. My impression is that they are  just temporary files from a web browser or something of the sort.

I've been desperately trying to recover my files the whole day and just now I've found this thread:
[http://ubuntuforums.org/archive/index.php/t-637576.html](http://ubuntuforums.org/archive/index.php/t-637576.html)

The  problem is that in my case I don't find any ".trash" folder in the root  directory as it suggests in the thread. I tried changing the option in  Nautilus so it would show hidden files and also by "ls -a" in a terminal  window with no luck.

Since the thread is from 2007 I thought  that maybe Ubuntu is wiser now so I also tried checking if they are in  the "RECYCLER" folder of the Windows partition but the newest files are  from last month so it doesn't look either like they are there.

Does  anybody know what does Ubuntu do exactly when you delete a file from a  Windows partition? I find it hard to believe that it really shreds the  files, they should be there somehow!

If possible I would like to  solve this without rebooting. Is there any other program that works  better that Testdisk and has more chances to find my files in the  Windows partition?Should I look with Testdisk in the Ubuntu partition? I  don't think that Ubuntu moved the files and then permanently delete  them but I ran out of ideas.

I would be very grateful if someone  could give me any ideas on how to solve it or tell me how Ubuntu  proceeds in these cases. Otherwise, I might have lost months of some of  the work.  :-(

---

### Post by mdurham on 2011-04-28
The **first** thing I would do would be to make an image copy of the partition of where the files were.

---

### Post by dragonfly41 on 2011-04-28
I'm no expert in data recovery but I have gone through what you are experiencing .. but in Windows and not in ubuntu.

I've read that from a forensic perspective once you delete files in linux they're gone .. but I might be wrong.

One problem is you don't want to shut down your PC in fear of losing your data.

Perhaps  as a matter of priority you should clone the entire disk drive onto an external USB drive which you might have to go out and buy.   At least you will have a backup of all files including those you deleted in error.   Clonezilla might help in cloning.   Or dd command.  [COLOR=DarkRed] [EDIT] This is the advice given above as I was writing this.[/COLOR]

I believe that photorec may be better than testdisk for recovering files but filenames are lost.

If you get to the point where you have to shut down your PC then I would recommend recovermyfiles (runs on windows) which would be applied to your disk in slave mode .. you would have to remove your drive and place it in a USB enclosure and run recovermyfiles from a working PC.   But this requires a shutdown.

There is another thread giving a list of recovery software.  If I find it I'll post it as a p.s.

---

### Post by Margaret Dumont on 2011-04-28
Ok, I will try to find someone from who I can borrow an external drive to make the image and hope to find a solution soon. 

Thank you, mdurham and dragonfly. I'll let you know if any of your suggestions work for me.

---

### Post by Blasphemist on 2011-04-28
I'm not sure just how you deleted the file but I just tried to do this myself. In Ubuntu's Nautilus file manager I deleted a file in my windows partition. I then looked at the root of the windows partition. C:\ in windows terms but I did this still in Nautilus. I saw a directory named .Trash-1000. In that folder was a files directory and in that directory was the deleted file and I could open it.

---

### Post by Margaret Dumont on 2011-04-28
Jim, which are your Ubuntu and Windows versions? Maybe that can be the reason why I don't get this folder?

When I do the same thing Ubuntu tells me that the file can't be moved to the Trash and whether I wish to delete it permanently.

---

### Post by Blasphemist on 2011-04-28
I'm using windows 7 and Ubuntu natty (11.04). I don't think the ubuntu version would change this but it could be that the windows version would or maybe even the partition type. My windows partition is ntfs. You can see the type in gparted. I did this because I had seen this on a picture card when I manually deleted something. Is your file manger nautilus (help, about)?

---

### Post by Margaret Dumont on 2011-04-28
Both things (partition type and file manager) are the same in my case.

---

### Post by oldfred on 2011-04-28
I mount my c: in /mnt/cdrive. When I deleted a file it was gone.

But I mount my NTFS shared in /mnt/shared and link it into /home. For whatever reason when I deleted a file there, it gave me the pop message of delete, but then I found it in .trash-1000 in the top level of the shared partition.

Do not know if that is how it is mounted & linked or something else. I mount both identically other than the link.

I have used photorec to recover a couple of folders. I think it found files from entire drive as I found a lot of stuff that was not in the missing folders. It takes a long time to run, does not recover file names (they are gone), as it is just scanning drive for bits on the drive that look like a file. You can restrict it to recover only certain file extensions. I had saved a .txt file many times. It found it many times - each of the history. Between backup and some of the copies I got most of my data back, but never did find last saved version as there were over a 1000 .txt files and I just gave up. I did a lot of bashing to move files, then a lot of grepping to try to see what was in my text files.

While the horse is out of the barn and it is a little late to close the door.  I might suggest a separate /shared NTFS partition with your important data. Only mount c: as read only. And regular backups of the /shared partition. I like rsync to a backup partition and periodic writes to DVDs. Depending on value of data you can backup as frequently as you are comfortable with losing data.

---

### Post by fdrake on 2011-04-28
> **Margaret Dumont said:**
> Hello to everyone,


This  morning I mistakenly deleted from Ubuntu a folder located in the  Windows partition which contained important files from my work. I  thought I would be able to restore those files from Ubuntu's trash but  there was no trace of them. I have a partial backup but much of the  latest work is lost.
what a great morning to start the day eh..? 

how did you delete the files . by overwriting the folder and the files or by selecting them and pressing DEL. if the 2nd one did a confirm window pop-up? what users were you running by doing that action?

---

### Post by Margaret Dumont on 2011-04-28
I believe what happened is that  the file I wanted to erase was already selected so I just had to press DEL, but I failed to realize that for some reason the work folder was also selected out of my sight.

It's possible that a confirmation window popped-up but I only realized what happened afterwards because it took an instant too long (at least a bit more than I expected) to erase such a small file.

I was running the default main user of Ubuntu that requires you to perform sudo when executing sensitive commands.

Yes, it was wonderful. Actually, it's been a "great" week altogether...  :-P   Now I expect seven years of good luck to compensate.  :-)

---

### Post by Margaret Dumont on 2011-04-29
Ok. So I tried to make the Windows partition as read only to prevent anything to mess up with the drive by 
```
sudo mount -o remount,ro /media/xp
```but it said that remounting is not supported so I just did
```
sudo umount /dev/sda1
sudo mount /dev/sda1 /media/xp -o ro
```which worked well.

Now a friend of mine has lent me an external hard drive so I can make a copy of the partition, but **dd** has many options (clone, image and backup) and I'm not sure if all of them will copy the whole structure of the partition (in particular the "empty" regions where my files might be). Do you have any advice on which is the way to go for me?

Thank you!

---

### Post by dragonfly41 on 2011-04-29
You can also use clonezilla to take a copy of your entire disc drive.

[http://ubuntuforums.org/showthread.php?t=1736591](http://ubuntuforums.org/showthread.php?t=1736591)

There is a copy of clonezilla on Parted Magic .. or burn your own CD.

[COLOR=DarkRed]Might be safer burning this Parted Magic rescue disc on another working PC to avoid any overwriting of deleted files in your drive you are trying to recover.[/COLOR]

[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

---

### Post by mdurham on 2011-04-29
you don't need any options with dd, you would do:

(assuming that the windows partition is on sda1)
sudo dd if=/dev/sda1 of=/media/BACKUP_DRIVE/WindowsBackup.dd

"if" is input file
"of" is output file
look in /media for the backup drive name

WARNING: be careful, dd will not protect you from silly mistakes, it will do exactly what you tell it without question.
Obviously, also make sure there is enough room on the backup drive.
Good luck.

---

### Post by mdurham on 2011-04-29
fdrake wrote: "reality is your pure immagination".
That's assuming that your imagination is pure, it might not be.:)

---

### Post by Margaret Dumont on 2011-05-01
Thank you.

I created an image of the partition with dd and it's 30 GB, which is perfect cause that was the size of the partition.

Since my files didn't seem to be between Testdisk's recovered files I tried with Photorec. The first had "only" found about 2200 files and the last has found about 5000. And to me it seems that at least some of the files I erased have been found (it's hard to know at first sight if it's all of them), which makes me feel somewhat relieved.

The big problem now is to sort out the meaningful files from all the trash since the names have nothing to do with the originals and there's no such thing as a directory structure and everything is mixed up in a single folder. Besides, they haven't kept the original creating date either. 

Luckily, Photorec has an option to look only in the free space of the  partition and, since I didn't have much, I "only" have to deal  with 2 GB of recovered files.

Although right now it seems a nightmare (or maybe impossible to really succeed) to find among the 5000 files and properly name each one of the different 20 versions of a same article, to name an example, so I don't feel right now like I've truly recovered the files yet.

Does anybody have any experience with a program that does something in between Testdisk and Photorec?

---

### Post by Margaret Dumont on 2011-05-01
Now that I've looked through the recovered files in more detail it seems to me like Photorec only found certain kinds of file types. I couldn't find any *.bib or *.opj, which were among the deleted files. 

Doing a search within the recovered files:

```
/media/External_Hard_Disk/Recovery$ find . -name *.bib
```

yielded no results at all.

I'm afraid that, unless I find a program able to bring back any kind of file, many of my files will remain lost beyond recovery.  :-(

---

### Post by dragonfly41 on 2011-05-02
Although Photorec does recover files you've found that it is difficult to identify the files you want from hundreds of randomly named files.   the file directory is lost.

I have reported in a number of posts here that I have had good results using recovermyfiles  from [http://www.recovermyfiles.com](http://www.recovermyfiles.com).  the file names are preserved .. usually .. and you can select the files to be recovered .. and extensions such as *.bib or *.opj .. by ticking each folder.   Photorec does not provide this flexibiiity.

However ..

[LIST]
[*]this program only runs on windows .. probably on another working PC
[*]you need to physically and carefully remove your damaged drive (unless it is an external drive) to place it in a USB container to be analysed by recovermyfiles and this may have the risk of you physically damaging connectors etc. or not using anti-static precautions .. a job best done by an experienced person
[/LIST]
          [COLOR=DarkRed][Correction] I see that you now have an external clone of your disk so this step can be eliminated.  
          Just plug your external drive into another windows environment where you can experiment with recovermyfiles].[/COLOR]


[LIST]
[*]it is not free .. although you can use it first in trial mode to see if you can recover files
[/LIST]

There are other (free) forensic data recovery tools you can try such as foremost and scalpel.


[COLOR=Blue][ADDED RESEARCH]

*.bib seems to be associated with Papyrus database file

[http://dotwhat.net/bib/1239/](http://dotwhat.net/bib/1239/)

bibliographies?

The .BIB file extension is an ASCII formatted list of references.


*.opj seems to be associated with rCAD PCB Designer

[http://dotwhat.net/opj/4113/](http://dotwhat.net/opj/4113/)

Cadence pcb design?



I suggested use of TEXTstat in this thread ..

[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

to analyse the corpus of hundreds of files with random names.

After installing TEXTstat (see instructions in thread) create a corpus of your 30 GB of files recovered from Photorec.

Then apply word frequency list from corpus.

Then search for key words in word frequency list to narrow down your search.

You can inspect the concordance of files.

...

Another approach you might try is to write a bash script to scan through your recovered files and inspect metafiles.[/COLOR]

---

### Post by Margaret Dumont on 2011-05-02
Thanks, dragonfly.

The *.bib files are BibTeX bibliography databases in text format, and *.opj are Origin Projects. But they were just two examples. There were many other file types among the files I'd like to recover that Photorec doesn't recognise. 

For instance, results of data analysis (*.dat), which are basically two columns of numbers. The problem is that, let alone the fact that I would have to examine every single *.txt file to find the meaningful candidates, without the folder structure where the material was specified, and the name of the file that included the magnitude and temperature, all this numbers are completely useless.

I'm downloading now Hiren's Boot CD which has several file recovery utilities. I'll let you know if I make any progress with that.

---

### Post by dragonfly41 on 2011-05-02
Here is the ubuntu link on data recovery ..

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I really would try recovermyfiles in evaluation mode.

[COLOR=DarkRed][EDIT][/COLOR]

Also re: Photorec .. read these ..

Read these ..

[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

---

### Post by oldfred on 2011-05-02
Linux does not use file extensions, but header data in the file. Perhaps your data is recovered but seen as text files?

You reminded me that during my recovery, I wanted to change how I did things. As I was grepping one of my text files that had saved many versions, why did I not have the file name & perhaps a date inside the file. In my case they are just text files and easy to save that way.

---

### Post by Margaret Dumont on 2011-05-03
Dragonfly, thanks for your help. Right now the disadvantages you pointed out from Recovermyfiles are too many for me to use it:

[LIST]
[*]I don't have another computer with windows to run it.
[/LIST]

[LIST]
[*]I  can't clone the partition in the external hard disk that I borrowed  because it's full of other stuff from its owner. I don't really have a  clone of my hard disk what I did was an image with dd so I could restore  it in case something happened but I don't know if Recovermyfiles will  identify this file as the partition and work only with this.
[/LIST]

[LIST]
[*]I strongly prefer to use free software.   :-)
[/LIST]
 

I have downloaded [Hiren's Boot CD]("http://www.hirensbootcd.org/")  which was made for this purpose and I highly recommend it. Among other  things, you can boot a small linux or xp from the cd, and it has a huge  amount of freeware/open source utilities already built in so it's easy  as pie to fix your computer. 

I succeeded in recovering some of  my files with their directory structure, names and everything. And I  found out that, after all, before I started the recovering process of  the partition, I had indeed copied something else in it that most likely  destroyed most of my files. I feel really stupid but at least I have  recovered something.

Although most of the utilities did a good  job, Piriform Recuva provided much more information than the rest and  DiskGenius did way better that the rest in preserving the folder  structure, so if you have to chose just one, I would go with DiskGenius.  In case it is useful to someone, among the file recovery utilities I  tried (all of them were able to recover the directory structure and  names of several files):

[LIST]
[*]**DiskGenius**: more than 5.700  restored files (I didn't see the exact number, these are only the ones  that I chose to restore). The feature that makes this the best program  from my point of view is that, even when the directory and subdirectory  name of a group of files is not available, the program restores all  those files together in the same folder simply naming it as "Lost Files"  and a number. So the files are neatly recovered in separate folders  when that was their original status. All other programs I've tried mix  all the files that had an unknown folder name in the same "Unknown"  recovery folder so it all ends up being a huge mess.
[*]**Piriform Recuva**:  unknown number of restored files. Listed 13.000 files in a standard  scan and 16.600 in a deep scan but not all of the listed files can be  recovered. Anyway, it's nice that it's giving so much information. Tells  you the condition of each file and whether it was overwritten and by  which other file. That proved really useful because it allowed me to see  that some of the deleted files had been overwritten just after  deletion. In my case it even listed files in "excellent" condition with  no name at all,  but I got an "Access is denied" message when I tried their recovery. I  recommend to use this program to gain insight on the situation of your  deleted files.
[*]Softperfect File Recovery: 8.400 restored files.
[*]Restoration: 8.600 restored files.
[*]Testdisk:  1.800 restored files. I had already tried this one from my linux  partition but I did it just to check how it worked from Hiren's cd.
[/LIST]
Just  for comparison, the Photorec version I executed from my Ubuntu  partition recovered more than 5.300 files but without any folder  structure and in many cases with random names (Hiren's cd also contains a  version of Photorec).

Now I only have to compare all the restored files from different programs to make sure that I recover all that was possible.


Oldfred,  I completely agree with you, I was thinking the exact same thing as I  was trying to recover my files... It would be so easy to make all the  files contain all the vital information from the conditions usually  written in its name instead of relying on the user's awareness!  Definitely, it will be something I'll keep in mind from now on.

Thank you all for your help and quick response!

---

### Post by Margaret Dumont on 2011-05-05
Good night!

Dragonfly, I have started analysing the files recovered by Photorec using TEXTstat, how you suggested, and I have found out that embbedded within standard files were some pieces of my precious *.OPJs.

My goal was to find out if Photorec had saved some of those files with a misleading extension as text files or something else. Surprisingly, I found part of what looked like an Origin file within a .GIF image and when I examined this image with a text editor I found bits and pieces of what were originally many different files.

So it looks like at least part of my information IS THERE after all, the "only" problem is that Photorec doesn't recognise this kind of files.

I've been thinking about using [Scalpel]("http://www.digitalforensicssolutions.com/Scalpel/") which in principle allows you to specify your own headers and footers to crave deleted files and restore them. This is done through a list of file types in a configuration file (scalpel.conf). For instance, for the *.ZIP files (extension, whatever, maximum length of file, header, footer) :

```
 zip    y    10000000    PK\x03\x04    \x3c\xac 
```And I know (because I've opened several *.OPJ files with a text editor) that all of them start with the text header "CPYA 4.2766" but the footer, if any, is not in ascii anymore. So I was wondering what program can I use to find out the binary footer to then translate it into [the code that Scalpel is understanding]("http://manpages.ubuntu.com/manpages/natty/man1/scalpel.1.html"):

>  To specify a value in hexadecimal use \x[0-f][0-f], and for octal use \[1-9][1-9][1-9]. Spaces can be represented by \s. Example: "\x4F\123\I\sCCI" decodes to "OSI CCI".Hexdump? I don't know any.

Or even better, does anybody know of a program similar to TextStat but that analyses any string of values from a group of files instead of only text strings? That would make the process of finding out the footer much easier.   :-)

---

### Post by dragonfly41 on 2011-05-05
Have you tried the regexp search feature of TEXTstat?

Also you might send a message to the author of PhotoRec to ask how your *.obj extensions might be found since *.obj is not in the PhotoRec default list of extensions.

[COLOR=DarkRed][EDIT]
For reference can you attach a small dummy *.obj file to this thread so that its innards might be inspected?[/COLOR]

---

### Post by Margaret Dumont on 2011-05-05
Hello Dragonfly!

Actually, I didn't see this option in TEXTstat, I'll check it out when I get home.

I've created a small *.OPJ file with a datasheet and its 2D graph, and a matrix with its 3D contour plot. I changed all the extensions to *.DOC to upload them but their names were sample.opj (project with everything), sampledata.ogw (only the datasheet) and samplegraph.ogg (only the 2d graph).

---

