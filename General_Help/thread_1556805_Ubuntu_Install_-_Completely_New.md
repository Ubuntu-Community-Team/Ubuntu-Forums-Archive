---
title: "Ubuntu Install - Completely New"
date: 2010-08-19
forum: General Help
---

### Post by lostkid on 2010-08-19
Hello, I'm having some trouble installing Ubuntu 10.04. I am completely new to Ubuntu, and Linux for that matter so if you do take the time to help me please understand my lack of knowledge. I'm also not very adept with computers in general so please try to explain things as simply as possible.

What I am trying to do is completely wipe all things on my computer and install Ubuntu. I have followed the instructions from Ubuntu's homepage on how to download the ISO, and ran their program to put it onto a portable USB device. Through doing all of this, I receive no error messages. Then it tells me to change the BIOS to boot from USB, so I did that. I've successfully accessed the install menu and filled in all the information requested (i.e. computer name, account name, etc.). I select that I want to delete the current partitions and use only Ubuntu. It starts to install, but at 67%, while copying files, I receive an error.

This error is:
> 
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment


I've tried to fix it, but truly have no clue where to begin, perhaps someone can give me some insight.

---

### Post by Quackers on 2010-08-19
I haven't done a usb install but it sounds possible that you may have suffered a bad write to your usb device. Can you burn the iso file to a disc and try that?

---

### Post by lostkid on 2010-08-19
Unfortunately, it has to be USB install. :/

---

### Post by Quackers on 2010-08-19
Can you check the md5 checksum of the downloaded file? Make sure it's what it should be. That would rule out a bad download. If that's ok you could try to burn it to usb again.

---

### Post by lostkid on 2010-08-19
Ahh, I've wiped my hard drive of my previous OS so I'll have to redownload on a seperate computer. Give me a few minutes. How do you check the md5 checksum? I'm not sure what that is.

---

### Post by NCLI on 2010-08-19
Here's [a guide]("https://help.ubuntu.com/community/HowToMD5SUM") to checking the MD5 checksum.

If that doesn't show any problems, it sounds like something might be wrong with your HDD. Is this a new computer?

---

### Post by lostkid on 2010-08-19
Relatively new... I haven't had any indications that there are any issues with the HDD. Any way I can check that?

The ISO I had did not match. Attempting to download again... :/ Maybe that was the issue.

---

### Post by Quackers on 2010-08-20
There is usually a md5 checksum shown on the website you download an iso file from. It is a multi-character string (loads of them).
There is a md5 checker for windows - I think it's called md5 or md5 check. It's a very small program and it runs very quickly. Running it is quite straightforward. It would have to be - I managed it!

---

### Post by lostkid on 2010-08-20
After trying to redownload the ISO I realize that I am downloading "10.04.1", the name does not even match. I have gotten the same md5 both times I download this file but there is nothing to compare it to as the most current on the hash list is "10.04". Why is mine 10.04.1? I downloaded it directly from the Ubuntu website...

---

### Post by Quackers on 2010-08-20
10.04.1 only came out the other day. If you've downloaded it give it a try.

---

### Post by lostkid on 2010-08-20
Because it is relatively new, how can I check the correct md5 checksum?

---

### Post by lostkid on 2010-08-20
Even after reinstalling the ISO, putting it on my USB again, and attempting to install... it fails at 60%.

---

### Post by ScarletWyvern on 2010-08-20
Do you have another USB drive you could try it with?

---

### Post by lostkid on 2010-08-20
No. :/ I guess I'll go back to Windows. This was a nice experience though. :lolflag:

---

### Post by lostkid on 2010-08-20
I don't want to give up quite yet. Anyone with a working version of 10.04.1 willing to post their md5 so I can compare? Also... how else can I troubleshoot to find the problem?

---

### Post by john newbuntu on 2010-08-20
MD5sums are available at:
[http://releases.ubuntu.com/10.04.1/MD5SUMS](http://releases.ubuntu.com/10.04.1/MD5SUMS)

Your error seems to be similar to memory errors described in:
[https://bugs.launchpad.net/ubuntu/+bug/245794](https://bugs.launchpad.net/ubuntu/+bug/245794)
Please do a memory test (memtest86) from the liveUSB and see if it is ok.

---

### Post by lapdog on 2010-08-21
> **john newbuntu said:**
> MD5sums are available at:
[http://releases.ubuntu.com/10.04.1/MD5SUMS](http://releases.ubuntu.com/10.04.1/MD5SUMS)


Thanks John, I was looking for the 10.04.1 md5sum hash numbers!  :)

When I:
```
md5sum ubuntu-10.04.1-desktop-i386.iso | grep "9a95ed6f6ec38fb58c446dba1add6a08  *ubuntu-10.04.1-desktop-i386.iso"
```

I get back the hash number and file name, so I think I'm ok re md5sums.  To use this code, be sure to have 2 spaces between the hash number and file name; that's the way md5sum apparently outputs.

---

### Post by lapdog on 2010-08-21
As I was looking for the 10.04.1 md5sum hash numbers, I checked those that are on the live CD I burned, in its root dir in md5sum.txt.  I came up with:

```
awk '{print "/media/cdrom/" $2}' /media/cdrom/md5sum.txt | xargs md5sum | awk '{gsub("/media/cdrom/", "");print}' | diff /media/cdrom/md5sum.txt -
```

AWK prints the filenames (which are in column 2) from md5sum.txt on the CD (which is mounted) and prepends the path to the CD.  md5sum is called for each file.  The results go to AWK again--gotta love AWK--where the CD path is removed (gsub) and the line printed.  Finally diff compares the results with the hash numbers on the CD.  If I wrote this correctly and there is no output, that means there are no differences and the hash numbers are correct.

It took about 3 minutes to run the first time on my AMD Phenom X3 w/ HP DVD 1035 CD/DVD drive.

If you have a different path to your CD drive, you'll need to replace the path in the above command in the 4 spots.  Hope this helps some folks...

---

### Post by BigCityCat on 2010-08-21
I don't know much about it but here are a few links that might help.

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

