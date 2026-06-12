---
title: "Help installing Handbreak on 11.10"
date: 2011-10-17
forum: General Help
---

### Post by newellj79 on 2011-10-17
I'm having trouble installing handbreak on 11.10.  I've added the ppa thru terminal and the two entries in synaptic package (the natty entries because there are none for 11.10).  When i try to install all the related stuff in synaptic I get:

handbrake-gtk:i386:
 Depends: libbz2-1.0 but it is not going to be installed
 Depends: libgstreamer-plugins-base0.10-0 but it is not going to be installed
 Depends: libgstreamer0.10-0 but it is not going to be installed
 Depends: libnotify1 (>=0.5.0) but it is not installable
 Depends: libnotify1-gtk2.10  but it is not installable
 Depends: libwebkitgtk-1.0-0 but it is not going to be installed

and 
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory

and

fix broken packages

please help!

---

### Post by newellj79 on 2011-10-17
OK. So i downloaded the .deb package but when i try to install it thru ubuntu software center it says:

dependency is not satisfiable libnotify1 (>=0.5.0)

i think if i can get this fixed it would install.  any help?

---

### Post by rkillcrazy on 2011-10-20
> **newellj79 said:**
> OK. So i downloaded the .deb package but when i try to install it thru ubuntu software center it says:

dependency is not satisfiable libnotify1 (>=0.5.0)

i think if i can get this fixed it would install.  any help?

Not sure if this will help but it did help me get Google Chrome installed when it failed on 11.10.

Try installing the deb via the CLI...  Open a terminal window and run the following command.
```

sudo dpkg -i path/to/your/deb/file/here.deb

```

**_Hint_: if you have terminal running and you have your Nautilus open with the deb file sitting there, you can type "sudo dpkg -i " into the terminal window and then just drag/drop the deb from the Nautilus window into the terminal window.  That will put the full path there for you and save you some typing.**

If it still fails immediately run: ```
sudo apt-get install -f
```

What this will attempt to do is fix dependencies of the previously failed installation.

Good luck.  It's helped me out of a few jams but it's not bomb-proof.


You can also try the following which adds the "snapshots" repository which aren't generally considered stabled builds.
```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk

```

---

### Post by devisenhandel on 2011-10-20
> **newellj79 said:**
> OK. So i downloaded the .deb package but when i try to install it thru ubuntu software center it says:

dependency is not satisfiable libnotify1 (>=0.5.0)

i think if i can get this fixed it would install.  any help?

Thanks for sharing this help.
I was also searching this since many days.


-------------------


[B][türkçe forex ]("http://www.xn--trkeforex-s3a2u.com/")
[devisenhandel für anfänger]("http://www.xn--devisenhandelfranfnger-i5b58c.com/")[/B]

---

### Post by newellj79 on 2011-10-20
check out this other thread. there u can get the link for libnotify1.

 [www.ubuntuforums.org/showthread.php?t=1864316](www.ubuntuforums.org/showthread.php?t=1864316)

---

