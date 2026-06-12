---
title: "Xmms and m4a/mp4"
date: 2005-03-02
forum: General Help
---

### Post by christooss on 2005-03-02
Is there a plugin for Xmms to play music encoded in mp4.

Thanks for the anwser

---

### Post by p!=f on 2005-03-02
You lazy one. ;) How about to try some searching first?
```

[~] > apt-cache search xmms-mp4
xmms-mp4 - a mp4/aac audio player for xmms

[~] > apt-cache show xmms-mp4
Package: xmms-mp4
Priority: optional
Section: universe/sound
Installed-Size: 64
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Source: faad2
Version: 2.0.0-0.3
Depends: libc6 (>= 2.3.2.ds1-4), libfaad2-0 (>= 2.0.0-0.3), libglib1.2 (>= 1.2.0), libgtk1.2 (>= 1.2.10-4), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxi6 | xlibs (>> 4.1.0), xmms
Filename: pool/multiverse/f/faad2/xmms-mp4_2.0.0-0.3_i386.deb
Size: 9382
MD5sum: 6d2e4b6914d056fb67080a48c3080bd2
Description: a mp4/aac audio player for xmms
 This plugin is a merge between aac and mp4 plugin. so now you could read
 all new and old files encoded with different encoder and different format
 (for the aac part). This is possible since the libfaad2 allow to read old
 aac ADTS format.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```
(running Ubuntu Hoary)

Google told me (xmms mp4):
[http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/)
[http://www.xmms.org/plugins.php?details=75#](http://www.xmms.org/plugins.php?details=75#)

---

### Post by Shaggy on 2005-03-02
Although this might be true, it's not the case for warty.  It's pretty unstable in warty, and the only way I found to play any mp4 files is using mplayer with the windows codecs installed.

If someone else has found a easy way to do it in warty I'm sure a lot of people would like to know.

---

### Post by christooss on 2005-03-02
[QUOTE=p!=f]
[http://www.xmms.org/plugins.php?details=75#](http://www.xmms.org/plugins.php?details=75#)[/QUOTE]

 I found this but the link was broken and I found several forums where nobody knew what to do. And yes its easyer to ask here :)

---

### Post by p!=f on 2005-03-02
This link works:
[http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/)

You could also try beep-media-player. Looks like XMMS but with GTK+2.x.

---

### Post by bored2k on 2005-03-02
[QUOTE=p!=f]This link works:
[http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/)

You could also try beep-media-player. Looks like XMMS but with GTK+2.x.[/QUOTE]

meanwhile, 
>  $ apt-cache search m4a
dir2ogg - converts mp3, m4a, and wav files into ogg-vorbis forma

---

### Post by dolson on 2005-03-27
[QUOTE=bored2k]meanwhile,[/QUOTE]

Wow, that looks cool. I've gotta install that and get converting. :)



EDIT: Hey, what repository is that in?

---

### Post by lorap on 2005-03-28
hi!
as soon as you're a newbie in ubuntu you better use xmms for mp3 and vlc for mp4:
you've to go to the Computer-->Computer Management-->Synaptic Package Manager.once you've the synaptic window open go to the Settings-->Repositories.
once you've a new small window open mark all possible checkboxes ignoring the worning messages after what press Ok button.the window closes and you're back again to the main synaptic window.press Reload button and wait until the process completes.after the process's completed press the Search button and in the search window write in VLC then press Ok button.once the synaptic picks it up for you mark the VLC whose remarks're "for gtk+" but not for the gnome.that one for the gnome has a bug.after you mark it for installation press Apply button.that's all.
have a nice day friend!
pavel

---

