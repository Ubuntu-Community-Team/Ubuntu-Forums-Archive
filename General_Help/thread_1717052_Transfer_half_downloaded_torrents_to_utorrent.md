---
title: "Transfer half downloaded torrents to utorrent"
date: 2011-03-29
forum: General Help
---

### Post by donpeter06 on 2011-03-29
I use ubuntu 10.10 in my AMD 64x2 4000+ processor.
I had downloaded half portion of a certain torrent file using ktorrent(in gnome).
Now i have installed utorrent using wine. 
Is there any way i can transfer the half downloaded torrent to utorrent and continue downloading the rest part in utorrent.
Thanx

---

### Post by DanneStrat on 2011-03-29
> **donpeter06 said:**
> I use ubuntu 10.10 in my AMD 64x2 4000+ processor.
I had downloaded half portion of a certain torrent file using ktorrent(in gnome).
Now i have installed utorrent using wine. 
Is there any way i can transfer the half downloaded torrent to utorrent and continue downloading the rest part in utorrent.
Thanx

Hi!

Have a look at the partially downloaded files from ktorrent.

Often, torrent clients append an extension to incomplete files

like ".part" or ".bc" to gain exlusive access to those files.

For example, if you have the ".part" extension, utorrent will not resume

the download of that file.



So if you have a file called "myfile.part" you would

delete ".part" from that file.

Next you would load the .torrent file in utorrent

and set the download directory to the location

of your files. Then it should resume.

---

### Post by seawolf167 on 2011-03-29
Most torrent programs should have a built-in "check" system for checking that the file matches the torrent. If the two don't match, it resumes downloading the incomplete file.

As DanneStrat said, move the files to your new location, but ensure that the filename is it's normal (final) filename without any *additional *extensions

---

### Post by donpeter06 on 2011-03-30
Thanx For the Help 
It worked.
Right now i dont feel like a newbie to ubuntu. as i have the forum here.

---

### Post by DanneStrat on 2011-03-31
> **donpeter06 said:**
> Thanx For the Help 
It worked.
Right now i dont feel like a newbie to ubuntu. as i have the forum here.

You're welcome!

---

