---
title: "Totem Help"
date: 2006-05-06
forum: General Help
---

### Post by cssutto on 2006-05-06
Totem starts my DVD, but no sound and no video.

It can find the files on the DVD and appears to run in that the progress button moves across the bottom just as it should when the video is running.

What can I do to resolve this?

CSSJR

---

### Post by kingmonkey on 2006-05-06
Have you installed ccs?

```
sudo apt-get install libdvdcss2 
```

More info here:

[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

---

### Post by cssutto on 2006-05-06
I have, and this is what I got when I ran it again just now:

Reading package lists... Done
Building dependency tree... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


CSSJR

---

### Post by ffferko on 2006-05-06
**Select System** >> **Administration** >> **Synaptic Package Manager**

Click Search and search for *libdvdread*. If the package isn't already installed, click its check box and mark it for installation. Then click Apply. Close Synaptic Package Manager.

**Open a GNOME Terminal. Type the following in the terminal window to download and install the DeCSS component:**

*sudo /usr/share/doc/libdvdread3/examples/install-css.sh*

---

### Post by cssutto on 2006-05-06
I had libdvread3.

I copied and executed the command you gave me.

Still not working.

I have sound, but no video.

CSSJR

---

### Post by cssutto on 2006-05-06
I can go direc tly to the folder containing the video and right click on it and tell it to open with VLC and it will open about half the time.  Then I can switch to Totem and it will run fine.

But when I exit and try to open it with Totem after the exit, I get sound and no video.

CSSJR

---

### Post by blackjack6.21.91 on 2006-05-06
try installing totem xine

---

### Post by cssutto on 2006-05-06
I have totem-xine.

CSSJR

---

### Post by r53s on 2006-05-06
If you already have libdvdcss and Xine engine doesn't work...
Then try VLC media player...
And tell us how it's going...

---

### Post by cssutto on 2006-05-06
As I mentioned above, I can go directly to the folder and right click and select VLC and it will run sometimes.

There is some combination of clicks that I have not figured out yet that will make it play.  Not the first one.

After VLC plays, I can sometimes exit it and get totem to play.

There is some file on my system that is there and working but the path to it is not correct and it has to be awakened by a non standard method.

CSSJR

---

