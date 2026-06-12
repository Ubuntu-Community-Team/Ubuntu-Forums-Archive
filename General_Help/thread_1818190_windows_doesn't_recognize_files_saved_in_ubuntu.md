---
title: "windows doesn't recognize files saved in ubuntu"
date: 2011-08-04
forum: General Help
---

### Post by jadu on 2011-08-04
Hello, 

I've had a problem for a while-- when I save files on a USB stick in Ubuntu, then put it in a windows computer, it doesn't recognize the files. It only recognizes a video file that I have, but not the .doc files. The folders either don't appear or only appear as shortcuts. I thought it was just me, but I talked to other people with the same problem. Any idea how I can fix that?

thanks

---

### Post by zero2xiii on 2011-08-04
Oka this is a strange problem, or just lacking clearity.. lets see...

Ok first of all, I assume your flash drives are correctly formatted (fat32).

Secondly, the doc files, how is it saved, what program, what exact FORMAT. For example, if you use libre/open office, there is 2 or 3 formats that share the extension *.doc... With what application (windows side) are you trying to open it with.

The folders that appear as shortcuts, make SURE you COPPY the files (right click, copy, paste) rather than drag and drop, you might just be making smbolic links (which is basicly the linux equvalent of shortcuts in windows).

Are you right clicking the removeable device and saying safely remove?

Please supply more information so we can help you track down the cause of this mysterious issue ;)

Edit:
What is the ownership of the files you copy to the drive on the linux computer, eg can "nobody" access (rad and write) to the files and folders.... Does files and folders share the exact same names, does files share names only differing in Captitalisation?

---

### Post by jadu on 2011-08-04
Hello, 
Thanks for your quick reply.
I think the problem is the permissions (see below). But here's all the information you asked for:

1) I don't know how it's formatted. It's the same as when I bought it. When I look at properties, it says in "basic" "filesystem type: msdos". Is that it?
2) What kinds of files: I summarized too much. I have several folders with files inside them, and files outside the folders. The files are, looking more closely, many different formats: .doc, .docx, .pdf; also portable programs and associated files, with file extensions .exe, .xml, .sys.
3) How I copied them: I copied with the copy command, not with drag and drop.
4) I always right click and "safely remove device"
5) How I try to open the files in windows: I can't open them because in most cases they don't even appear. In ubuntu, they aren't "hidden files".
6) **Permissions**: This might be the problem. The one file that I CAN see in windows has the following permissions: owner acces: read and write; group access: read only; others access: read only.
The other folders have the following permisions:
owner: folder access-- create and delete files: file acces: ----;
group: folder access: none; file access: -----; 
others: folder access: none; file access: -----; 
I try to change them and it changes back automatically. I entered nautilus as sudo and it still doesn't let me change them.

Any ideas?
thanks

---

### Post by glene77is on 2011-08-04
> **jadu said:**
> Hello, 

I've had a problem for a while-- when I save files on a USB stick in Ubuntu, then put it in a windows computer, it doesn't recognize the files. It only recognizes a video file that I have, but not the .doc files. The folders either don't appear or only appear as shortcuts. I thought it was just me, but I talked to other people with the same problem. Any idea how I can fix that?

thanks


This problem/info is too general to offer direct solutions, IMO. 
I am not able to follow which OS is doing what,  from your two posts,  
in order to define the problem(s). 

> 
5) How I try to open the files in windows: 
I can't open them because in  most cases they don't even appear. 
In ubuntu, they aren't "hidden  files".Well, I have yet to see a M$ OS that will outright read/write to any Linux formatted partition. 
Linux will read/write to a dozen different formatted HD systems, 
but Microsoft is concerned only with their own money-making system. 

They " only appear as shortcuts."  from Ubuntu  or M$ ?.   
I had a similar problem, caused by a click and drag,  which transferred only a LINK !!!
All these problems can be resolved.  :p    M$ was making a 'link'.  


Have courage.  The combo can work very well, but has peculiarities.  :)

My business computer has M$ XP, Ubuntu, Puppy, Tiny-Core, and Parted-Magic, 
controlled by Ubuntu Grub2.    
There are a few peculiarities that I have gotten used to.  ;)
 
I don't ever loose any data, 
but I do have to 'flip' permissions/owners sometimes, 
and there are quick short-cuts for that.    :D   
In Ubuntu, when it comes to changing owner and permissions from 'root' as sent by Puppy,  
I usually just "copy/paste" and use the (copy) file.  
The "paste" function applies my Ubuntu status. 

I keep Parted-Magic available, since it runs from RAM, and has good utility programs.  
I keep "PCMan file manager" aboard, since it allows me to drop to 'root' for full priviledges. 
I am adept in using the "Terminal" for simple script runs, just like in the old days.  

BTW, if you fall in love with the Live-CD Parted-Magic, you need to visit their website,
where you will find simple steps to Install Frugal to your PC, in either M$ or Linux partitions.  
I installed Parted-Magic 'frugally' inside the M$ XP system partition, 
and Tiny-Core Linux 'frugally' inside the Ubuntu system partition.

---

### Post by jadu on 2011-08-05
hello,
I think that the problem might be the permissions, then. From what I described about the permissions, is there something I'm doing wrong when I try to change permissions, that would explain why it's not working?
thanks

---

### Post by ottosykora on 2011-08-05
you have to find out exactly what file system is used on the target drive.

It should be fat32 or called also vfat. In this case there are no permissions at all, as on that file system no permissions can be stored and so no permissions can  be changed as they not any.

If you see that files on your target drive have permissions of some kind set, then you have probably ntfs formated drive.

Could you try to format it in fat32 ? Then all should work.

---

### Post by jadu on 2011-08-05
mmm, thanks. In "properties" for the drive, it says "msdos". Is that ok, or should I reformat it? and if you have a tip on how to reformat... thanks

---

### Post by GoffyGoober on 2011-08-05
It probably is a problem with partition formatting. But I agree, Windows alone can't find the Linux Partition. I know of a better technique:

Open up your file browser and go to the main file system (/).
Once there, you go into media and look into the files there. Find the one with the most windows-looking files.
Now that you have the Windows partition opened up, find where you want the file to be.
Finally, copy the file you want to transfer and past it in the folder where you want it to be in the Windows partition.

This should get the file over nice and easy. ;)

---

### Post by jadu on 2011-08-06
Thanks very much to all for your replies.
I didn't quite understand the last post, but it gave me an idea-- I just copied everything from the flash drive to my computer, and back again. 
Strangely, that worked, both on Windows 7 and XP.
Thanks again!

---

### Post by zero2xiii on 2011-08-06
> Thanks very much to all for your replies.
I didn't quite understand the last post, but it gave me an idea-- I just copied everything from the flash drive to my computer, and back again. 
Strangely, that worked, both on Windows 7 and XP.
Thanks again!

So your problem is solved now? If it is, please mark the thread as solved :biggrin:

---

