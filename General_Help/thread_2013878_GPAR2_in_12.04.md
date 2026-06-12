---
title: "GPAR2 in 12.04"
date: 2012-07-01
forum: General Help
---

### Post by bvt on 2012-07-01
hello,
where would I get GPAR2 for 12.04? apps.ubuntu.org only has it for 11.10.  Its a great utility.

---

### Post by ubudog on 2012-07-01
You could download the Natty .deb and install it:
[http://packages.ubuntu.com/natty/gpar2#pdownload](http://packages.ubuntu.com/natty/gpar2#pdownload)

Once you have it downloaded, run the following to install it: 
```
sudo dpkg -i **pathtodownloadeddeb.deb**
```

Replace the bold text with the location of your downloaded .deb.

Best,
ubudog

---

### Post by rai4shu2 on 2012-07-01
Just be aware that gpar2 has not been looked at by devs for over 2 years.

See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=564996](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=564996)

---

### Post by bvt on 2012-07-01
It worked fine.  didn't see libpar2 or the gnome-desktop-data (were installed anyway).  GPAR2 is much better than PyPar2

thanks for the help.

---

### Post by ubudog on 2012-07-01
> **bvt said:**
> It worked fine.  didn't see libpar2 or the gnome-desktop-data (were installed anyway).  GPAR2 is much better than PyPar2

thanks for the help.

Great!  Be sure to mark the thread as solved under "Thread Tools".  :)

---

