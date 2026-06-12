---
title: "Rhythmbox: Unable to activate most plugins"
date: 2010-11-06
forum: General Help
---

### Post by davezatch on 2010-11-06
Two days ago, I started up Rhythmbox and was met by a slew of pop-up windows telling me that almost all my plugins were 'Unable to Activate.'  This includes context pane, buscawiki, cover art, GoCover, Jump to Playing, Song Lyrics and most others.  After closing all the pop-ups, I am unable to re-enable any of these plugins, leaving my Rhythmbox far less useful than it used to be.

Several plugins do still work, including DAAP Music Sharing, Last.FM (although not Last.FM Synchronization features, which allows me to update play counts via last.fm), Portable Players - iPod, Power Manager, Status Icon, and Visualization.  

I've searched all over and have been unable to find any help on this.  Various people have had one or 2 plugins go on the fritz but I'm not sure what to do about the vast majority of them just failing.  I presume it's some kind of dependency issue caused by an update, but for the life of me, can't figure out which one.

Possibly related, I have one held-back update, gir1.0-glib-2.0.

This is rhythmbox 0.13.1.

Any help is greatly appreciated!

---

### Post by dino99 on 2010-11-06
if some of the plugins used are old and no more maintained, it could be the reason why.

try to remove/purge then reinstall each related packages

---

### Post by kostkon on 2010-11-06
You could check the permissions of the rhythmbox plugins folder(s):
```
/usr/lib/rhythmbox/plugins/
```
and
```
$HOME/.gnome2/rhythmbox/plugins
```

---

