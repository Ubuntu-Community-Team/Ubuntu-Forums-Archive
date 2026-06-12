---
title: "Printing with Samsung CLP310N"
date: 2009-11-19
forum: General Help
---

### Post by SteveHillier on 2009-11-19
Hi guys,
Has anyone had any issues with printing to a Samsumg CLP310N Laser printer.
This is the first Ubuntu release where printing has not behaved like a goodun.
This is a network printer and 9.10 has seen it and loaded it, however when I try to print it comes up with 'Please use the correct driver for this printer' message.
I have tried the Unified Linux Driver from the Samsung website but cannot get it installed.
Any clues anyone?

Cheers
Steve

---

### Post by SteveHillier on 2009-12-07
I have noticed this before - most times when I post with a problem I get lots of readers but not many people with the same problem.

I am not complaining - just making a comment.

However.....

I have a solution.

I downloaded the Unified Printer driver from the Samsung website
```
http://www.samsung.com/my/consumer/detail/support.do?group=pc-peripherals-printer&type=printer-multifunction&subtype=colour-laser-printer&model_nm=CLP-310N&disp_nm=CLP-310N&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010200&model_cd=CLP-310N/XSS&menu=download
```
This downloads as a cdroot file in which there is an install script.

To run this script I logged on as root, moved the download directory to a new directory in /etc/samsung.  I changed the ownership of the directory and all the child folders and files using ```
chown -vR root:root /etc/samsung/cdroot
```
I then used shell to run the installer.  This put on the system a file called Samsung Unified Driver Configurator.

I ran this configurator.  I had to tell it to find the printer on the network (192.168.0.55 in my case) and then configured it all.

Ran test print - all OK.  Have now logged back on as my normal user and checked and everything seems fine.

I shall now close this thread.  If anyone needs to know more (and I don't know if I have done this in the recognised proper fashion but it works) then feel free to email me.

Thanks to everyone interested enough to have viewed the initial post.

---

