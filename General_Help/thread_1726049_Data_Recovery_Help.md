---
title: "Data Recovery Help"
date: 2011-04-10
forum: General Help
---

### Post by HalfEmptyHero on 2011-04-10
So I had my external harddrive formatted as ext4, and decided that was stupid since I need to dual boot now. I backed up all my data, and transferred it onto another hard drive. One particular folder I decided to put into a 7zip archive first. Everything seemed to work, and like an idiot I didn't test the archive. It looked a little small, but I didn't even think about it. It turns out 7zip only packed half my data from that folder. I have already formatted my hard drive to ntfs but I have not put anything on it. This is around two years of work, and I want to recover it if at all possible. I was reading about testdisk, but wanted to check on a few things first. Should I delete the ntfs partition first, and just leave it with empty data? I haven't installed ubuntu again, as I noticed this right as I was setting up windows on my machine, and I see there is a testdisk version for windows. Will this be able to recover an ext4?


Any help is greatly appreciated, this is really the only important data that I have on my computer.

---

### Post by Telengard C64 on 2011-04-10
Do not write to the drive at all! You won't be able to recover anything if you overwrite the data.

---

### Post by Quackers on 2011-04-10
I wouldn't recommend doing anything to the disc before using testdisk. The less done to it can mean that less is over-written.

---

### Post by Telengard C64 on 2011-04-10
[list]
[*][http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[*][http://trinityhome.org](http://trinityhome.org)
[*][http://www.sysresccd.org](http://www.sysresccd.org)
[/list]

---

### Post by dragonfly41 on 2011-04-10
As the others write above ... don't use your disk any more!

Even though files are deleted there is still a chance of recovering them if the delete was recent.

But first have you checked if you have anything in Rubbish Bin?   Long shot!!

Other than that you might stand a better chance of recovering important data if you use the disk in slave mode in a USB enclosure to be analysed and recovered by another PC.   But only if you are comfortable with removing drives.

Test disk is your first port of call.

So stop using your disk now.

p.s. If test disk doesn't help you I've used RecoverMyFiles to good effect .. you can try it for free first ..

[http://www.recovermyfiles.com/data-recovery-software-download.php](http://www.recovermyfiles.com/data-recovery-software-download.php)

---

### Post by HalfEmptyHero on 2011-04-10
> **dragonfly41 said:**
> As the others write above ... don't use your disk any more!

Even though files are deleted there is still a chance of recovering them if the delete was recent.

But first have you checked if you have anything in Rubbish Bin?   Long shot!!

Other than that you might stand a better chance of recovering important data if you use the disk in slave mode in a USB enclosure to be analysed and recovered by another PC.   But only if you are comfortable with removing drives.

Test disk is your first port of call.

So stop using your disk now.

p.s. If test disk doesn't help you I've used RecoverMyFiles to good effect .. you can try it for free first ..

[http://www.recovermyfiles.com/data-recovery-software-download.php](http://www.recovermyfiles.com/data-recovery-software-download.php)

My drive is an external usb drive, so that's not an issue. Also, I didn't delete the files, I deleted the partition they were on and then added an ntfs partition. I haven't written anything to the ntfs partition though.

---

### Post by dragonfly41 on 2011-04-10
> My drive is an external usb drive

so it should be easy to try RecoverMyFiles from windows .. free trial .. at least to see if anything can be recovered.

---

