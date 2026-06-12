---
title: "No root system defined - WUBI install"
date: 2012-03-23
forum: General Help
---

### Post by ojdon on 2012-03-23
Hi there, no matter what version of Ubuntu or which DE I select using any version of Wubi that I can find (Various versions of the Lucid Wubi and the most up to date precise Wubi) I cannot get into Ubuntu.

It installs fine, reboots and can be selected from the boot loader but after the little text message saying about completing installation in x amount of settings it loads up a couple of message boxes and then displays the message:

> No root system file is defined.

Please correct this from the partitioning menu.

...Or something along those lines. I've also tried to install Xubuntu 10.04 LTS without Wubi but it can't seem to find my Windows 8 Consumer Preview partition. Ideally I only want to do a Wubi install for the time being since I need Windows for the last couple of weeks at University and only need to use Ubuntu 10.04 at the moment to compile Chromium OS with a Virtual Keyboard.

Any help?

---

### Post by bcbc on 2012-03-23
Please can you boot an Ubuntu CD (select "Try Ubuntu") and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). 
Usually this problem occurs due to:
1. Minor partition table errors
2. mix of gpt and mbr partition table data
3. unsupported raid

The bootinfoscript can provide the answer in some cases, and clues in others.

---

### Post by ojdon on 2012-03-24
Hmmm here is my [results.txt]("http://pastebin.com/F75CbV9Z").

It's showing the smaller Windows 8 partition and the "need-to-be-deleted" (Larger) Windows 7 partition. Can't see any issues as to why GParted/Installer can't detect the partition layout in order to dual boot Windows 8 Consumer Preview and Xubuntu (I want to get rid of the Windows 7 partition as it's no longer used). That is, if I can't fix the Wubi issue.

---

### Post by bcbc on 2012-03-24
Here's your problem:
> GUID Partition Table detected, but does not seem to be used.

See fixparts for more info: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by ojdon on 2012-03-24
Ah that's done the trick. Just needed to delete the leftover GPT data from when it used to be a OSX hard drive.

Thanks!

---

