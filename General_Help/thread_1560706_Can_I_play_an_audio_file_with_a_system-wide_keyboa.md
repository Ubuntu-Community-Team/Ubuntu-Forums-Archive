---
title: "Can I play an audio file with a system-wide keyboard shortcut?"
date: 2010-08-25
forum: General Help
---

### Post by joeblurton on 2010-08-25
I do a bit of script writing, and part of this involves reading the text aloud and reacting to audio cues. What I'd love to do is set up a method of playing audio files at whim based on a general shortcut. So, say if I pressed <Super>C1, I could play ~/Music/cue1.mp3, <Super>C2 would be ~/Music/cue2.ogg  etc.

Currently the closest I've got is using the terminal and a modified .bashrc to play via VLC's ncurses. 

```
alias cue1="vlc -I ncurses ./Music/cue1.mp3"
```

Obviously this isn't very near to what I want. Entering a Keyboard Shortcut using the usual methods (xbindkeys, gconf-editor, the KeyShort Preferences GUI) to run ```
vlc -I ncurses ./Music/cue1.mp
``` doesn't play anything. Is it possible to launch these kinds of commands as shortcuts, or am I hoping for too much? My Google trawls have been pretty fruitless.

Many thanks if any of you can help.

I'm running Lucid, btw.

---

### Post by joeblurton on 2010-08-25
I thought I'd best mention that I'd rather summon a program when needed, rather than have to rely on a player like Rhythmbox already being open.

Similarly, ```
mplayer ./Music/cue1.mp3
``` doesn't work.

---

### Post by joeblurton on 2010-08-25
I've worked it out! Making custom keybindings with gconf-editor didn't work with vlc, but for someone reason it works with mplayer. I entered:

```
mplayer ./Music/cue1.mp3
``` 

Press <Super>c1. And it now plays.

Success! I hope that's useful to someone down the line.

You can even make a new keybinding saying ```
killall mplayer
``` and the sound will stop!

---

