---
title: "Complete newbie pleads for your help on aptitude"
date: 2010-12-19
forum: General Help
---

### Post by xr4ti on 2010-12-19
I installed 8.04 server (no gui) on my laptop (thinkpad x61).  Then got my wireless to working.  Now I want to do follow these instructions (below).  Problem is my first aptitude command says: Couldn't find any package whose name or description matched "xorg".  Then states exactly the same for gdm and xfce4.
 
[B]aptitude install xorg gdm xfce4
aptitude install <name of GUI browser, I use firefox>
aptitude install gedit
aptitude install gnome-terminal
and if you need it, 
aptitude install synaptic 
aptitude install xchat
shutdown -r now[/B]

---

### Post by cipherboy_loc on 2010-12-19
> **xr4ti said:**
> I installed 8.04 server (no gui) on my laptop (thinkpad x61).  Then got my wireless to working.  Now I want to do follow these instructions (below).  Problem is my first aptitude command says: Couldn't find any package whose name or description matched "xorg".  Then states exactly the same for gdm and xfce4.
 
[B]aptitude install xorg gdm xfce4
aptitude install <name of GUI browser, I use firefox>
aptitude install gedit
aptitude install gnome-terminal
and if you need it, 
aptitude install synaptic 
aptitude install xchat
shutdown -r now[/B]

What tutorial are you using. Oh, and BTW, you need to install 10.04. 8.04 is no longer supported. If you re-install using 10.04 (Lucid Lynx),  it should go much smoother. Also, why didn't you install the default Ubuntu or Xbuntu on you laptop?


Cipherboy

---

### Post by xr4ti on 2010-12-19
> **cipherboy_loc said:**
> What tutorial are you using. Oh, and BTW, you need to install 10.04. 8.04 is no longer supported. If you re-install using 10.04 (Lucid Lynx), it should go much smoother. Also, why didn't you install the default Ubuntu or Xbuntu on you laptop?
 
 
Cipherboy
 
 
Thanks but also no thanks.  I purposely installed 8.04 SERVER because it is needed for other software I want to install.

---

### Post by cipherboy_loc on 2010-12-19
> **xr4ti said:**
> Thanks but also no thanks.  I purposely installed 8.04 SERVER because it is needed for other software I want to install.

8.04 is no longer supported; the repositories have been taken down. You need to update to 10.04 (the LTS after 8.04) or 10.10 (the current release). I would recommend download and installing the 10.04 server edition, instead of an out of date server version.

Again, 8.04 is no longer supported, so you cannot install, nor update, etc, etc the software due to the fact that there are no repositories any longer.

Cipherboy

---

### Post by yeats on 2010-12-19
> 8.04 is no longer supported; the repositories have been taken down. You need to update to 10.04 (the LTS after 8.04) or 10.10 (the current release). I would recommend download and installing the 10.04 server edition, instead of an out of date server version.

Again, 8.04 is no longer supported, so you cannot install, nor update, etc, etc the software due to the fact that there are no repositories any longer.


Actually, this is incorrect.  8.04 is an LTS (long term support) release.  The desktop version will be supported until April 2011 and the server version until April 2013.

To the OP, you can do "apt-cache search <keyword>" to find exact package names.  You might do that with the packages you're having trouble with.  If nothing is coming up, can you post (within CODE tags) your /etc/apt/sources.list ?

---

### Post by cipherboy_loc on 2010-12-19
Thanks for correcting me about the dates. For some reason I was thinking that the last LTS's support ended just after (a month or two) the next LTS came out. 

OP, would you please post the output (again in code tags) of:
```
ls /etc/apt/sources.list.d/
```Thanks for correcting me chrissharp123,
Cipherboy

---

### Post by xr4ti on 2010-12-19
> **chrissharp123 said:**
> Actually, this is incorrect. 8.04 is an LTS (long term support) release. The desktop version will be supported until April 2011 and the server version until April 2013.
 
To the OP, you can do "apt-cache search <keyword>" to find exact package names. You might do that with the packages you're having trouble with. If nothing is coming up, can you post (within CODE tags) your /etc/apt/sources.list ?
 
 
```

 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

 
 

```

---

### Post by gmargo on 2010-12-19
"xorg" is the right name, and your /etc/apt/sources.list looks ok.  So you must just simply need an update.  Before you try anything else, do this:
```

aptitude update
aptitude -V -R full-upgrade

```That will update your current packages to the latest.  Then go ahead and install xorg and the other packages.

---

### Post by xr4ti on 2010-12-19
> **gmargo said:**
> "xorg" is the right name, and your /etc/apt/sources.list looks ok. So you must just simply need an update. Before you try anything else, do this:
```

aptitude update
aptitude -V -R full-upgrade

```That will update your current packages to the latest. Then go ahead and install xorg and the other packages.
 
gmargo, thanks.
the first command executed with success.
 
the second complains.  I dont think there is a -R flag.

---

### Post by gmargo on 2010-12-19
> **xr4ti said:**
> 
the second complains.  I dont think there is a -R flag.

What makes you think that?  What "complaint" did you get?  Did you check the man page?

---

