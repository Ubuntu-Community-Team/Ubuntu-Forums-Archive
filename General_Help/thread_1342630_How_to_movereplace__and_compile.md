---
title: "How to move/replace  and compile"
date: 2009-12-01
forum: General Help
---

### Post by princeofnam on 2009-12-01
I'm new to Ubuntu and need some major help. I was given some basic instructions on how to fix my sound for my Pavillion dv6500. Unfortunately I don't know how to replaces to files and subsequently compile them.  The post is:

--
-----
 Hey Scotty, I was just able to get the sound working, I found the solution here: [https://bugtrack.alsa-project.org/al...ew.php?id=3165]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165") . Just sign in as guest to view the forum.

Kentrosaurus gives his solution and links to where he found it...download the newest alsa driver, utils, and lib (I used 1.0.14rc4), replace hda_proc.c and patch_realtek.c from realtek10.tar.gz (on the page Kentrosaurus linked to, pshou explains how to do this).

Insert the line "options snd-hda-intel model=toshiba" on the end of /etc/modprobe.d/alsa-base. Finally, compile the driver using the directions here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) .

If you have any questions, just ask!

Edit: Interestingly, though, the mute button is now always lit up blue, and it seems to only mute the front audio jacks. On the volume control, the "headphone" slider seems to affect both the headphone and line-out jacks, while "front" affects the built-in speaker. Also, at this point, the speaker does not automatically turn off when headphones are inserted, it needs to be manually muted.
---

Can anyone help me? When I try to use the GUI i am not allowed permission to replace the file.

---

