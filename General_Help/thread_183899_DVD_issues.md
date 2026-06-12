---
title: "DVD issues"
date: 2006-05-28
forum: General Help
---

### Post by laix1234 on 2006-05-28
So I'm trying to get my dvd drive to operate cleanly.  When I put a cd in my cd drive, it shows up on my desktop, and the cd drive icon changes from a rectange to a cd shape.  When I put an information dvd into my dvd drive, nothing happens to the icon.  The information on it shows up in the media drive, but there is no icon on the desktop.  When I put in a video dvd (a movie from blockbuster, wanted to see if I could watch it on my computer as tv was in use), same thing, could see info, but this time I could see the files but they wouldnt run.  Perhaps that's a codex issue?  During the course of my issues, i changed my ftc/fstab file to read 

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/dvd      auto    user,noauto     0       0

instead of 

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

meaning, for one thing, that I created a dvd folder in media and the info now shows up in there instead of cdrom1 (this was just for myself, I didnt actually expect it to help).  the auto instead of udf,iso9660 was a suggestion I read on the forums for someone else's dvd woes.  Also during the course of my issues the dvd drive icon no longer appears under the computer menu

So I guess what I would like help with is

1.  When I put in a dvd, it shows up on the desktop like it should.
2.  When I put in a video dvd, it can play it (Totem launches but is unable to play when I put in the movie from blockbuster)
3. My dvd drive icon under computer to come back....

Any ideas?

---

### Post by thunderduck3141 on 2006-05-28
u need xine and a certian lib
xine is in the repos and the lib

libdvdcss2_1.2.8-1_i386.deb

just google it it comes up, click on it and follow the install instructions

---

### Post by thunderduck3141 on 2006-05-28
to run the movie type

xine dvd://

into a console

---

### Post by thunderduck3141 on 2006-05-28
and for the icon
go insto the configuration editor (gconf) and go to apps>nuatilis
and click the option in there (somewhere) that say "dislpay icon when media is....."

---

### Post by impakt on 2006-05-28
did exactly what you described and i get

** libdvdread: CHECK_VALUE failed in ifo_read.c:1006 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgcn != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1008 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgn != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1006 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgcn != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1008 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgn != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1728 ***
*** for pgci_ut->nr_of_lus != 0 ***

xiTK received SIGSEGV signal, RIP.


Is it really this difficult to play a dvd with ubuntu? Im liking some things about this OS but its little things like this that just will never allow such a great OS to never be mainstream.

---

### Post by laix1234 on 2006-05-29
Ok, I got xine to play my movie, and then I set it up so that when ever I put in a dvd movie, it plays it in xine automatically.  I also got the icon to come back.

What I didnt get that I was hoping for, and mind you it's an insignificant detail, but would be really nice to me if it could be fixed, is that when I put a dvd in it still doesnt show up on the desktop the way cds do.  I tried to find the option in gconf-editor but had no luck locating it.  When I put a cd in the dvd drive, it does show up on desktop, and does change the icon to a disk under computer.  Any ideas?  Should I not worry about it?

---

### Post by impakt on 2006-05-30
anyone have an idea whats going on with mine?

---

### Post by 2501 on 2006-05-30
It took me 5 minutes to watch dvds in my laptop. I installed 6.06 DD and i downloaded xine and libdvdcss2. This lib is available as libdvdcss2_1.2.9-1_i386.deb.

That was all. 

I would suggest you to install or upgrade to 6.06 DD.

-2501

---

