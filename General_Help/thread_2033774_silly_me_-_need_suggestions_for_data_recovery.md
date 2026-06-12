---
title: "silly me - need suggestions for data recovery"
date: 2012-07-26
forum: General Help
---

### Post by jwferk1 on 2012-07-26
I was doing a reinstall of ubuntu the other day when the cat jumped on my lap.  Unfortunately, I was right on the screen where one selects the drive/partition to install the OS.  In the process of removing the cat from my keyboard, the two of us inadvertently managed to hit the "install" button while the wrong drive was showing in the selection box.  Regrettably, the installation started on my main backup drive instead of the place I wanted it to go.  The installation only ran for about 10 - 15 seconds but that was enough to delete the partition on the backup drive.  Now, of course, there's no access to the files which is not a good thing as the "backup" drive actually contained a bunch of files not on any other of my drives.

So - here's the setup.  I have a single box with two hard drives.  Windows 7 and 8 are installed on the first drive and Ubuntu is installed on the second drive.  The "backup" drive is a usb/external Seagate which was formatted in NTSF and could be accessed from both the Windows and Ubuntu sides.  Since I've lost the main partition, Windows no longer recognizes the drive so I can't do a data recovery from the Windows side of things.  Ubuntu sees the drive and can access it but it does't see any of the files that were (are) on the drive.

Now - after that long winded explanation of my stupidity (I am blaming the cat) I'd like to know what packages folks recommend to do a data recovery operation from Ubuntu.  I've got a couple of the forensic OS packages (Caine and Backtrace) but they are a pain in the back end.  Is there something that simpilier to use?

All suggestions are welcome.

The cat is not allowed on the desk for the night.

Cheers and thanks,
jwferk1

---

### Post by Dylan1473 on 2012-07-26
I've had some success with PhotoRec before. If you're on Ubuntu you can open a terminal and type: 

```
sudo apt-get install testdisk
```to download it and then

```
sudo photorec
```to start it. It runs in the terminal and has a relatively friendly interface (you don't need to learn a ton of commands). [Here's]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/") the page I  used to learn about it, still got it bookmarked.

It was the first program I ever had to use for data recovery and I found it pretty easy to use, though I wasn't able to recover the one program I was after (I think it was too big).

EDIT: The article is about a couple different methods of data recovery. You'll want to look at the sections on testdisk/photorec only.

---

### Post by marinara on 2012-07-27
i've used getdataback, and photorec.  getdataback is about 1000x times better.

---

### Post by raja.genupula on 2012-07-27
read this for more information 
[https://help.ubuntu.com/community/DataRecovery/](https://help.ubuntu.com/community/DataRecovery/)

---

### Post by jwferk1 on 2012-07-27
Thanks folks - appreciate the suggestions.  Will let everyone know how it comes out later tonight.

Cheers

---

### Post by Nixarter on 2012-07-27
They neglected to mention step #1.

Always, ALWAYS dd the drive/partition first!  Then do all the recovery operations (testdisk, etc.) on the COPY.  Else, you risk screwing up the data more, or accidentally wiping parts of it.

---

### Post by jwferk1 on 2012-07-27
> **Nixarter said:**
> They neglected to mention step #1.

Always, ALWAYS dd the drive/partition first!  Then do all the recovery operations (testdisk, etc.) on the COPY.  Else, you risk screwing up the data more, or accidentally wiping parts of it.

Nixarter et al.

Thanks again.  I used gddrescue to make a .dd file of the hard disk first before I did anything else.

At the end of the day I used "testdisk."  It turned out to be much easier than I had anticipated.  The entire (1TB) disk was a single ext4 partition.  I was able to use testdisk to exchange that to an NTSF file system and then have testdisk insert a new MBR.  Bingo, all files are now accessible and readable on both Win and Ubu.

Thanks again for everyone's suggestions.

The cat is now sleeping on her pillow on the desk.

---

