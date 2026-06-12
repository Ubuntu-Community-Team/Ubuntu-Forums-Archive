---
title: "Ipod Touch recognized as Normal Ipod?"
date: 2010-05-24
forum: General Help
---

### Post by jephrei on 2010-05-24
First, My ipod touch is shown on my desktop as a regular ipod. through the screenshots of other folks i've seen it showing as an iphone/ipod touch icon.

Second, I'm not exactly sure how to manage it. sbmanager, ideviceinstaller, backups and the like. I have done a new install of Ubuntu Lucid Lynx 10.04. I had thought everything worked "out of the box" from what others have said. is here anything i have to do on top of a new ubuntu install?

i'm assuming these 2 issues may be related. any help is obvioudly greaaaaatly appreciated as i've already made the choice to ditch windows/itunes all together.

---

### Post by itxaka on 2010-05-24
I can't comment on the default libimobiledevice library coming on 10.04.

What I can tell you is that in order to gain all functionality I had to compile the latest version available on their webpage [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/) and some other dependencies like usbmuxd.

I can now use Sbmanager to manage the springboard, rhythmbox to manage the music and backup the device with idevicebackup.

Also, I get the iphone icon when connecting it.

What does ideviceinfo shows when you run it with the touch connected?

---

### Post by jephrei on 2010-05-24
ideviceinfo just says "ipod" for DeviceClass. what else are you looking for?i have everything updated and all the supposed required stuff is already installed (libimobiledevice, ifuse, libplist and usbmuxd).

---

### Post by jephrei on 2010-05-24
I can probably also summarize all this in one question: can i manage an ipod touch (music, photos, and especially apps and backup) with lucid lynx out of the box or do i have to compile/install some other packages?

---

### Post by itxaka on 2010-05-24
> **jephrei said:**
> I can probably also summarize all this in one question: can i manage an ipod touch (music, photos, and especially apps and backup) with lucid lynx out of the box or do i have to compile/install some other packages?

Music and photos should work out of the box with ubuntu 10.04.

Backups are done via terminal with idevicebackup.

Apps are done via terminal too, with ideviceinstall.

Springboard is managed via sbmanager [http://cgit.sukimashita.com/sbmanager.git/](http://cgit.sukimashita.com/sbmanager.git/), you will have to compile it from git.

ideviceinfo identifies perfectly my iphone 3gs so maybe the problem is that the libimobiledevice version on the repositories is too old to recognize it properly?
Ubuntu packages show me that the repository version is 0.9.7-1 while the latest version is 1.0.1

---

### Post by jephrei on 2010-05-24
AAAH. okay. never compiled anything before and would know where to start but there's gotta be a "how to" somewhere. i'll try these mini adventures out and let you (and whoever else has the same problem) what happens. thanks itxaka!

---

### Post by itxaka on 2010-05-24
> **jephrei said:**
> AAAH. okay. never compiled anything before and would know where to start but there's gotta be a "how to" somewhere. i'll try these mini adventures out and let you (and whoever else has the same problem) what happens. thanks itxaka!

It is pretty easy.

1)get all the dependencies
```
sudo apt-get install build-essential automake autoconf libtool libgnutls-dev libglib2.0-dev libxml2-dev libreadline5-dev libplist-dev libplist++-dev
```

2)download the source code with git or a tar.gz (depending on what do you want to compile, sbmanager->git , libimobiledevice->git or .tar.gz file

3)compile it with the awesome 3 step course(./configure,make, sudo make install)

4)?????

5)PROFIT!

:P

Let me know if you need more info :)

---

### Post by jephrei on 2010-05-24
i didn't get your reply until now, but i found the link below based on what you said earlier...wow! a COMPLETE tutorial already right here...at your friendly ubuntu forums!

[http://ubuntuforums.org/showthread.php?t=1471018](http://ubuntuforums.org/showthread.php?t=1471018)

thanks for your help itxaka!

---

