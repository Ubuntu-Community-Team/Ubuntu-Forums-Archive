---
title: "gMount-iso Issue"
date: 2011-12-13
forum: General Help
---

### Post by new to linux help needed on 2011-12-13
am i correct that mounting is like, decompressing, im able to then open a folder with all of the files that were within the iso. i have both a physical cd where i put the iso on it, and a copy on my computer.

to be a little clearer on my objective, it is to mount an iso to play my game. _am i doing this correctly, should i use wine, what wine program, thanks for the help_

when ever i try to use gMount i get the following error

"An error occured
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

what does this mean?
how would i go about fixing this issue?

---

### Post by seawolf167 on 2011-12-14
ISO file images are *uncompressed*, so opening or mounting an ISO does not require decompression of any kind.

Here is the Ubuntu Community Docs on [Mounting ISO images]("https://help.ubuntu.com/community/MountIso").

---

### Post by 4Orbs on 2011-12-14
Gmountiso has gotten a bit less user-friendly when using Xubuntu 11.10. I also get an error when mounting the iso, and gmountiso doesn't show the iso as mounted, but it really is mounted. You can verify if it is mounted by opening the folder /media and see if the iso is showing up there (or whichever folder you specified as the mount-point). Unmounting is the real hassle; gmountiso won't unmount it, so I gotta use the terminal to unmount.

If this iso is a game for Windows, then you need to use Wine to make it work. And you need to configure Wine properly before attempting to install the game.

---

