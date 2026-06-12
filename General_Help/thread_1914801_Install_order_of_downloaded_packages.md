---
title: "Install order of downloaded packages"
date: 2012-01-25
forum: General Help
---

### Post by Jeff Root on 2012-01-25
Last year I downloaded and installed the "ugly" set of codec
plugins for 64-bit Maverick Meerkat.  I just reformatted the
drive and reinstalled Meerkat, and find that I do not have
instructions for the order in which the 16 parts need to be
installed.  I couldn't find it in a Google search, either.
 
flashplugin-installer_10.2.153.1ubuntu0.10.10.1_amd64.deb
ia32-libs_20090808ubuntu9_amd64.deb
lib32asound2_1.0.23-1ubuntu2.1_amd64.deb
lib32bz2-1.0_1.0.5-4ubuntu1_amd64.deb
lib32gcc1_1%3a4.5.1-7ubuntu2_amd64.deb
lib32ncurses5_5.7+20100626-0ubuntu1_amd64.deb
lib32stdc++6_4.5.1-7ubuntu2_amd64.deb
lib32v4l-0_0.6.4-1ubuntu1_amd64.deb
lib32z1_1%3a1.2.3.4.dfsg-3ubuntu1_amd64.deb
libasound2_1.0.23-1ubuntu2.1_amd64.deb
libc6_2.12.1-0ubuntu10.2_amd64.deb
libc6-dev_2.12.1-0ubuntu10.2_amd64.deb
libc6-i386_2.12.1-0ubuntu10.2_amd64.deb
libc-bin_2.12.1-0ubuntu10.2_amd64.deb
libc-dev-bin_2.12.1-0ubuntu10.2_amd64.deb
nspluginwrapper_1.2.2-0ubuntu7_amd64.deb
 
Where can I find the correct install order?
 
I also have this file:
 
gstreamer0.10-fluendo-plugins-mp3-partner_7.0.20100316-3_amd64.deb
 
Where does it fit in?
   
   -- Jeff, in Minneapolis

---

### Post by mastablasta on 2012-01-25
why not just install restricted extras package?

---

### Post by Jeff Root on 2012-01-25
> **mastablasta said:**
> 
why not just install restricted extras package?
How is it different from what I already have?
 
   -- Jeff, in Minneapolis

---

### Post by Jeff Root on 2012-01-26
I can't figure out what I did last time.  It worked before,
but now I can't get any of the packages to install.
 
   -- Jeff, in Minneapolis

---

### Post by mcduck on 2012-01-26
You don't need to think about the correct order yourself, dpkg will sort it out automatically if you just give it all the packages to install at the same time.

```
sudo dpkg -i package1.deb package2.deb package3.deb
```

or

```
sudo dpkg -i *.deb
```

Anyway, I'd recommend using apt-get/software center/synaptic instead of downloading packages manually. That will save you a lot of work, and also makes sure you get every package you need and that they are the latest available versions.

---

### Post by Jeff Root on 2012-01-26
I didn't download each package "manually", but I forget now
what I did.  I remember watching at least 15 packages download
one after another, with very little indication of how long it
was going to take.  I fouled up by not making a clear record
of what I did after that.
 
I'll try the terminal command.  Thanks!
 
   -- Jeff, in Minneapolis

---

### Post by Jeff Root on 2012-01-26
The terminal command "sudo dpkg -i *.deb" appears to have
worked okay.  I can now play MP3.  I didn't check before
installing whether I could play AVI video, but I can now.
I'm not sure I gained anything else, and with the huge
number of of files involved, it seems like it should play
a lot more than just MP3.  I still get a message that I
need some other files to play stored Flash video (which
Firefox plays just fine when I first download them).
 
Thank you.
 
   -- Jeff, in Minneapolis

---

