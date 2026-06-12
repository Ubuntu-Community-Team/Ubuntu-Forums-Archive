---
title: "External HD- folders renamed and cant access files within them"
date: 2010-12-10
forum: General Help
---

### Post by Osiriskc on 2010-12-10
hey guys, this might be a questions for a Windows forum but whenever I post on them, I mostly get back very basic, and generic resolutions. so I need some straight forward answers i guess...

so recently i partitioned 6 gigs of my 1TB external drive for my xbox...which might be irrelevant , but this issue came up about 4 or 5 days after this...

Issue is that on my external drive, when everything was normal, I had a bunch of folders, some containing music and installed program data  and photos and ya, for Windows 7 64bit..after reconnecting with my computer then my xbox then my computer ect ect(always safely disconnect on PC) I now connect the drive to my computer, but instead of seeing the normal names of the folders and files, im seeing alterations of the names and I cant access the content within the folders.. example is i had a folder names Programs and it is now names PROGRAMS.1

I went to the properties of the drive and scanned it without auto-fixing the issue, and it gave me some errors but the most repeated being Orphan Truncated...there was a bit more to it, but i switched to Ubuntu to see if it was consistent with the os and didnt bother writing the errors down...

some of the files I can access but some I cannot...Any ideas???

---

### Post by Osiriskc on 2010-12-11
nobody? :[

---

### Post by argedion on 2010-12-11
Try running Tesk disk and see if you are having partition issues. Could be a virus that has attacked your system as well try doing a virus scan.

testdisk can be found here:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Osiriskc on 2010-12-11
thats one of the first things I did, I ran testdisk and it picked up the NTFS partition quick with no issues. the strange part that I just noticed, is that on Windows, Im not able to access ANY folders that have an altered name, but under Ubuntu I can access a few more folders even with the name changed…
it also altered the permissions to read only and I cant rename or anything along those lines.

I ran Avira under windows and it did pick up 28 fake photo gen detections from when I recovered my older HD to the external…it also picked up, what I believe to be false-positives, some photo recovery software from windows. but i read through the comments before downloading the program and multiple people confirmed that I would get false positives with the DL

---

### Post by Osiriskc on 2010-12-11
is it possible that by unplugging the drive from the xbox, then computer a few times has caused the device to become corrupted? if so, any ideas on how to reverse the corruption?

---

### Post by Osiriskc on 2010-12-12
im hoping someone gets back to me before I try something myself and do damage lol…  :/

---

### Post by coffeecat on 2010-12-12
> **Osiriskc said:**
> I went to the properties of the drive and scanned it without auto-fixing the issue, and it gave me some errors but the most repeated being Orphan Truncated.

You did a scan from Windows and it reported errors, but you didn't fix them?

> **Osiriskc said:**
> is it possible that by unplugging the drive from the xbox, then computer a few times has caused the device to become corrupted?

If you suspect filesystem corruption then, assuming it's an NTFS filesystem, you need to run chkdsk from Windows to fix any errors.

---

### Post by Osiriskc on 2010-12-12
> **coffeecat said:**
> You did a scan from Windows and it reported errors, but you didn't fix them?



If you suspect filesystem corruption then, assuming it's an NTFS filesystem, you need to run chkdsk from Windows to fix any errors.

Correct, from the properties screen of the drive in Windows, I went to tools and scanned for errors (cant remember the actual title) but I unchecked the box that said automatically fix because I've read about some people that lose the corrupted data when windows tries to fix it.. you think I'm safe allowing that?

---

### Post by coffeecat on 2010-12-12
If it's a NTFS filesystem you have no choice but to use Windows chkdsk or the  GUI tool. NTFS is a Microsoft filesystem so MS tools are the best ones for the job. There is no Linux utility that can repair NTFS as comprehensively as chkdsk can. I'm sure some people have lost data after chkdsk, but with any filesystem, with any OS, if you have a corrupted filesystem you run the risk of losing data. Sad but true.

If you want a little more control, you might want to run chkdsk from the command line rather than using the scanning tool, although I guess that is just a GUI frontend for chkdsk. See here:

[http://en.wikipedia.org/wiki/CHKDSK](http://en.wikipedia.org/wiki/CHKDSK)

However, before starting you might want to do a bit of googling. I believe there are some differences between the versions of chkdsk that come with the different Windows releases.

---

