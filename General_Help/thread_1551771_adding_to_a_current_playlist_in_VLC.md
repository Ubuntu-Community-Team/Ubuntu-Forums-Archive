---
title: "adding to a current playlist in VLC"
date: 2010-08-12
forum: General Help
---

### Post by badbradmx on 2010-08-12
couple things to start
im tired and my typing may be off a tad
this could be in the wrong place and my excuss for this is as above.

So, what i want to be able to do is add a song or video to a current playlist in VLC. i know that sounds simple, but i wanna do it from my music folder, so right click on the file then "add the playlist" like in windows (i shall headbutt a wall for saying i want something like windows).

dont know where to start on this at all, not sure what to google or anything.

i was using rhythmbox but it skips when streaming across the network so thats out unless i fix that issue. so a fix to either is appreciated.

---

### Post by howefield on 2010-08-14
> **badbradmx said:**
> So, what i want to be able to do is add a song or video to a current playlist in VLC. i know that sounds simple, but i wanna do it from my music folder, so right click on the file then "add the playlist" like in windows.

Not sure you can do it via Nautilus, but you add files to your current playlist by using VLC > View > Playlist > Add button to add music to the playlist.

---

### Post by Vaphell on 2010-08-14
install nautilus-actions. it's a tool that lets you add stuff to the context menu
you need to find out what is the command line command to enqueue file in vlc and put it there

edit:
**vlc --playlist-enqueue** supposedly adds file to the playlist, though vlc must be run in a single instance mode. There is an option in VLC preferences that does that. vlc parameter is working, 100% confirmed :)

```
sudo apt-get install nautilus-actions
nautilus-actions-config-tool
```
create a new entry, name it 'Enqueue in VLC'

conditions: file *.mp3; *.MP3; etc. (or by mimetype)
'only for files' checked

command:
path: vlc
parameters:--playlist-enqueue %f (for a single file) or %M (for a space delimited list of files). There is a button that shows all possible symbols, you can find the one you want and that works with vlc

If that newly created entry is valid, it should appear in a context menu when you right click any file(s) that match(es) the criteria.

---

### Post by badbradmx on 2010-08-16
thanks for the reply il give it ago tomorro after work :)

---

### Post by badbradmx on 2010-08-22
ok i think i got it working, fso for anyone else who wants to know.

i followed the previous posters directions and used the %M extension thingy it throws errors yet still works, just doing a few tests now.

i made sure my preferences in VLC were set to one instance and for the enqueue.

right ok it works bar one thing, i have to click next for the next song to play otherwise it repeats

---

