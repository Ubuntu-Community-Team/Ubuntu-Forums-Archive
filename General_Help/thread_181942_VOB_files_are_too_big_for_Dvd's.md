---
title: "VOB files are too big for Dvd's"
date: 2006-05-25
forum: General Help
---

### Post by lemix on 2006-05-25
I copied a movie that i dont have anymore to my hard drive. I have both audio_ts and Video_ts folders but the files total 7 Gigs. My DVD-RW Drive isnt able to burn to Dual Layered DVD's. 

Is there any way that i can make this smaller by sacrificing quality or resolution?
Any programs that will compress this files?

---

### Post by Resurrection on 2006-05-25
Well, I don't know on Linux, but DVD Shrink was a great program for this on Windows.  I highly recommend it.  I don't know of a Linux equivalent to DVD Shrink.  With Shrink, you could remove everything down to the main movie, and then compress it with some quality loss (not bad) to fit on disks better.

Without something like that, you're only other option would be to take the movie, and find an encoding program and re-encode the movie into Xvid or Divx or some other format, but this would result in a lot of quality loss.

---

### Post by stevestyle51 on 2006-05-25
dvd shrink is in fact the best option for you.  You need to download wine-setuptk (not sure what exactly it is called so search synaptic) and setup a fake windows partition, or use the one you already have (dual boot).  Then install wine, a windows emulator to run dvd shrink with.  There are several more options that you need to set before this application will run properly on your box.  To my suprise I found several tutorials on this by searching google with: dvd shrink on linux.  Hope this helps.  I have yet to find a good program that is solely linux based that can manipulate the file sizes of vobs like dvd shrink can.  So if someone could, enlighten me.

---

### Post by zainka on 2006-05-25
Also check [Videohelp]("http://www.videohelp.com") for Linux tools, however, as far as I know with my experience, burning the new vobs cant be done with dvd shrink, but if you already have a dvd burner program which is capable of burning dvd videoes format (to be played in Video dvd players) there should be no problems using shrink

Z

---

### Post by T313C0mun1s7 on 2006-05-25
Go into Synaptic Package Manager and do a search for K9Copy. It is the Linux replacement for DVD Shrink. It is a KDE Tool however, so be aware you will be adding a fair number of dependent packages to your install if you are not running anything else KDE.

---

### Post by lemix on 2006-05-26
Thanks a lot All.

---

### Post by richbarna on 2006-05-26
I am using k9copy to extract the dvd's to my hard drive, and then I use dvd shrink with wine and it works perfectly.

---

### Post by lemix on 2006-05-28
Thanks for the Tip. DVD shrink works great.
Hear is a link for anyone else to download it
[http://www.afterdawn.com/software/dawnload.cfm?mirror=0&software_id=519](http://www.afterdawn.com/software/dawnload.cfm?mirror=0&software_id=519)

---

