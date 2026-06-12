---
title: "an error occurred while mounting /proc/bus/usb  press s to skip mounting or M form ma"
date: 2010-04-30
forum: General Help
---

### Post by autonomy on 2010-04-30
> an error occurred while mounting /proc/bus/usb

press s to skip  mounting or M for manual recoveryHello, I'm getting this error while booting.

This is the only other result I found: [http://babelfish.yahoo.com/translate_url?doit=done&tt=url&intl=1&fr=bf-home&trurl=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%3Ftopic%3D379424.0&lp=it_en&btnTrUrl=Translate]("http://babelfish.yahoo.com/translate_url?doit=done&tt=url&intl=1&fr=bf-home&trurl=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%3Ftopic%3D379424.0&lp=it_en&btnTrUrl=Translate")

It's translated from Italian.

---

### Post by bturig on 2010-04-30
I had same error after upgrading to Lucid from Karmic. My understanding of your link was that it discussed VirtualBox and the /etc/fstab file.

Under Karmic, I had modified my fstab file by adding " none /proc/bus/usb usbfs devgid=userid,devmode=664 0 0", in order to get the USB support to work with VirtualBox.

Now under Lucid, I have removed the line from fstab, rebooted, and now all is good.

see support link [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by autonomy on 2010-04-30
Yep, that worked. Thanks, it's kind of amusing that I read fstab as sources.list

---

### Post by jorisctn on 2010-05-01
Same problem here, solved by removing the extra line from /etc/fstab!
Thanks for posting :)

---

### Post by Blond on 2010-05-01
To bad. This didn't work for me.
My laptop couldn't start anymore. I even did not get the option to skip

:-(

---

### Post by daveespionage on 2010-05-01
Whew!  Thanks, that totally fixed it for me too.  I had forgotten about the usb hack for VirtualBox, even more confusing, the upgrade process looked like it removed VirtualBox.

---

### Post by ccrs8 on 2010-05-01
Commenting out that line fixed both my computers.  I remember doing that hack back in 9.04, but I actually reformatted both computers and clean installed 9.10 and VirtualBox shared USB devices out of the box then.  The VB install may have added that line automatically in later versions?  Who knows?

Even without commenting out that line, USB mounting both natively and within VirtualBox worked fine after upgrading from 9.10 to 10.04 despite getting this error message when booting.  The biggest concern was that if you type 'm' you get thrown in to a command prompt at root.  That gave me access to everything on the machine without typing any passwords.  Kind of scary.  Glad I got rid of that error message.

---

### Post by autonomy on 2010-05-01
> **Blond said:**
> To bad. This didn't work for me.
My laptop couldn't start anymore. I even did not get the option to skip

:-(
Intel 855? Try this: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Good point, ccrs8, and yeah, I used my USB in VirtualBox this morning.

---

### Post by OzzyFrank on 2010-05-06
> **Blond said:**
> To bad. This didn't work for me.
My laptop couldn't start anymore. I even did not get the option to skip
:-(

Did the fix not work (or make things worse, if I read it right), or you just can't get to the desktop to implement it? If it's the latter, get to a recovery command line and:

sudo nano /etc/fstab

---

### Post by bsusim on 2011-05-05
Hi
I'm using ubuntu 10.10 (maverick). I just installed virtualBox (oracle) and my usb devices is gray in the virtualBox. I edited the /lib/init/fstab file (none  /proc/bus/usb usbfs .....) .
but my system don't have /proc/bus/usb. I fond that I need to edit the file 
/etc/init.d/mountdevsubfs.sh this file is also missing from my system.
Please help.

---

