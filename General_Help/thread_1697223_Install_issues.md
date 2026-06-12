---
title: "Install issues"
date: 2011-02-28
forum: General Help
---

### Post by bg4m3r on 2011-02-28
I am attempting to install Ubuntu 64-bit and it keeps failing. This is my first 64-bit system, and have not had problems with installing x86 Ubuntu in the past. When the full install failed, I tried installing it within Windows and that also failed. I've attached the log from that attempt in this post (had to trim it down to fit the file limit though). I don't know if these are the same errors I was getting on full install as I didn't write those errors down...I can try again and post them if needed though.

---

### Post by sikander3786 on 2011-02-28
Welcome to the forums :-)

I am not an expert with Wubi installs.

But with the full install, I suspect it is a disc/image issue rather than 64-bit itself. If your hardware is 64-bit capable, there shouldn't be any problems.

First of all, check your downloaded image against any possible defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, check the disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

If you need to re-download the image, using a torrent client minimizes the risk of data corruption. If you need to burn a new disc, burn at the lowest possible speed preferrably 4x.

Or burn a USB drive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html?showComment=1297175951702#c3100135703895167905](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html?showComment=1297175951702#c3100135703895167905)

Or if none of those helps, can you please explain what happens when you try to do a full install? Any error messages?

---

### Post by bg4m3r on 2011-03-14
I tried to check the disc for errors (I deleted the iso, so I couldn't check the hash) and got the same error as when I try to install:

Can not mount /dev/loop0 on //filesystem.squashfs
Input/output error

I'm running Win7 64-bit, so I definitely have a 64-bit system.

---

### Post by sikander3786 on 2011-03-15
Then the disc is corrupted. It is either the result of a bad burn or a corrupt image itself. You can download a new iso (using a torrent client reduces the risk of corruption) and then burn it to a disc at the _lowest_ possible speed.

---

### Post by bg4m3r on 2011-06-18
> **sikander3786 said:**
> Then the disc is corrupted. It is either the result of a bad burn or a corrupt image itself. You can download a new iso (using a torrent client reduces the risk of corruption) and then burn it to a disc at the _lowest_ possible speed.

yeah, that seems to have been exactly it...I re-downloaded and re-burnt, although IMGBurn ignored my speed settings for some reason? I set it to 1x, and it went and burnt at 16x anyway. O.o
Anyway, long story short (too late, I know :P), I'm posting this from my fresh Ubuntu x64 install! :)

The Oracle issue has also been figured...seems virtualization was disabled on the MoBo! /facepalm

Thanks for all the input everyone gave!

---

