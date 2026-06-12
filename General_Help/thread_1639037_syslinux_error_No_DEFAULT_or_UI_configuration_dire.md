---
title: "syslinux error: No DEFAULT or UI configuration directive found."
date: 2010-12-06
forum: General Help
---

### Post by madmax.santana on 2010-12-06
I had a problem with 10.10 and I was mighty frustrated.
So I decided to go on and install 10.04 LTS, because it is LTS...
I created the live USB as directed on the Ubuntu download page. I download Universal USB Installer and it says USB created successfully.
However, when I boot from the USB the error comes up as mentioned in title...
The USB has no problems because I installed 10.10 last time from the very same USB. There's nothing wrong with the procedure because I am following the officially suggested method. Also, nothing wrong with partitions because one instance of Ubuntu is installed and was working fine until I tried to install video drivers (long story)...

Can anyone please look into this and suggest a solution or at least explain the problem to me?

---

### Post by tajiknomi on 2010-12-06
[SIZE=2]Go to usb .... ***syslinux***(directory) > open ***syslinux.conf***-file and search for "ui" word,remove "ui" from the beginning of line..just remove it...save it, and retry...[/SIZE]

---

### Post by tajiknomi on 2010-12-06
[SIZE=2]if the problem still not solved with that...then you need to rename the *isolinux.bin* and *isolinux.cfg* files in the * syslinux *folder to *syslinux.bin* and *syslinux.cfg**** .***[/SIZE]

---

### Post by madmax.santana on 2010-12-06
There is no syslinux folder in the usb!

---

### Post by AbuNusaibah on 2010-12-06
Hi there,
I have registered specifically to comment on your question because I was having the same problem, I believe. I came across your thread looking for a solution but then I have resolved the problem.

The ISO file I got from my wife had crc errors!! ( performed md5sum on the file to find out so)

I re-downloaded the ISO file and made sure it is a verbatimcopy by another md5sum.

By the way, in the damaged iso file based usb installation, the Syslinux folder did not have the sysXXX files but one text file.

This is not necessarily always the solution to this problem but this is what happened.My Ubuntu system is working and browsed the Internet via WiFi network. However, some error messages pop up like software center crashes, flash did not install etc.

Good luck,

Abu Nusaibah

---

### Post by madmax.santana on 2010-12-06
Hello Abu Nusaibah!
First of all, warm warm welcome to Ubuntu Forums


Second, I have already checked the md5 hash of my Ubuntu iso image. It was alright. But, just to make sure, I will download again and try.

---

### Post by madmax.santana on 2010-12-07
Nah. The new image has the same problem. There's no syslinux dir. :(

---

### Post by madmax.santana on 2010-12-07
Actually, as I see it, there is some problem with the 10.04 LTS image... Because when i write a 10.10 image it has a syslinux dir and works good... But the 10.04 LTS image lacks both the mentioned dir and functionality. I have tried to burn 10.04 LTS on the only CD that I had, but only to discover that it has the exact same problem...

Anyways, since my Ubuntu system is completely broke, I need to install a system. I wanted to install the LTS for two reasons. 1- that I believed that it will not have the same problem as 10.10... 2- that it is still supported...

But I have no other option than to install 10.10... :(

---

### Post by tajiknomi on 2010-12-11
[SIZE=2]I think the image you are using is bad-0ne, you can check it via ***MD5SUM > ***[/SIZE][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by madmax.santana on 2010-12-11
I have already checked it. The MD5SUM is okay!
Please read my previous replies before posting your comment in this thread.

---

### Post by mcanada on 2010-12-11
madmax.santana:

I just tried using Universal USB installer with Ubuntu 10.04.1 LTS today and I got the same issue you did. I then tried 10.10 and was successful using that image.

After thinking about it for a few minutes, I decided to try using the last option in the drop down list in Universal USB installer entitled "Try Some Other Live Linux ISO". This did the trick. I am using Universal USB Installer 1.8.1.7, so maybe it's an issue with this version.

I compared the logs between 10.10 and 10.04 and I noticed it omitted copying over the syslinux files.

Hope this helps you.

-Medardo

---

### Post by madmax.santana on 2010-12-12
> **mcanada said:**
> madmax.santana:

I just tried using Universal USB installer with Ubuntu 10.04.1 LTS today and I got the same issue you did. I then tried 10.10 and was successful using that image.

After thinking about it for a few minutes, I decided to try using the last option in the drop down list in Universal USB installer entitled "Try Some Other Live Linux ISO". This did the trick. I am using Universal USB Installer 1.8.1.7, so maybe it's an issue with this version.

I compared the logs between 10.10 and 10.04 and I noticed it omitted copying over the syslinux files.

Hope this helps you.

-Medardo
Thanks a lot.
This was the very same problem that I had. :)
Thanks for help. No i have an idea hat happens causing this error.
I could definitely have tried but now I am successfully running a 10.10. Cheerio! :)

---

### Post by PaC_1250 on 2010-12-30
> **mcanada said:**
> madmax.santana:

I just tried using Universal USB installer with Ubuntu 10.04.1 LTS today and I got the same issue you did. I then tried 10.10 and was successful using that image.

After thinking about it for a few minutes, I decided to try using the last option in the drop down list in Universal USB installer entitled "Try Some Other Live Linux ISO". This did the trick. I am using Universal USB Installer 1.8.1.7, so maybe it's an issue with this version.

I compared the logs between 10.10 and 10.04 and I noticed it omitted copying over the syslinux files.

Hope this helps you.

-Medardo

Thanks, I had the same problem when trying to install Ubuntu desktop 10.10 with Universal USB Installer **1.8.2.1** or Unetbootin.
But Universal USB Installer **1.8.1.7** with the same option worked fine for me. (I found it [here]("http://brainwavedesigncentral.net/mike/index.php?dir=usb-creator/&sort=name&order=asc"))

---

