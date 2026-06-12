---
title: "I cannot play any DVDs."
date: 2009-09-10
forum: General Help
---

### Post by paulmmj on 2009-09-10
Ubuntu Forums,

Netflix came in the mail. I just got Ubuntu. Throw it in the machine, it's a no go. Movie Player says I don't have permission, as well as some other media player I just downloaded. Don't know what to do. But in the meantime, I'll watch it on my Mac. Any clues as to how to amend of bypass the problem? I have no qualms with bypassing DRM or other "illegal" ways of using data (pssh, yeah, cause I'm really a criminal...)

Thanks,
Paul.

---

### Post by Efwis on 2009-09-10
did you install the w32codecs package?

```
sudo apt-get install w32codecs
```

---

### Post by paulmmj on 2009-09-10
Thank you for your help, but I am afraid this error came up:

```
paul******@paul******-desktop:~$ sudo apt-get install w32codecs
[sudo] password for paul******: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
paul******@paul******-desktop:~$ 

```

---

### Post by jmszr on 2009-09-10
paulmmj,

If you haven't already, you will need to install Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

---

### Post by StuartN on 2009-09-10
I think gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse do DVDs. I vaguely recall that mplayer now asks to install them the first time it finds encrypted content.

---

### Post by Maheriano on 2009-09-10
Medibuntu is definitely what you need as posted earlier. I just did this fix last week.

---

### Post by paulmmj on 2009-09-10
Hello again,

Thank you for the advice, but I have installed Medibuntu to no avail. I did not remove the "not-free" section, and I rebooted after install. But, apparently, I still don't "have permission." But, upon reviewing the documentation on Medibuntu, I am glad you pointed me towards it. A few usefull things seem to be packaged with it and it should probably be better advertised.

WIth thanks for all help,
Paul.

---

### Post by paulmmj on 2009-09-10
Sorry to double post, but it would appear as if my Movie Player plays NOTHING. It will not play YouTube because I don't have "permission." I hope some light can be shed on this unfortunate situation...

---

### Post by jmszr on 2009-09-10
paulmmj,

I'm not sure about the "permission" problem, but make sure you have this installed:```
sudo apt-get install ubuntu-restricted-extras
```

also you should try the VLC media player:```
sudo apt-get install vlc
```

If you are feeling adventurous, and want the newest version of VLC: [http://www.ubuntugeek.com/howto-install-vlc-media-player-1-0-0-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-vlc-media-player-1-0-0-in-ubuntu.html) .

---

### Post by fooman on 2009-09-10
for dvds...if you have added the medibuntu repos as in the link above, then open a terminal and run this command:

```
sudo apt-get install libdvdcss2
```as far as youtube goes,  you need to install flash.  installing the ubuntu-restricted-extras package will take care of that...  again,  open a terminal and run this:

```
sudo apt-get install ubuntu-restricted-extras
```hope that helps.

---

### Post by Earl_Maroon on 2009-09-10
Exactly as the poster above me said, you almost certainly are lacking libdvdcss2.

---

### Post by paulmmj on 2009-09-10
Joy to the world! Excellent! Thank you SO MUCH. I've asked for help on multiple occasions, and on all occasions you've solved my issues! It would appear you believe VLC is superior to Video Player, so I will investigate surely, but for now, it's movie time.

Thanks once again,
Paul.

---

### Post by Maheriano on 2009-09-11
> **paulmmj said:**
> It would appear you believe VLC is superior to Video Player
It is. I even configured mine for AC3 passthrough to give me Dolby Digital and DTS from my DVD. Glad you got it working.

---

### Post by tweener on 2010-01-17
> It is. I even configured mine for AC3 passthrough to give me Dolby Digital and DTS from my DVD. Glad you got it working.

sorry for the nob question but, how did you do this? #-o

---

### Post by Maheriano on 2010-01-17
> **tweener said:**
> sorry for the nob question but, how did you do this? #-o
You have to mess with the settings in System - Preferences - Sound as well as Sound Preferences and finally the VLC preferences. That AC3 encrypted signal needs to make it all the way to your receiver without being decrypted by anything along the way.

---

### Post by tweener on 2010-01-17
thanks man.... i will try l8r

---

