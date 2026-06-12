---
title: "and ubuntu, samba problems"
date: 2010-09-17
forum: General Help
---

### Post by deviator on 2010-09-17
i can't acces some folders on my samba share.

for example i set the Video folder to share and to allow creating or moving files. but inside the video folder i cant access some folders.

this only happened after i upgraded my samba client.

---

### Post by jv2112 on 2010-09-17
Are the permissions set for access in the sub directories ?

---

### Post by deviator on 2010-09-18
yes they are

---

### Post by lmarmisa on 2010-09-18
[FONT=Verdana]Have you any symbolic link to follow?. I got some problems with the option[/FONT][FONT=Verdana] **follow symlinks=yes** of the **/etc/samba/smb.cong** file after an upgrade of my samba server.[/FONT]

---

### Post by deviator on 2010-09-18
i don't quite understand that.

should i look for or change follow symlinks=yes ?

---

### Post by lmarmisa on 2010-09-18
This page explains some aspects of the symbolic links:

[http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html](http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html)

A symbolic link is defined with this command:

```

ln -s TARGET LINK_NAME

```

This post is related to the lucid problem with symlinks and samba:

[http://ww.ubuntuforums.org/showthread.php?t=1480858](http://ww.ubuntuforums.org/showthread.php?t=1480858)

Your problem will be probably different, but it sounds similar.

---

