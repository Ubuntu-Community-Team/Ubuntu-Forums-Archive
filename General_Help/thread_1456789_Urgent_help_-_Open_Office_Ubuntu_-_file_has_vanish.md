---
title: "Urgent help - Open Office Ubuntu - file has vanished! &quot;General input/output error&quot; :("
date: 2010-04-17
forum: General Help
---

### Post by Ian D on 2010-04-17
Hello,

I've spent all day editing a file in Open Office in Ubuntu - a very important file which is part of my final degree work. I have just gone to open it again, only to find that, terrifyingly, it has completely vanished. I'll explain exactly what I have done:

[LIST]
[*]Original file (.docx) was created using Office 2007 Windows 7 on the NTFS partition.
[*]I booted into Ubuntu to run a Linux program, and continued editing the file there with OpenOffice3 in Ubuntu, from the Windows partition.
[*]When saving the file, I saved it as a different name (.docx) in the same folder on the Windows NTFS partition, and continued to work on it all day.
[*]I turned the computer off, and after an hour turned it on, booting into Windows. I find that the new file, with all of today's work, is not there.
[*]I boot into Ubuntu, wondering if I could have possibly saved it somewhere else by mistake. I hadn't. Clicking the filename in the Recent Documents menu opens OpenOffice, and the error message "General input/output error while accessing /home/ian/Documents/Windows Documents/Uni Final Year.......docx." ('Windows Documents' is a link to Documents on the Windows partition).
[/LIST]

Where has the file gone? It is not possible for it to vanish? It isn't in the trash. Could anybody tell me how I could get the file back - does OpenOffice keep a cache, or would it have survived in the form of a temp file anywhere? It's so important, as I have so little time now before it has to be submitted, and to have to redo everything would be something of a disaster. I'm always so good with backups, and can't imagine how this has happened!

Any help hugely appreciated!

Thanks,
Ian

---

### Post by jaco223 on 2010-04-17
Try this link. It is about using the "find" command. Hope it helps.

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

Jaco

---

### Post by oxf on 2010-04-17
> **Ian D said:**
> Hello,

I've spent all day editing a file in Open Office in Ubuntu - a very important file which is part of my final degree work. I have just gone to open it again, only to find that, terrifyingly, it has completely vanished. I'll explain exactly what I have done:

[LIST]
[*]Original file (.docx) was created using Office 2007 Windows 7 on the NTFS partition.
[*]I booted into Ubuntu to run a Linux program, and continued editing the file there with OpenOffice3 in Ubuntu, from the Windows partition.
[*]When saving the file, I saved it as a different name (.docx) in the same folder on the Windows NTFS partition, and continued to work on it all day.
[*]I turned the computer off, and after an hour turned it on, booting into Windows. I find that the new file, with all of today's work, is not there.
[*]I boot into Ubuntu, wondering if I could have possibly saved it somewhere else by mistake. I hadn't. Clicking the filename in the Recent Documents menu opens OpenOffice, and the error message "General input/output error while accessing /home/ian/Documents/Windows Documents/Uni Final Year.......docx." ('Windows Documents' is a link to Documents on the Windows partition).
[/LIST]

Where has the file gone? It is not possible for it to vanish? It isn't in the trash. Could anybody tell me how I could get the file back - does OpenOffice keep a cache, or would it have survived in the form of a temp file anywhere? It's so important, as I have so little time now before it has to be submitted, and to have to redo everything would be something of a disaster. I'm always so good with backups, and can't imagine how this has happened!

Any help hugely appreciated!

Thanks,
Ian
 
As long as you saved it it IS still there somewhere! "General input/output error" sounds like a permissions issue which would make sense since you've saved it on a different partition

---

### Post by eltonw on 2010-04-17
> **Ian D said:**
> Hello,

I've spent all day editing a file in Open Office in Ubuntu - a very important file which is part of my final degree work. I have just gone to open it again, only to find that, terrifyingly, it has completely vanished. I'll explain exactly what I have done:

[LIST]
[*]Original file (.docx) was created using Office 2007 Windows 7 on the NTFS partition.
[*]I booted into Ubuntu to run a Linux program, and continued editing the file there with OpenOffice3 in Ubuntu, from the Windows partition.
[*]When saving the file, I saved it as a different name (.docx) in the same folder on the Windows NTFS partition, and continued to work on it all day.
[*]I turned the computer off, and after an hour turned it on, booting into Windows. I find that the new file, with all of today's work, is not there.
[*]I boot into Ubuntu, wondering if I could have possibly saved it somewhere else by mistake. I hadn't. Clicking the filename in the Recent Documents menu opens OpenOffice, and the error message "General input/output error while accessing /home/ian/Documents/Windows Documents/Uni Final Year.......docx." ('Windows Documents' is a link to Documents on the Windows partition).
[/LIST]

Where has the file gone? It is not possible for it to vanish? It isn't in the trash. Could anybody tell me how I could get the file back - does OpenOffice keep a cache, or would it have survived in the form of a temp file anywhere? It's so important, as I have so little time now before it has to be submitted, and to have to redo everything would be something of a disaster. I'm always so good with backups, and can't imagine how this has happened!

