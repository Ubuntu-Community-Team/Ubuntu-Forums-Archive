---
title: "Cannot play dvd"
date: 2010-02-04
forum: General Help
---

### Post by schwabdale on 2010-02-04
**Can't play DVD** 			
 			 			 		   		 		 		Please help. I cannot play a dvd in Movie player, or VLC. I get gstreamer plugin error in movie player, and all kinds of errors in VLC. I tried to do this [https://help.ubuntu.com/community/Me...crypted%20DVDs]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs")

Thanks in advance

---

### Post by Twitch6000 on 2010-02-04
> **schwabdale said:**
> **Can't play DVD** 			
 			 			 		   		 		 		Please help. I cannot play a dvd in Movie player, or VLC. I get gstreamer plugin error in movie player, and all kinds of errors in VLC. I tried to do this [https://help.ubuntu.com/community/Me...crypted%20DVDs]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs")

Thanks in advance

Sorry you have to deal with this... 

Anyways here is how to fix the problem.

First install the restricted extra packages.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Follow that guide.

After installing the repo open aa terminal and type sudo-apt-get libdvdcss.

This should fix your problem.

Edit: oh your could just install the package manually via putting this in a terminal -

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

---

### Post by Leppie on 2010-02-04
did you run the following script:
```
/usr/share/doc/libdvdread4/install-css.sh
```

you can run it like this:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by schwabdale on 2010-02-05
Thanks, I must have missed something the first time.

---

### Post by Leppie on 2010-02-05
> **schwabdale said:**
> Thanks, I must have missed something the first time.
so it's working now?

if this issue is solved, use the thread tools to set it to solve.

---

### Post by schwabdale on 2010-02-05
Problem solved! Thanks

---

### Post by Leppie on 2010-02-05
> **schwabdale said:**
> Problem solved! Thanks
you're welcome.

use the thread tools to set this to solve.

---

