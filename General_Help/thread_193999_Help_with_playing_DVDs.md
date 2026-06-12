---
title: "Help with playing DVDs"
date: 2006-06-10
forum: General Help
---

### Post by yteh on 2006-06-10
Looking for any help I can get. I just got done installing Ubuntu 6.06 on my desktop PC.

I can pretty much do everything except for playing DVDs. I've got Totem-Xine and libdvdcss installed.  Totem's telling me that it couldn't play because the disk is not present. It's in the CDROM drive.

I'm totally lost here. I can play audio CDs and even Diablo (via Wine) but just not DVDs. I'm thinking it's not the CDROM device. Maybe there's something I'm missing from the setup? Please help.

I've got Ubuntu set up on my laptop and DVDs are fine there.

Thanks

---

### Post by zugu on 2006-06-10
I managed to play DVDs with VLC: install vlc, then go to File >> Open Disc. In the Open field, in the Media Resource Locator box, type```
dvd:///media/cdrom
```assuming your CD-ROM is mounted to /media/cdrom or ```
dvd:///media/cdrecodrer
```if you have a DVD writer and it is mounted to /media/cdrecorder

It worked for me, hope it works for you.
You can install vlc with:```
sudo apt-get install vlc
```

---

### Post by yteh on 2006-06-10
Thanks for the reply. Tried your suggestion out but it's still not working. Could this be a mount issue? Reason I ask is because in my preferences for "Removable Drives and Media", it's set to play DVDs with Totem when I insert the disc. However, nothing happens when it's inserted.

That's when I open up Totem, select Play Disc "CD-ROM' Drive and receive the "...please check that disc is present" message.

---

### Post by zugu on 2006-06-10
Insert your dvd. It should automatically be mounted to /media/cdrom or /media/cdrecorder. Under either of these directories, you should be able to see some files (even if the inserted disc it's a dvd video). If there are some files there, then it's not a mounting problem. Either way, I cannot help you anymore in this problem. Maybe someone else can.

---

### Post by yteh on 2006-06-10
I'll look around some more but I guess I can live without DVDs. Not a biggie.

I really appreciate your suggestions.

---

### Post by scxtt on 2006-06-10
totem is generally a pain, have you tried xine?

---

### Post by yteh on 2006-06-11
I've pretty much tried totem-xine, gxine, mplayer, vlc...

I don't think the problem is with those applications. It's been quite straightforward setting it up on my laptop which I had no issues with. I think there's something else going on with my desktop. 

I'm going to let it go for now. I can live with it. 

Thanks

---

### Post by scxtt on 2006-06-11
[QUOTE=yteh]I've pretty much tried totem-xine, gxine, mplayer, vlc...

I don't think the problem is with those applications. It's been quite straightforward setting it up on my laptop which I had no issues with. I think there's something else going on with my desktop. 

I'm going to let it go for now. I can live with it. 

Thanks[/QUOTE]well there are generally subtle differences between all that you've mentioned - i've even noticed usability issues b/t xine and gxine ... i've had the best luck w/ xine (ver. 0.99.*) it has tons of options and is pretty self-explanatory ...

since i can't see your system, i'm almost thinking this is a case of mistake link identity, meaning something isn't understanding that your dvd drive is /dev/hdb (for example) and is trying to default to something like /dev/dvd (which might not exist - the only reference to my DVD±RW would be /dev/hdb) ... basically, all you'll need to do is make sure xine points to your /dev/hdb and you should be good to go, since libdvdcss is installed ...

---

### Post by yteh on 2006-06-11
Problem fixed with playing DVDs. I just bought myself a new CD/DVD ROM drive. Probably something corrupted with the old one.

Thanks for all the suggestions...

---

