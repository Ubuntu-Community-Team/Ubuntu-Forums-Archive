---
title: "Data Recovery Help"
date: 2009-12-13
forum: General Help
---

### Post by Punko353 on 2009-12-13
Greetings,

I am hoping someone can help me with my problem.   I am not a Linux geek by any means,  I mainly use Windowz because of my work (3d modeler using 3d Studio) but have been playing around with Linux for a few years now.  If it were not for my work I would have switched to Linux a long time ago.

My problem is this:

A couple of weeks ago I was working on my Win Pc and on a reboot I got an error saying it could not find one of the major system files.  I managed to fix the problem and my pc was up and running just fine after that...  (or so I thought).

I have a 250 gig drive in my main work machine and decided I would start backing up my files to another networked pc.  As I was backing up the drive it started to give me some CRC errors in reading some of the files and before I could finish backing eveything up the drive failed.

I had a spare pc so I went out and bought a new 500 gig drive so I could install Ununtu on it (so far my favorite flavor of Linux).  

I have a semi-understanding of what I am doing so the first thing I did was create a 200 gig partition to install Ununtu and I left the other 300 gig free so I can copy the content of my bad drive to the new partition.

Here is where I need help.


My linux partition is** dev/sda2 **
the linux install is shown as **dev/sda5**
the linux swap is on **dev/sda6**

The empty partition is on **dev/sda1**

the bad drive is **dev/sdb1**


I am trying to use ddrescue (GNU ddrescue) to recover any data on the drive that I can.  Since I didn't get everything backed up.   I have not written to the bad drive since I pulled it out but the errors I am getting say the file structure is bad.

The drive does have readable data on it because I was able to run Testdisk on it as well as pull some files off using PhotoRec.


My problem is I am not clear on the right command to use.  I have read almost eveything I can find about ddrescue but still do not understand the syntax I need to use.

I have tried:

ddrescue -n /dev/sdb1 /dev/sda1 rescue.log

I think that command is suppose to copy all good blocks to sda1 but I
get an error saying:

cannot open input file: permission denied

I thought the reason for using ddrescue (GNU ddrescue) is because it does not 
need an input file and will automatically write the log file.


As I said,  I am not a Linux guru and probably know just enough to get myself
in trouble... ;)   


Can anyone help?

Thanks,
Bob

---

### Post by audiomick on 2009-12-13
Looks like the user you are logged in as doesn't "own" the bad drive, sdb1.

Try putting 
```
sudo
```
before the ddrescue command ( with a space between )
This means "super user do" i.e. "execute the following command as the super user"
You will be asked for your password ( the one you log in with), and will not see this as you type it in.

---

### Post by Punko353 on 2009-12-13
Thanks man...

I feel pretty stupid...  

I spent a good part of yesterday trying to figure out what my problem was.  I did however learn a lot from all the searching I did .

Thanks for the fast reply.  

Bob

---

### Post by earthpigg on 2009-12-13
another data recovery tool that you may find helpful:

[testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and its cousin photorec. both in the repos. photorec comes with testdisk.

---

### Post by Punko353 on 2009-12-13
I did run testdisk and photorec on the drive in another windows box but I knew Linux would be the best choice to actually recover any data ;)

I am doing this more of a challenge than the need for the data (and it gives me a reason to use Linux...  

It appears the drive is being copied with the above command I used.  It is still working and looks like it will be a while.  

The one thing I am not quite sure of is what I need to do after I get the data copied over.

Any help would be welcome ;)

Bob

---

### Post by earthpigg on 2009-12-13
> 
The one thing I am not quite sure of is what I need to do after I get the data copied over.

you had a failing hard drive, and you backed up your data before it failed.

buy a new hard drive, put the data back?

---

### Post by Punko353 on 2009-12-14
As I said in my other post, I am doing this more for the challenge than the data.  I do regular backups but I did loose a couple of files that I would like to try and recover. 

This just gives me a good reason to use Linux and to see if I can squeeze anything out of this dead drive.

Is it true from what I read that if your file system is corrupted you can't get any files back?

Bob

---

### Post by diaco on 2009-12-14
> **earthpigg said:**
> another data recovery tool that you may find helpful:

[testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and its cousin photorec. both in the repos. photorec comes with testdisk.

thank you earthpig
after reading your post. i got testdisk and it rescued my external hdd. there were over 200 gigs of valuable data and no paid application in windows (like recovermyfiles) were able to recover it (with accurate file name and paths).
I'm wondering that a free linux app can restore a ntfs partition better than any windows one!
I feel very grateful about you and about linux! thank you again & sorry 4 my english.

---

### Post by earthpigg on 2009-12-14
outstanding, diaco.

in certain areas, GNU/Linux is almost inarguably superior to Proprietary software. usually, the nerdier the task, the more likely it is that Free Software will blow anything else out of the water.

---

