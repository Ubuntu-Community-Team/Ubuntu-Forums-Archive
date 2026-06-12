---
title: "Can't play DVDs even with ubuntu-restricted-extras"
date: 2010-05-08
forum: General Help
---

### Post by ecujak on 2010-05-08
I have done this:
sudo aptitude install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh

I have followed all the steps here:

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)


I still cannot open dvds with anything. I can navigate and see the files, I just can't play or anything else.

---

### Post by shaka_zulu on 2010-05-08
Did you install w32codecs package?

---

### Post by ecujak on 2010-05-09
Yes, this is already installed too. This drive works just fine for Win7 and Vista. I have all the software for Linux that I could find.

---

### Post by 3rdalbum on 2010-05-09
Use VLC Media Player, not the default movie player on Ubuntu.

---

### Post by shaka_zulu on 2010-05-09
You will also need libdvdcss2 package. It is compulsory for playing encrypted DVD.

---

### Post by Dayofswords on 2010-05-09
> **shaka_zulu said:**
> You will also need libdvdcss2 package. It is compulsory for playing encrypted DVD.

this

[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29)

---

### Post by ecujak on 2010-05-09
> **shaka_zulu said:**
> You will also need libdvdcss2 package. It is compulsory for playing encrypted DVD.


> **Dayofswords said:**
> this

[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29)


I guess you didn't read the original post... thanks for trying.


$ sudo apt-get install libdvdcss2 
[sudo] password for ####: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.

---

### Post by MooPi on 2010-05-09
What player are you using ?

---

### Post by stoneage on 2010-05-09
> **ecujak said:**
> I have done this:
sudo aptitude install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh

I have followed all the steps here:

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)


I still cannot open dvds with anything. I can navigate and see the files, I just can't play or anything else.


So, maybe you could post up the errors you are getting......?

---

### Post by rmartinus on 2010-05-13
This worked for me:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html")

---

