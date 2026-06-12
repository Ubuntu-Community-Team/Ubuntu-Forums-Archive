---
title: "linux &amp; ipod shuffle"
date: 2009-09-10
forum: General Help
---

### Post by oospill on 2009-09-10
I'm trying use my ipod shuffle with my linux box.  I've tried gtkpod, and it doesn't do anything at all.  can't even use the 'load' button at the top.  I noticed another program (or rather collection of perl scripts) called GNUpod.  I have no idea what I'm supposed to do with it.  can anyone help?

all I want to do is put my music files in the right directory (on the ipod) and then have it update the binary index file.

please help!!

ps:  I think my cat unrolls the toilet paper because he wants to know what it's for.

---

### Post by oospill on 2009-09-10
sorry folks, I spoke too soon.  once I read the docs (which seemed really long), I got my ipod shuffle working great with GNUpod.

is there a way too set posts as SOLVED?

thanks, 
oospill

---

### Post by speedwell68 on 2009-09-10
An even better option is Songbird with the Ipod support addon and the media flow addon.  It is much more user friendly and works in a similar way to real iTunes.  You can get Songbird from GetDeb.

---

### Post by chriskin on 2009-09-10
as for the solved tag all you have to do it edit the first post and put the solved tag on :)

---

### Post by oospill on 2009-09-10
> **speedwell68 said:**
> An even better option is Songbird with the Ipod support addon and the media flow addon.  It is much more user friendly and works in a similar way to real iTunes.  You can get Songbird from GetDeb.

hey, cool.  I just un-tarred it into it's own directory in my home dir, and double-clicked the file 'songbird' .. it loaded up and seems cool so far.  though, I would like it to be up in my applications menu.  how do I add programs to my applications menu?

thanks,
oospill

---

### Post by oospill on 2009-09-10
well, I just installed the ipod add-on.  but I can't tell a difference in songbird, I can't find anything that says 'ipod' anywhere.  ??

oospill

---

### Post by matt5596 on 2009-10-31
I had my iPOD shuffle partially working in Songbird.  Songbird could see the ipod but if I sent a playlist it would show the entire playlist in songbird but the ipod would only play some of the songs.

I synced my ipod with my itunes on  other machine and now when I connect it to my ubuntu, Songbird won't even recognize it.  

I need some help!

---

### Post by matt5596 on 2009-11-01
So I figured out both issues:  

1: For some reason if I send a m4a to my iPOD it wont play.  If I convert the files to mp3 and plays fine.

2: I deleted the ipod_control directory from the iPOD and it was immediately recognized by Songbird.

---

### Post by Ampi on 2009-11-16
[iPod shuffle's Rebuild]("http://shuffle-db.sourceforge.net/")

With this software you are not depending on any music player or linux distribution at all.

It's a real simple and small program which you copy into your iPod shuffle folder. Then just drag 'n drop the music. Once you're done, just run the program and all the files on your iPod are updated..
The program generates a log-file that shows you all the files that have been stored on the iPod shuffle.

It works in my opinion better and simpler than GNUpod or GTKpod or any of those other programs. But it is only for the shuffle..

---

