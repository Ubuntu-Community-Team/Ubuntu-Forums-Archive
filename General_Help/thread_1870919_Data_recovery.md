---
title: "Data recovery"
date: 2011-10-28
forum: General Help
---

### Post by Gwaro on 2011-10-28
I lost my files in Ubuntu 11.10(accidental permanent delete). Is there any way/program to recover them?

---

### Post by agillator on 2011-10-28
I think the answer is a definite 'maybe but probably not'. Do a google search for 'linux recover deleted files' and you will get a number of links to look at. They cover different situations and different methods. See if any apply to your situation. That's the best I can offer, I'm afraid. Of course everyone will tell you the same thing which doesn't help you now, but wouldn't it be nice to have a backup?

---

### Post by tartalo on 2011-10-28
testdisk & photorec

---

### Post by tubbygweilo on 2011-10-28
A search through your files via the Ubuntu Live CD or [Gparted]("http://gparted.sourceforge.net/") may save the day but also it may not:(

---

### Post by westie457 on 2011-10-28
If the file space has not been over-written then as already suggested testdisk/photorec. However permanent delete usually means exactly that with little to no chance of recovery.

A program that might have a good chance is ['RLinux']("http://www.r-tt.com/free_linux_recovery/"). Be aware that it will find a lot more than just the files you deleted.
I tried this a couple of years ago on a 80GB hard drive that had been formatted and partitioned and reinstalled 5 times. RLinux found enough file information to fill a 2 Terabyte drive. Due to the volume of info found the actual recovery steps were never tried.

---

### Post by linux.girl on 2011-10-29
> **tartalo said:**
> testdisk & photorec

Does anyone have experience with testdisk? Is it safe to use? Pros and cons?

I deleted something by mistake and think perhaps testdisk might help, but am afraid to use it before understanding better what it actually does.

---

### Post by Rubi1200 on 2011-10-29
> **linux.girl said:**
> Does anyone have experience with testdisk? Is it safe to use? Pros and cons?

I deleted something by mistake and think perhaps testdisk might help, but am afraid to use it before understanding better what it actually does.
Testdisk is used to recover partitions, MBRs etc.

Photorec can recover files.

Are they safe to use? Good question. My answer would be that I have seen both positive and negative results, but bear in mind that a lot depends on how bad the situation was to begin with.

Here is a link for using Photorec and similar tools:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by collisionystm on 2011-10-29
PhotoRec should work fine. The important thing in this situation, no matter what program you use, is to keep disk usage to a minimum. You don't want to risk an overwrite.

---

### Post by linux.girl on 2011-10-29
Thanks! The data that I want to recover is on an external drive. I accidentaly shift+del a file that I really need, but I dont want to jeopardize the whole content of the disk just to get that one file back. So the question is, would photorec damage my other stuff if I try to use it to recover that one file?

What do you guys think? Is it worth it to give it a try, or perhaps better safe than sorry?

---

### Post by collisionystm on 2011-10-29
> **linux.girl said:**
> Thanks! The data that I want to recover is on an external drive. I accidentaly shift+del a file that I really need, but I dont want to jeopardize the whole content of the disk just to get that one file back. So the question is, would photorec damage my other stuff if I try to use it to recover that one file?

What do you guys think? Is it worth it to give it a try, or perhaps better safe than sorry?


On an external drive?

What kind of filesystem is it? Can windows read it???

If so, SAVE YOURSELF ALOT OF TIME.

Boot windows and use this program

[http://www.piriform.com/recuva](http://www.piriform.com/recuva)

BEST PROGRAM EVER!!!!

Get from here

[http://www.filehippo.com/download_recuva](http://www.filehippo.com/download_recuva)

---

### Post by linux.girl on 2011-10-29
The external drive is NTFS. I dont have windows anymore, but I guess I can use a VM to install windows and then recover the file?

Thanks for the tip! But just out of curiosity, why is it any better than doing it on linux, with photorec, etc?

---

### Post by collisionystm on 2011-10-29
> **linux.girl said:**
> The external drive is NTFS. I dont have windows anymore, but I guess I can use a VM to install windows and then recover the file?

Thanks for the tip! But just out of curiosity, why is it any better than doing it on linux, with photorec, etc?



Well, I can say that from experience... It is very fast. Has a nice GUI and is just flat out simple. Not every program in Ubuntu is better.

I guess really it is just a personal opinion and one that I feel so highly about I choose to recommend it!! :)

---

### Post by linux.girl on 2011-10-29
Fair enough, many thanks for the tip, I will certainly try it out!

:D

---

