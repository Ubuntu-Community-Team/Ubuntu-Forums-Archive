---
title: "Windows/Other os help?"
date: 2010-09-24
forum: General Help
---

### Post by thizzleboom on 2010-09-24
Hi everyone,
Please forgive is the incorrect place to post. I have a computer running Windows XP that is having hard drive problems and I was trying to copy the files off the drive using Ubuntu bootable cd but am having problems.

I looked around and it looks like the "Other OS" portion of the site is closed down. Is there any place on the site that would be better to post questions like this, or has the board moved away from these type of discussions to focus on Ubuntu only?

Thank in advance!

---

### Post by Megaptera on 2010-09-24
Hi,
Is this the sort of guide you're looking for?

[http://www.makeuseof.com/tag/how-to-back-up-data-on-your-computer-that-wont-boot/#more-32771](http://www.makeuseof.com/tag/how-to-back-up-data-on-your-computer-that-wont-boot/#more-32771)

---

### Post by thizzleboom on 2010-09-24
Almost, except I've done all that and have specific questions to ask about where I'm stuck.

I just didn't want to be rude and type it all out without knowing where to ask or even if these questions are on topic here. Should I just go ahead and post the problem and steps I've taken, etc?

---

### Post by Rubi1200 on 2010-09-24
What problems are you having?

I recommend Knoppix as a LiveCD for, amongst other things, rescuing files etc.

---

### Post by thizzleboom on 2010-09-24
Thank you for the quick replies. 

My Windows XP computer is stuck in an endless reboot cycle. I tried going into safe mode and it did the same thing. 

I then ran Seagate For Dos hard drive diagnostics (it's a Seagate drive), IBM Hitachi Drive fitness test (from Hiren boot cd), and both came back with no problems. No bad sectors, etc. 

I have some really important documents on there so the next thing I tried was to use Ubuntu Bootable to try to access the drive and save the documents. 

when I did this, I received the following error message: 

Error mounting: mount exited with exit code 13: Inode is corrupt(0):Input/output error 
Failed to open $MFT/$BITMAP: Input/output error 
Failed to load $MFT: Input/output error 
Failed to mount '/dev/sda1': Input/output error 
NTFS is either inconsistent, or there is a hardware fault, or its a SoftRaid/FakeRaid hardware. In the first case 
run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the 
device is a SoftRAID/FakeRAID then first activate and mount a different device....rest not applicable. 

Using the chkdsk suggestion from the error message, I tried running CIA CheckDisk 2.2/NTFS4DOS chkdsk from the Hiren Boot CD, but it just said 

"One of your disks needs to be checked for consistency. You may cancel the disk check, but it is strongly recommend that you continue. 
Windows will now check the disk.  
...
An unspecified error occurred." 

I'm not really sure what to do next or even what could be my problem.

---

### Post by Rubi1200 on 2010-09-24
> My Windows XP computer is stuck in an endless reboot cycle. I tried going into safe mode and it did the same thing. 
The first thing I would be checking is RAM; faulty memory can often cause problems like this.
Try taking out and cleaning (gently) the memory modules and then replacing them.

Alternatively, remove just one (I don't know how many you have of course) and try with just one stick and see what happens.

In any event, consider giving the Knoppix CD a try:
[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

---

### Post by thizzleboom on 2010-09-24
Thanks for the suggestions, I really do appreciate your responses. 

Since I can't get the drive to mount in Ubuntu I'm not sure this is the problem (maybe a symptom of the problem?) but I will try swapping out the ram and I have a Knoppix install downloading now. I will give both a try and report back.

Should I try running the same tasks in Knop that I did in Ubuntu (mount the drive, etc). Or should I be looking to try something else? Do you think running memtest86 or some other memory validation program would be able to identify these types of problems as well?

I'm sorry if these are stupid questions... I think I know enough about hardware/computers to be dangerous (get complacent, or try too much, etc) so I'm trying to double check my logic/thought process as I move along. Teach a man to fish...., etc.

I hope I'm not too difficult for you, and I really am appreciative of your help.

---

### Post by Rubi1200 on 2010-09-24
> **thizzleboom said:**
> Thanks for the suggestions. I will give them a try and report back. 

Do you think running memtest or some other memory validation program would help as well?
Yes. If you can, run memtest from the Ubuntu CD.

---

### Post by searchfgold6789 on 2010-09-24
Try installing testdisk from the live CD and run it to recover lost files, maybe?
if you do this I recommend reading the user manual  on it first. (in the terminal type man testdisk.) Once you finish installing it you have to run it from the terminal :)

---

### Post by thizzleboom on 2010-09-24
You guys are great! I'll be working on this throughout the afternoon, will report back later with progress. Have a good one, and thanks again!

---

### Post by Rubi1200 on 2010-09-24
You are more than welcome :)

---

