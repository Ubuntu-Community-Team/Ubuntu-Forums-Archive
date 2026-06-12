---
title: "Playing DVD movie"
date: 2010-07-04
forum: General Help
---

### Post by jereece on 2010-07-04
Does Ubuntu not support playing DVD movies?  The default Movie Player that comes with Ubuntu won't.  I downloaded and installed VLC movie player then set this as the default for DVD Video in File Manager Preferences.  However VLC won't play DVD movies either. I even downloaded and installed K-lite Codec Pack in Wine and set that as the default.  In Windows K-lite will play anything but in Ubuntu it won't play DVD movies either.

Any suggestions?

Thanks,
Jim

---

### Post by jmszr on 2010-07-04
jreece,

This will take care of DVD's: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) . You might want to install Medibuntu, though. It will take care of DVD's plus more: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

Edit: If you decide to install Medibuntu be sure and install libdvdcss2 as part of it.

---

### Post by jereece on 2010-07-04
I installed both Restricted Formats and Mediubuntu, then rebooted.  Still won't play DVD movies.

---

### Post by jereece on 2010-07-14
Still no resolution.  I did this on a second computer and got the same results.  It does not work.

---

### Post by fooman on 2010-07-14
have you tried running the following command in a terminal?

```
sudo apt-get install libdvdcss2
```

---

### Post by philinux on 2010-07-14
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by CoolJohnB on 2010-07-14
I installed Gnome Mplayer from the Ubuntu Software Centre, had to make some minor adjustments in preferences and it plays DVD's fine, no problem. Suggest you give it a try and see if it works for you.

---

### Post by Zorgoth on 2010-07-14
Surely libdvdcss2 is not in the repository?  You either need to install libdvdcss2, which in some sense may be illegal in the US, but is not in real sense immoral and for which you will not be prosecuted or anything, or you can buy the Fluendo DVD stuff for about $30 if you are queasy about the digital millenium copyright act.

Your problem is probably that you cannot read encrpyted DVDs.  libdvdcss2 breaks the encryption while Fluendo handles it the way you are supposed to.

---

### Post by louis--taylor on 2010-07-14
I got it working by enabling either the multiverse, restricted or partner repositories, I can't remember which and then running:

```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```I think this has been mentioned above, but I thought I might as well repeat it :)

EDIT: Hey [Zorgoth]("http://ubuntuforums.org/member.php?u=656471")! you're from Cambridge too!

---

### Post by nmaster on 2010-07-14
> **jereece said:**
> It does not work.

you say this quite a bit.  is there an error message or is the playback  just of very poor quality? if the playback is of poor quality, then it is an issue with your graphics card.  if this is the case, you'll need to open up another thread and/or search for other solutions.  the dvd might just be revealing a different problem

---

### Post by Zorgoth on 2010-07-14
Yay for cambridge!  Although I'm in Virginia right now.  But I'll be in Cambridge again soon enough.  Do you live there or are you a student?

---

### Post by louis--taylor on 2010-07-14
I live here (Well, just outside in Willingham). Yourself?

---

### Post by Zorgoth on 2010-07-14
I'm an undergrad at Churchill college; I'm orginally from America

---

### Post by jereece on 2010-07-16
> **fooman said:**
> have you tried running the following command in a terminal?

```
sudo apt-get install libdvdcss2
```

Ubuntu says > Package libdvdcss2 is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source

---

### Post by jereece on 2010-07-16
> **neal.m.master said:**
> you say this quite a bit.  is there an error message or is the playback  just of very poor quality? if the playback is of poor quality, then it is an issue with your graphics card.  if this is the case, you'll need to open up another thread and/or search for other solutions.  the dvd might just be revealing a different problem

There is no playback at all.  I think it say something like can't find resource.  It's not the DVD because it plays fine on Windows.

---

### Post by jereece on 2010-07-16
> **CoolJohnB said:**
> I installed Gnome Mplayer from the Ubuntu Software Centre, had to make some minor adjustments in preferences and it plays DVD's fine, no problem. Suggest you give it a try and see if it works for you.


I installed Gnome MPlayer.  When it tries to open a DVD, it says > Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

---

### Post by Zorgoth on 2010-07-16
As I said, Ubuntu does not supply libdvdcss2 from the repository (for legal reasons).  However if you google it you should easily find a libdvdcss2.deb for Ubuntu.

---

### Post by jmszr on 2010-07-16
jereece,

Under System > Administration > Software Sources > Ubuntu Software do you have restricted and multiverse enabled (checkmarked)? If not, please do and then try installing libdvdcss2 again.

@Zorgoth: You are correct that Ubuntu doesn't supply libdvdcss2 but Medibuntu (which jereece has already installed) does and so it should be available for installation.

@jereece: Sorry, forgot to tell you to run:```
sudo apt-get update
```

that will update the source list - then install libdvdcss2.

---

### Post by 3rdalbum on 2010-07-16
If the Medibuntu repository is enabled, and you've updated the package list ('sudo apt-get update') then libdvdcss2 is in the repositories and you can use VLC to read DVDs.

---

