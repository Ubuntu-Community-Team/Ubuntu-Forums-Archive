---
title: "DVD not readable with 10.04 was readable with 9.04"
date: 2010-08-06
forum: General Help
---

### Post by DrScum on 2010-08-06
I have a DVD which I can open and play on a machine running 9.04 but I can't get to open and play it on a machine running 10.04.

How can I diagnose and prefereably fix the problem?

---

### Post by dino99 on 2010-08-06
is ubuntu-restricted-extras installed ?

sudo apt-get update
sudo apt-get install -f

---

### Post by utilitytrack on 2010-08-06
Which players you use? And post here output of (from both 9.04 and 10.04)

```
ls -l /dev/dvd*
```

---

### Post by DrScum on 2010-08-06
I believe restricted extras is installed

here the output for dvd players

lrwxrwxrwx 1 root root 3 2010-08-06 11:49 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-08-06 11:49 /dev/dvdrw -> sr0

---

### Post by DrScum on 2010-08-06
just checked in package manager: ubuntu restricted extras is installed

---

### Post by lucasart on 2010-08-06
> **DrScum said:**
> I have a DVD which I can open and play on a machine running 9.04 but I can't get to open and play it on a machine running 10.04.

How can I diagnose and prefereably fix the problem?

Install the following packages (those are codecs)

```

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

```

And then run the script which installs the CSS decoder

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

Just play with Totem (right click the DVD and click play or sth like that).

---

### Post by DrScum on 2010-08-06
did what you suggested lucasart:
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.

the css decoder was installed without apparent error messages

the dvd is still not available. when I put it in the drive it does not get mounted (at least I don't see it anywhere in the file manager)

---

### Post by dino99 on 2010-08-06
[http://www.google.com/search?as_q=dvd%2Bnot%2Brecognised%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=dvd%2Bnot%2Brecognised%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by LowSky on 2010-08-06
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get install libdvdcss2 w32codecs
```

---

### Post by DrScum on 2010-08-06
did what you suggested, low sky, the dvd is still not available.

Here is a new puzzle (posted a new thread about this)

I think the problem is not caused by lack of codecs or such things, I think it's the drive. 

When I insert a CD at startup, the CD is available in the file manager and readable. As soon as I instert a DVD the drive is no longer available in the file manager. When I reinsert the CD after that it doesn't become available. I have no idea how to solve this problem.

If I reboot with nothing in the drive, the drive is available in the file manager.

Inserting a commercial movie DVD works fine it is mounted and can be played in VLC movie player.

However, after inserting this "special" dvd the drive is no longer available

---

### Post by Pykler on 2010-12-30
> **DrScum said:**
> 
When I insert a CD at startup, the CD is available in the file manager and readable. As soon as I instert a DVD the drive is no longer available in the file manager. When I reinsert the CD after that it doesn't become available. I have no idea how to solve this problem.


I have the exact same issue! I am not sure about other DVD's but the one I am trying now is doing exactly that. If you run totem as root it works but therwise unreadable.

---

