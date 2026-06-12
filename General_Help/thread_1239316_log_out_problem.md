---
title: "log out problem"
date: 2009-08-13
forum: General Help
---

### Post by mkrahmeh on 2009-08-13
some video players like VLC and mplayer are causing my system to log out automatically, thats when i try change anything from the program's menus or try to maximise the video while playing. 

am using kde3 desktop on 9.04, i thought its the problem, but its happening on gnome too..

i tried to look for something similar but not to avail, tried a fresh install, and the problem still persists !!

any help or clue is very much appreciated

---

### Post by coldReactive on 2009-08-13
Try a different player such as gxine or totem. See if they work.

(I can't use VLC, mplayer or totem to play DVDs, I can only use gxine. Go figure.)

---

### Post by mkrahmeh on 2009-08-14
does it mean that both vlc and mplayer suffer the very same bug ?
dont know about that but am more inclined into fixing an issue on my box !!

---

### Post by colau on 2009-08-14
> **mkrahmeh said:**
> some video players like VLC and mplayer are causing my system to log out automatically, thats when i try change anything from the program's menus or try to maximise the video while playing. 

am using kde3 desktop on 9.04, i thought its the problem, but its happening on gnome too..

i tried to look for something similar but not to avail, tried a fresh install, and the problem still persists !!

any help or clue is very much appreciated
It's not for mplayer.
Can you post the output of the following:
```

dpkg -l | grep mplayer

```

---

### Post by mkrahmeh on 2009-08-16
> **colau said:**
> It's not for mplayer.
Can you post the output of the following:
```

dpkg -l | grep mplayer

```

currently the mplayer is not installed, but the output for the VLC is as follows

ii  libvlc2                                    0.9.9a-2ubuntu1                    multimedia player and streamer library
ii  libvlccore0                                0.9.9a-2ubuntu1                    base library for VLC and its modules
ii  vlc                                        0.9.9a-2ubuntu1                    multimedia player and streamer
ii  vlc-data                                   0.9.9a-2ubuntu1                    Common data for VLC
ii  vlc-nox                                    0.9.9a-2ubuntu1                    multimedia player and streamer (without X su

could it be a dependency problem, a shared library for players that the system usually do not complain about ?

---

### Post by colau on 2009-08-16
> **mkrahmeh said:**
> currently the mplayer is not installed, but the output for the VLC is as follows

ii  libvlc2                                    0.9.9a-2ubuntu1                    multimedia player and streamer library
ii  libvlccore0                                0.9.9a-2ubuntu1                    base library for VLC and its modules
ii  vlc                                        0.9.9a-2ubuntu1                    multimedia player and streamer
ii  vlc-data                                   0.9.9a-2ubuntu1                    Common data for VLC
ii  vlc-nox                                    0.9.9a-2ubuntu1                    multimedia player and streamer (without X su

could it be a dependency problem, a shared library for players that the system usually do not complain about ?

Hello,
Does this ***logout problem*** occur if you use ubuntu-desktop?

---

### Post by mkrahmeh on 2009-08-16
yes ideed, it started on VLC and mplayer, then i installed ubuntu 9.04 again, with gnome desktop of course (if that's what you mean by ubuntu-desktop)..it happened again on VLC, installed kde 3 desktop, and its all the same as before !! 
in short:
it happened on both kde and gnome, using VLC and mplayer..

any suggestions ?
thx in advance

---

### Post by mkrahmeh on 2009-08-17
bump

---

### Post by mkrahmeh on 2009-08-17
> **KatePulford said:**
> Really a educative and informative post, the post is good in all regards,I am glad to read this post.

the bump ? ;)

well..[_bump_]("http://ubuntuforums.org/showthread.php?t=520091") again

---

### Post by mkrahmeh on 2009-08-18
i installed some codecs to play flv files in kaffeine, thinking that it wont cause any problems, but now the system logs out once i start the video using kaffeiene..

apparently the problem is not in either player (VLC, mplayer or kaffeiene), but there seem to be something wrong with my X setup or something.

can i reinstall X by itself ? and how ?
any other suggestions ???

---

### Post by MichealH on 2009-08-18
> **colau said:**
> Hello,
Does this ***logout problem*** occur if you use ubuntu-desktop?

Heloooooo! Colau you have got it all wrong mate GNOME is ubuntu- desktop which the person had said used KDE and GNOME and I was all not working

Geeesh:rolleyes:

---

### Post by mkrahmeh on 2009-08-18
bump..

it seems like a bug in kubuntu-desktop, though it happens on gnome too..anyway, if its not repairable, least is to track it down and attempt to report a bug..

its really annoying after a fresh install, trying different players, and different desktop managers..whats next ? to replace the hardware ?

---

### Post by MaxIBoy on 2009-08-18
What graphics hardware do you have?

---

### Post by mkrahmeh on 2009-08-18
> **MaxIBoy said:**
> What graphics hardware do you have?

```
lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

---

### Post by mkrahmeh on 2009-08-21
BumPooo

---

### Post by aldimond on 2009-08-21
In MPlayer does choosing different video output methods fix the problem?  Try something simple like plain old x11 (it might have crummy performance), then more advanced ones like xv, xover, gl, sdl, etc.  If you're using GMPlayer you can go to Preferences and look under the Video tab... from the command line you can get a list of available drivers by running "mplayer -vo help", then open your videos with "mplayer -vo <driver_name> <video_name>".

---

