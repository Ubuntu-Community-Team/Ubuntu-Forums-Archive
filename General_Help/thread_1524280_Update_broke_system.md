---
title: "Update broke system"
date: 2010-07-05
forum: General Help
---

### Post by Meskarune on 2010-07-05
I just updated my xubuntu  10.4 to the latest firmware and xorg server. Now my computer will only boot in low graphics mode and I can't log in, when I try it logs back out again. I have an nvidia graphics card. My computer was working perfectly until the update.

---

### Post by giddyup306 on 2010-07-05
Can you boot with a different/previous kernel?

---

### Post by Meskarune on 2010-07-05
No. That was the first thing I tried and it didn't work. :/ I think I might just take the time to set up arch linux...I wanted to give ubuntu a chance because of the nice features like ubuntu one, gwibber, boxee etc. But its just way too buggy. I could probably set up a fast, stable arch install in the time it would take me to fix all the problems the update created.

---

### Post by giddyup306 on 2010-07-05
I was having boot issues with nvidia as well.  I believe that this is the file that fixed my problem.

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/Xorg.png[/IMG]

You can always try copying the file (if it's missing) off of the live CD.

---

### Post by Meskarune on 2010-07-05
I uninstalled and reinstalled the nvidia drivers from xterm and now it boots up and seems to be working ok. Fixed the xfce not logging in thing by editing a text file.

---

### Post by Meskarune on 2010-07-05
Is there a command to reload the video drivers when xorg or the linux kernel get updated? I'd like to avoid this happening in the future...

:)

---

