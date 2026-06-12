---
title: "Wubi Crashes At End?"
date: 2011-01-02
forum: General Help
---

### Post by bustedup277 on 2011-01-02
So I was running Wubi trying to install Ubuntu on my computer when at the very end it crashed and said "Could not retrieve needed files" or something like that. Then it said for more info check out the log file. Why did it crash?

I am using an hp mini notebook windows 7 trying to install Ubuntu with Wubi

---

### Post by SnickerSnack on 2011-01-02
Programs crash sometimes.  Did you look at the log file?  There's pretty much no way anyone can say what happened without looking at the log.

Did you try a second time?

---

### Post by bustedup277 on 2011-01-02
> **SnickerSnack said:**
> Programs crash sometimes.  Did you look at the log file?  There's pretty much no way anyone can say what happened without looking at the log.

Did you try a second time?

I tried to times, one last night and one this morning.

I don't where the log is, it said where it was but I forgot. ._>

---

### Post by SnickerSnack on 2011-01-02
Well, I doubt anyone can help you without that file.  You should probably try searching the web to find out where that file is (I don't know where it should be), and if that doesn't work, you might try installing again and writing down the file location when you get the error.

Edit: A quick google search (first link: [http://ubuntuforums.org/showthread.php?t=1439526](http://ubuntuforums.org/showthread.php?t=1439526)) gives this:

> More points if you attach the wubi.log file which is located in your user temp directory.

---

### Post by bustedup277 on 2011-01-02
> **SnickerSnack said:**
> Well, I doubt anyone can help you without that file.  You should probably try searching the web to find out where that file is (I don't know where it should be), and if that doesn't work, you might try installing again and writing down the file location when you get the error.

Edit: A quick google search (first link: [http://ubuntuforums.org/showthread.php?t=1439526](http://ubuntuforums.org/showthread.php?t=1439526)) gives this:

All I found in the user temp was a .txt file titled wubi-10.04.1-rev190.txt.

I pastebinned the contents here: [http://pastebin.com/suhqSXzA](http://pastebin.com/suhqSXzA)

---

### Post by SnickerSnack on 2011-01-02
Look at lines 969 through 1008.  It looks like there's something wrong with the files on the disc.  You can try downloading the file(s) again, but you should first look at the md5 sum on the file you already downloaded.  [http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

Basically, you need some software to compute the md5 sum of the file you downloaded, and you compare the hash number (letters and numbers I think) to the one listed on the site where you downloaded the file.  If the hashes are the same, then your download should be good.  If the numbers are different, then your downloaded file is bad and you need to download again.  I don't know of any windows software to compute md5 sums since I don't use windows.  But if you google a bit, you should be able to find some, though it's possible that windows does it already.

Of course, if you download the files again, be sure to check their md5 sums before trying to install.

---

### Post by bustedup277 on 2011-01-02
> **SnickerSnack said:**
> Look at lines 969 through 1008.  It looks like there's something wrong with the files on the disc.  You can try downloading the file(s) again, but you should first look at the md5 sum on the file you already downloaded.  [http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

Basically, you need some software to compute the md5 sum of the file you downloaded, and you compare the hash number (letters and numbers I think) to the one listed on the site where you downloaded the file.  If the hashes are the same, then your download should be good.  If the numbers are different, then your downloaded file is bad and you need to download again.  I don't know of any windows software to compute md5 sums since I don't use windows.  But if you google a bit, you should be able to find some, though it's possible that windows does it already.

Of course, if you download the files again, be sure to check their md5 sums before trying to install.

Thanks, I'll read up on that.

Also I was wondering, do I need to download the Ubuntu 10.04 (since I think Wubi doesn't go up to 10.10) .iso, I know I may sound stupid, but I didn't. I was just wondering if I needed it.

---

### Post by SnickerSnack on 2011-01-02
> **bustedup277 said:**
> Also I was wondering, do I need to download the Ubuntu 10.04 (since I think Wubi doesn't go up to 10.10) .iso, I know I may sound stupid, but I didn't. I was just wondering if I needed it.

I'm 99.9% sure you don't need to.

---

### Post by bcbc on 2011-01-02
You can't install ubuntu netbook using the wubi available at [www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer"). This version is at 10.04.1 and there is no netbook edition. Due to a bug it downloads the 10.04 version instead, then rejects it.

It can do this a number of times before failing. I think 3.

> 01-02 02:08 DEBUG  TaskList: ### Finished download
01-02 02:08 DEBUG  downloader: download finished (read 733837312 bytes)
01-02 02:08 DEBUG  TaskList: New task check_iso
01-02 02:08 DEBUG  TaskList: ### Running check_iso...
01-02 02:08 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
01-02 02:08 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
01-02 02:08 DEBUG  Distro: wrong version: 10.04 != 10.04.1
01-02 02:08 DEBUG  TaskList: ### Finished check_iso
01-02 02:08 DEBUG  TaskList: New task download
01-02 02:08 DEBUG  TaskList: ### Running download...
01-02 02:08 DEBUG  downloader: downloading [http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso

So, if you want 10.04 you need the [10.04 wubi.exe]("http://people.canonical.com/~evand/wubi/lucid/wubi-r189.exe"), or if you really want 10.10 you can use the wubi.exe found at [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

In general, installing wubi is easiest if you download the .iso you want e.g. [http://releases.ubuntu.com/maverick/ubuntu-10.10-netbook-i386.iso](http://releases.ubuntu.com/maverick/ubuntu-10.10-netbook-i386.iso) and then download the appropriate wubi into the same directory. Then run wubi.exe from there.

Later use that .iso to create an Ubuntu USB you can boot from - for rescue purposes.

Also, with wubi - never update packages grub-pc and grub-common. They are causing booting issues at the moment (can affect your whole computer). So just look through the list shown by Update Manager and uncheck these (look under the "Recommended" update list).

---

