---
title: "Ubuntu installation problems"
date: 2011-08-09
forum: General Help
---

### Post by new_b on 2011-08-09
Background info:
So I installed 11.04 32 bit and it messed my computer up therefore after trying everything I got rid of it, now I've been trying to install the 10.04 long support version from the official ubuntu website and it doesn't seem to be working. Neither the 32 bit version or the 64 bit. 

To convert the iso etc. etc. I used "Universal-USB-Installer-1.8.6.0" which is reccommended from the ubuntu website and it didn't work. So I tried "unetbootin-win-549" which a friend recommended to me - didn't work either. 

Main problem:
The menu loads up when I turn on the computer and whether I click on the install ubuntu, or try ubuntu from usb option - both go to the ubuntu screen where the dot's under "ubuntu" flash for about 2 minutes before taking me to a screen where the following message appears:

```

(initframs) unable to find a medium containing a live file system

```
And after about 5 seconds intervals, messages similar to this appear for about 7 or 8 times:
```

usb 1-3: device not accepting address 7. error -110
new high speed usb device using ehci_hcd and address 8

```
Each time they appear the parts which differ is the numbers from the text above i.e. usb 2-3....

---

### Post by zealibib slaughter on 2011-08-09
this could be caused by a bad iso or a failing usb drive.  Check the md5sum of the downloaded iso to verify it: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by new_b on 2011-08-09
Sorry man but that page is almost gibberish to me. My tech terminology isn't great. I see what you mean by the md5 though, it's a file I have on the usb. Can someone put it down for me in simple, clear instructions perhaps?

---

### Post by zealibib slaughter on 2011-08-09
are you using windows atm?

---

### Post by e79 on 2011-08-09
What **Zealib** is trying to say is that maybe your Ubuntu ISO (Live CD) is corrupted or a bad download. A simplier way would be to redownload Ubuntu and recreate your bootable USB stick. Make sure to ask the installer to format the USB stick prior to put Ubuntu on it.

If you still get the error I would suggest to try another USB stick if you can. If not, try 10.10 to see if the same problem occurs.

Hope this helps

---

### Post by new_b on 2011-08-09
Yes, I'm on windows 7 to be specific

And I did ask it to reformat the memory stick prior to extracting the iso and putting it on the memory stick but when I put version 11.04 on here I used this same memory stick so I'm not sure how it could be a problem for an older version :/

---

### Post by zealibib slaughter on 2011-08-09
The download may be corrupt.  It happens sometimes.  You can check the md5sum with winmd5sum found here: [http://www.nullriver.com/products/winmd5sum](http://www.nullriver.com/products/winmd5sum).  Once this program runs it will give you a bunch of numbers and letters.  Compare it to the md5sum you downloaded when you downloaded 10.04.  OR you can try downloading 10.04 again and remaking the usb disk.

---

### Post by new_b on 2011-08-09
I just used that program to firstly put in the 10.04 iso which generated an md5 sum. Then I put in the actual md5.txt file which was in my usb. 

The two sums generated were different. How can that be possible? I downloaded the 10.04 version twice and also converted it twice why has it not worked both times?

---

### Post by zealibib slaughter on 2011-08-09
It happens, are you downloading from ubuntu.com?  If you are it could be your internet connection.  Ive had iso's corrupted because of interuptions of my connection.

---

### Post by new_b on 2011-08-09
> **zealibib slaughter said:**
> It happens, are you downloading from ubuntu.com?  If you are it could be your internet connection.  Ive had iso's corrupted because of interuptions of my connection.

Ahh I see. Well I guess I'll try a few more times then! Will let you know how it goes

---

