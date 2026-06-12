---
title: "Linux made zip file not unzipping on Windows"
date: 2011-02-27
forum: General Help
---

### Post by NMFTM on 2011-02-27
I made an 8GB password protected Zip file on Ubuntu 10.10, sent it to a friend who's using Windows 7, and now she can't unzip it. The file transfer speeds between us are very slow, so I don't want to resend it. Every application she's tried (WinRAR, WinZip, and 7Zip) fails and gives some sort of "invalid archive format" error.

I had her do an MD5 checksum on the file and it matches mine. So, the likelihood of it being damaged during transmission is very small. I also successfully unzipped it on my end and used TeamViewer to try and get it unzipped on her end, just to make sure she wasn't doing anything wrong, she wasn't.

What could be the problem be UbuntuForums? Is there a difference in the way Windows and Linux handles zip files that is causing this problem?

---

### Post by NMFTM on 2011-03-01
Nobody?

---

### Post by Diametric on 2011-03-01
You might want to check on how big if a file winzip can accommodate...there might be a capacity issue there.

Worth checking out.

Cheers.

---

### Post by gmargo on 2011-03-01
What is the exact command you used to create the .zip file?

---

### Post by gmargo on 2011-03-01
Here is unzip for Windows:

[http://gnuwin32.sourceforge.net/packages/unzip.htm](http://gnuwin32.sourceforge.net/packages/unzip.htm)

---

### Post by NMFTM on 2011-03-01
> **Diametric said:**
> You might want to check on how big if a file winzip can accommodate...there might be a capacity issue there.
If she was just using Winzip then maybe. But this is every application she's tried (except Unzip below) that's been giving her similar problems.
> **gmargo said:**
> What is the exact command you used to create the .zip file?
I used the GUI. Right click -> compress -> selected .zip and set a password.
> **gmargo said:**
> Here is unzip for Windows:
[http://gnuwin32.sourceforge.net/packages/unzip.htm](http://gnuwin32.sourceforge.net/packages/unzip.htm)
Thanks, I'll have her try this. Although I'm not sure why this utility would succeed where 7Zip, Winzip, Winrar, and Window's built in unzip feature have failed.

---

### Post by philinux on 2011-03-01
When you say sent, what method. How is your friend downloading the file.

---

### Post by NMFTM on 2011-03-01
> **philinux said:**
> When you say sent, what method. How is your friend downloading the file.
TeamViewer's file transfer feature. But it shouldn't matter how I transferred the file because the checksums matched.

---

### Post by Vaphell on 2011-03-01
does some small zip file with dummy data for testing purposes get through successfully?
maybe there is some issue with encoding of the filenames - i can see utf8 vs win12xx causing some mess.
can you ask that other person to run livecd/usb to see if he/she manages to open zip in live session? If so, it would be possible to mount windows partition and drop the extracted data there.

---

### Post by gmargo on 2011-03-01
I zipped a file with a password, using Gnome/Nautilus, in the manner you described.  I had no problem reading it on a Windows 7 system (both 7-Zip and whatever the file manager uses.)

Perhaps it is due to the very large file size?  My test was small.  Is the destination machine 32-bit only?

---

### Post by NMFTM on 2011-03-03
> **Vaphell said:**
> does some small zip file with dummy data for testing purposes get through successfully
I did this with a 700KB zipped bmp image. It worked successfully with WinZip and 7Zip.
> **Vaphell said:**
> can you ask that other person to run livecd/usb to see if he/she manages to open zip in live session
I'll have to resend the file tonight because she needed the space. But I'll have her do that and see if it works.
> **gmargo said:**
> Perhaps it is due to the very large file size?  My test was small.  Is the destination machine 32-bit only?
Mine is Ubuntu64 and hers is Windows7 32. It could be the filesize, but I don't see why filesize would come into play. Zip is the most generic archive format for sending files.

---

### Post by NMFTM on 2011-03-05
I rezipped file with the exact same procedure I did previously, resent it, and it extracted successfully. No idea why it didn't work last time. Maybe it was one of those rare instances where the checksums matched even though it wasn't a 1:1 copy.

When she tried to extract the original file, I remember one of the error messaged mentioned "pointers" being incorrect, or something along those lines.

---

### Post by vancouverite on 2011-06-28
I don't think this is quite fixed yet.

I have sent a couple of different zip files with passwords in the last month to users on WinXP.  Both of them had a problem where the Explorer extraction wizard errored out with "File skipped unknown compression method"

I found that this could be avoided by having the receiver use 7zip, but that's not always an option.  

Is there a way to create a WinXP friendly zip file in Ubuntu?

---

### Post by rdd37 on 2012-03-06
Fwiw, I recently had an issue where a password-protected zip file created via the right-click -> 'Compress' option in Ubuntu would not open on a customer's Windows (unknown version) system ("Windows cannot complete the extraction. The destination file could not be created.").

I then created a password-protected zip file using the command line:
```
$ zip -e ./file.pdf.zip ./file.pdf
```

This seems to open Ok on their Windows system.

---

