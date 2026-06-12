---
title: "Playing media from an external hard drive"
date: 2011-11-13
forum: General Help
---

### Post by bradlees on 2011-11-13
Is there a way to play music through banshee (the music player I currently use) without uploading a library or directory onto the pc? I would like to a path or something to point the player to the usb drive rather than having to sync all the files. Is there a better player or a simpler step that I am too computer eliterrat to figure out?

Just don't want to store the music files on the pc's hd.

Thanks for looking,

Big Ben

---

### Post by Nixarter on 2011-11-13
I like Elissa (which is a media center).  XBMC also works well.

As for just a media player (not media centers), I don't know.  :(

---

### Post by raja.genupula on 2011-11-13
> **bradlees said:**
> Is there a way to play music through banshee (the music player I currently use) without uploading a library or directory onto the pc? I would like to a path or something to point the player to the usb drive rather than having to sync all the files. Is there a better player or a simpler step that I am too computer eliterrat to figure out?

Just don't want to store the music files on the pc's hd.

Thanks for looking,

Big Ben

why dont you use VLC or Umplayer for playing the songs

---

### Post by K-Jtan on 2011-11-13
Sorry for not being to help you with this, but like the others I could suggest you to use a different software. The one I suggest is call Totem (usually use to play movies).

Like mention in this post, [http://ubuntuforums.org/showthread.php?t=1670217](http://ubuntuforums.org/showthread.php?t=1670217)

you could just run a small line in the terminal to enqueue all your songs into totem using this command

```
find . -iname \*.mp3 -print0 | xargs --null totem --enqueue
```

---

