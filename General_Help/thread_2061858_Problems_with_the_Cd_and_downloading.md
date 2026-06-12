---
title: "Problems with the Cd and downloading"
date: 2012-09-23
forum: General Help
---

### Post by contranauta on 2012-09-23
Hello to all,

i am a new Ubuntue user since one month, and I have to say that  I really like much more than the system I was using before!!, much easier, and colourfull..

I&#7743; trying my best for do the upgrades but allways become this message:

W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Also Im not  able for see original DVDs on it, any ideas?

Thanx  to all

Best regards
):P

---

### Post by Polydorus on 2012-09-23
I'm having similar problems with DVDs.  Hope you get some helpful answers.

---

### Post by Bashing-om on 2012-09-23
I think the d/l from cd option has been turned on:
 check:
   Launcher=>USC=>task bar menu=>edit=>software sources: Under ubuntu software: ensure the check box for installable from CD-ROM/DVD is NOT checked.

also: Look in sources.list and make sure there are no corresponding lines for cd or dvd:
dash=>search term sources --->click on sources.list icon (opens the file in the file manager).

[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by varunendra on 2012-09-24
Please disable the CD-ROM repository as Bashing-om said above (just to elaborate, by 'USC' he means- 'Ubuntu Software Center'), or by manually editing the "sources.list" file :
(just copy-paste and enter the following in a terminal)
```
gksu gedit /etc/apt/sources.list
```
add a '#' before each line that starts with "deb cdrom:", so that it looks like..
> # deb cdrom:....
Proofread, save and close. Then retry updating, you won't get the error again.

By the way, for playing DVDs, you need some restricted codecs. An easier way is to just install VLC and use it for playing contents that require restricted codecs:
```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by contranauta on 2012-10-07
> **varunendra said:**
> Please disable the CD-ROM repository as Bashing-om said above (just to elaborate, by 'USC' he means- 'Ubuntu Software Center'), or by manually editing the "sources.list" file :
(just copy-paste and enter the following in a terminal)
```
gksu gedit /etc/apt/sources.list
```add a '#' before each line that starts with "deb cdrom:", so that it looks like..

Proofread, save and close. Then retry updating, you won't get the error again.

By the way, for playing DVDs, you need some restricted codecs. An easier way is to just install VLC and use it for playing contents that require restricted codecs:
```
sudo apt-get update
sudo apt-get install vlc
```

Thanx, very usefull... I LOVE MY UBUNTUUUUUUUUUUUUUU YI HAAAAAAAAAWWW:guitar:

---

