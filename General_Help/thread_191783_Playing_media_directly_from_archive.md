---
title: "Playing media directly from archive"
date: 2006-06-08
forum: General Help
---

### Post by dyssident on 2006-06-08
does anyone know of any apps that will play media files directly from archives (tar, gz, zip, rar)??

for some p2p programs (i.e. eMule),,  its very common for albums to be packed in archives because they dont understand directories, only individual files.. so once a user downloadeds their free,, public domain Grateful Dead live show,, one of two things generally happen:: 1. they unpack the files and delete the archive,, thus becoming leeches 2. they keep the downloaded archive and create a separate extracted folder,, thus doubling the required storage space..

ive searched in vain for an app that handles archives natively.. winamp has a sucky plugin and is generally useless;; this feature has been discussed on the videolan mailing list,, but no one seems interested in implementing it..

ive hacked out a script that untars and then plays in totem any archived media files.. if anyone is interested,, ill posted it once ive improved it a bit..

---

### Post by nanotube on 2006-06-08
[QUOTE=dyssident]does anyone know of any apps that will play media files directly from archives (tar, gz, zip, rar)??

for some p2p programs (i.e. eMule),,  its very common for albums to be packed in archives because they dont understand directories, only individual files.. so once a user downloadeds their free,, public domain Grateful Dead live show,, one of two things generally happen:: 1. they unpack the files and delete the archive,, thus becoming leeches 2. they keep the downloaded archive and create a separate extracted folder,, thus doubling the required storage space..

ive searched in vain for an app that handles archives natively.. winamp has a sucky plugin and is generally useless;; this feature has been discussed on the videolan mailing list,, but no one seems interested in implementing it..

ive hacked out a script that untars and then plays in totem any archived media files.. if anyone is interested,, ill posted it once ive improved it a bit..[/QUOTE]
having a script is nice :).  but since it untars the stuff and then plays it, doesn't that still require double the space? in which case, what is the goal of your script, exactly?

---

### Post by dyssident on 2006-06-08
oh right,, left that part out.. when youre done playing,, it deletes the files..

1. unarchive
2. start player
3. delete files when player closes

its about as simple as a script gets,, but it saves a whole lot of pointing and clicking..

---

### Post by dyssident on 2006-06-09
Here is a rough draft of the script.. If you get a second,, try it out and let me know what you think..

To install::

download to ~/.gnome2/nautilus-scripts
chmod 755 ~/.gnome2/nautilus-scripts/play-archive-totem.txt
mv ~/.gnome2/nautilus-scripts/play-archive-totem.txt "/home/yourusername/.gnome2/nautilus-scripts/Play Archive in Totem"
killall nautilus

then just right click archive file in Nautilus > scripts > Play Archive in Totem..

---

### Post by dyssident on 2006-07-07
You can find what has become archplayer at [this post]("http://www.ubuntuforums.org/showthread.php?p=1227167").

---

