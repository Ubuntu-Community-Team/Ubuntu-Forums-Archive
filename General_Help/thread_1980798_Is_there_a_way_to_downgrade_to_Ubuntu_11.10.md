---
title: "Is there a way to downgrade to Ubuntu 11.10?"
date: 2012-05-15
forum: General Help
---

### Post by johnboy601 on 2012-05-15
Ubuntu 12.04 is not being nice to me. Minecraft and Google Talk Plugin will not work for me. I'm starting to get very mad. I would really like my 11.10 back. Is there anyway to go back?

---

### Post by TheGuyWithTheFace on 2012-05-15
Absolutely. As far as I know, you should be able to simply put in the disk, USB, or whatever you had 11.10 on, and there will be an option to "upgrade". I think.

---

### Post by TheGuyWithTheFace on 2012-05-15
Wait. I believe the only way that'll work is if you erase all of 12.04 including your files and programs, which you probably don't want. Perhaps you could move your files to a separate partition first so they won't get deleted?

---

### Post by pbrane on 2012-05-15
Why won't minecraft work? I am running xubuntu 12.04, OpenJDK, and minecraft works fine for me. Perhaps these are issues that can be fixed. Google Talk plugin may need to be upgraded.

---

### Post by TheGuyWithTheFace on 2012-05-15
> **pbrane said:**
> Why won't minecraft work? I am running xubuntu 12.04, OpenJDK, and minecraft works fine for me. Perhaps these are issues that can be fixed. Google Talk plugin may need to be upgraded.

Good point. Johnboy, you may want to look at this:

[http://ubuntuforums.org/showthread.php?t=1812767](http://ubuntuforums.org/showthread.php?t=1812767)

---

### Post by BlinkinCat on 2012-05-15
> **TheGuyWithTheFace said:**
> Good point. Johnboy, you may want to look at this:

[http://ubuntuforums.org/showthread.php?t=1812767](http://ubuntuforums.org/showthread.php?t=1812767)

I wouldn't be rushing in to trying to downgrade just yet - :)

---

### Post by TheGuyWithTheFace on 2012-05-15
Personally, I wouldn't dream of leaving 12.04, but hey, linux is about freedom, right? You wanna downgrade, your choice.

---

### Post by johnboy601 on 2012-05-16
So, what is the best way to down grade if using a live CD will erase my files. I do have an extra hdd I could put every thing on.

---

### Post by wilee-nilee on 2012-05-16
You can't downgrade safely period. If this was a regular install your only option would be if you had a separate home, you could reinstall using that home.

---

### Post by TheGuyWithTheFace on 2012-05-16
I disagree. There's nothing stopping you from just copying your files and programs to your separate hdd and doing a clean reinstall on your original disk.

---

### Post by wilee-nilee on 2012-05-16
> **TheGuyWithTheFace said:**
> I disagree. There's nothing stopping you from just copying your files and programs to your separate hdd and doing a clean reinstall on your original disk.

That is not a downgrade, but a clean install.

Thread tittle:  Is there a way to downgrade to Ubuntu 11.10?

---

### Post by TheGuyWithTheFace on 2012-05-17
Perhaps I misunderstand, but I think by "downgrade" he means going from version 12.04 to 11.10. Perhaps that involves having to do a clean install? 

Or... I could be dead wrong. 

Regardless, it seems a clean install is the only choice, so it really doesn't matter.

---

### Post by johnboy601 on 2012-05-17
All I meant by "downgrading" was just going back to Ubuntu 11.10, not like upgrading by clicking a button and it working. I kinda expected it to make me format everything but I just don't want to loose anything. Good thing I have an extra HDD.

---

### Post by Mark Phelps on 2012-05-18
Reinstalling is not "Downgrading".  Downgrading requires doing something like a roll-back -- which is not available in Ubuntu.  We should not be telling folks they can "downgrade" when they can not.  That kind of misinformation only leads to confusion and frustration.

---

### Post by TheGuyWithTheFace on 2012-05-18
Ok, my bad.

---

### Post by johnboy601 on 2012-05-19
So what I have decided to do is this:
Mirror my main HDD.
Format my main HDD after the mirroring is done.
Boot off my flash drive and install a completely clean version of Ubuntu 12.04.
(I used the command dd to mirror the drive)
I really hope this will work. Also, after entering the dd command (everything is correct) and after entering my password, it just has a flashing cursor. Does this mean it's loading or should I close the terminal?

---

### Post by 2F4U on 2012-05-19
The dd command doesn't have a progress bar or something like this. The cursor just sits there until the command is finished. This may take some time, depending on how much data there is to be copied. If you close the terminal you terminate the process.

---

### Post by johnboy601 on 2012-05-19
> **2F4U said:**
> The dd command doesn't have a progress bar or something like this. The cursor just sits there until the command is finished. This may take some time, depending on how much data there is to be copied. If you close the terminal you terminate the process.

Yeah, I found that out. Now the problem is this error:
dd: writing to `/dev/sdb1': No space left on device
488392705+0 records in
488392704+0 records out
250057064448 bytes (250 GB) copied, 14230.2 s, 17.6 MB/s

Does this mean nothing got copied to the drive? I have less then 50GB of files on my 320GB hard drive so I figured it would copy to my 250GB drive. Also, using the disk utility, I can't mount the drive any more.

---