Any help hugely appreciated!

Thanks,
Ian
'general input / output error" is invariably a sign of disk corruption. 
You could:
1) On the Windows side, defrag your hard drive.
2) Depending on how you did your initial Options in Open Office, it can make regular backups while you are working... search your HD for files with the .bak extension. (If you use the first letters of the file and a wildcard, PLUS the extension, you should get faster results to your search.

e.g. Original filename: UNIwhatever.doc, SEARCH for un*.bak, or uniw*.bak....


HTH....

---

### Post by Ian D on 2010-04-17
Thank you all for your replies so far.

> **oxf said:**
> As long as you saved it it IS still there somewhere! "General input/output error" sounds like a permissions issue which would make sense since you've saved it on a different partition
Would you have any suggestion as to how to solve such an issue? I currently can't find the file in any form :(

[QUOTE=eltonw]'general input / output error" is invariably a sign of disk corruption. 
You could:
1) On the Windows side, defrag your hard drive.
2) Depending on how you did your initial Options in Open Office, it can make regular backups while you are working... search your HD for files with the .bak extension. (If you use the first letters of the file and a wildcard, PLUS the extension, you should get faster results to your search.

e.g. Original filename: UNIwhatever.doc, SEARCH for un*.bak, or uniw*.bak....[/QUOTE]
Unfortunately, searching for .bak files hasn't brought up anything related to my file. I also found the backups folder in .openoffice.org folder in the home directory, but unfortunately it's empty.

I've done a search in Ubuntu and Windows of all the files that have been modified today, including the system and hidden ones, but the file isn't there - not even renamed as something else or with a different extension.

Does anybody have any additional suggestions? I would be ever so grateful, and I would love to understand how it is possible that Ubuntu could randomly delete a file that it had saved?

Thanks very much in advance,
Ian

---

### Post by Ian D on 2010-04-17
Interestingly, if I create a file in Open Office, save it and then delete it, trying to open it from Recent Documents beings up the error ".....docx does not exist". This is different from the error that comes up when trying to open the file that I saved - "General input/output error while accessing .....docx".

This would imply that the file must be there, but has been corrupted somehow when writing to the NTFS partition?

If anybody knows anything about this, I'd be very grateful for any hope of retrieving the file!

---

### Post by oxf on 2010-04-18
> **Ian D said:**
> Interestingly, if I create a file in Open Office, save it and then delete it, trying to open it from Recent Documents beings up the error ".....docx does not exist". This is different from the error that comes up when trying to open the file that I saved - "General input/output error while accessing .....docx".

This would imply that the file must be there, but has been corrupted somehow when writing to the NTFS partition?

If anybody knows anything about this, I'd be very grateful for any hope of retrieving the file!

The" General input/output error" still sounds like a permission thing to me. Its possible though its been corrupted, in which case it is still there somewhere just a matter of finding it. I had the same error trying to write to a flash drive which was formatted in FAT32. It was solved when I changed ownership of it. TBH I've noticed strange permission issues writing from Linux to another partition/drive which is formatted in Windows so I dont do it any more. 

My most recent permission/partition issue was EXT3 but maybe of some help. 
[http://ubuntuforums.org/showthread.php?t=1423255](http://ubuntuforums.org/showthread.php?t=1423255)
Perhaps someone else can shed some light on this?

---

### Post by Hagar Delest on 2010-04-19
The General Input/output is a very common error message in OOo. Not always linked to a disk problem. It just means that the file is corrupted.

.docx is not a standard file format (MS Office doesn't use the ISO version of OOXML but a custom flavor - to insure the vendor lock-in policy). Its support is therefore not that perfect. Especially with OOo since the official version doesn't support the save as .docx. Only the Novell version delivered by default with Ubuntu can. But perhaps the export filter is not that perfect. That's why this file format should be avoided. Better use the native ODF. Moreover, you use the NTFS partition, I would have worked with a copy on the GNU/Linux partition instead, to avoid problems with access to such partition.

For your issue, you can try to open the .docx file with an archive manager and see if you can retrieve something.

---

### Post by dez93_2000 on 2011-02-08
if it's of any interest to anyone reading this with similar problems, or hopefully to people who haven't had similar problems - I spent last evening doing some work on a docx file emailed to myself from work (which i saved in ubuntu partition) changed the whole file, saved, closed, reopened to change one last thing, it was blank except for the title which i changed. So it had saved one change and deleted the entirety of the rest. When I reopened today after an angry sleep, it offered to recover to.... the original pre-edited file. Yay.

Subsequently, even if it turns out i did something wrong, BECAUSE I did everything normally and intuitively (opened a saved file, edited, closed) and it was OOs fault, i'll be using notepad from now on.

Annoyingly, the same thing happened in Ubuntu's pdf reader last week, which i fixed by getting adobe reader. Literally amazing that these most basic of problems can exist.

---

