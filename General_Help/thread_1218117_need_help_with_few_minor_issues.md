---
title: "need help with few minor issues"
date: 2009-07-20
forum: General Help
---

### Post by cdd on 2009-07-20
Hi community!

Yesterday I decided to change to Kubuntu after using Ubuntu for about 3 months;
mainly for these fancy looking widgets and the more polished KDE environment :)
I installed the newest Kubuntu 9.04 with KDE 4.

Everything went just as expected, except for a few smaller problems,
here we go (sorted by urgency ^^):

1. The Konqueror browser and Mozilla Firefox don't play sound in flash videos (e.g. youtube), seems to be a known bug, but still no fool-proof solution?

2. I'm using a Buffalo Linkstation network drive and everytime I open up a video (or music, or anything else) via dolphin file manager the system copies the whole file into "file:///var/tmp/kdecache-desktop" - pretty annoying if you want to watch a ~1GB video file - is there a way to turn off this behaviour?

3. Using Amarok as my default audio player I was not able to add media on my network drive to Amaroks-music-library, but I assume Amarok can handle large databases on network drives, right? If not, does anyone know an alternative music player, which can do it? I was using Songbird on Ubuntu, but it's not available in the package manager of Kubuntu :(

4. This is a simple one: How to enable double-click in the file browser? I don't want documents, folders etc. to open with a single mouse click.

5. Is there a widget like "folder view" which actually can view and access folders, not only open the dolphin file manager, but open a folder within the widget?

If you read this far, thank you :D 
Any help is appreciated!

Greetings!

---

### Post by automaton26 on 2009-07-20
1. Do the following after a fresh install (see [http://en.wikipedia.org/wiki/Ubuntu-restricted-extras]("http://en.wikipedia.org/wiki/Ubuntu-restricted-extras")) but notice that it's *_**k**_ubuntu* that needs to be specified, not *ubuntu*:

```
sudo apt-get install **_k_**ubuntu-restricted-extras
```

3. I use JUK from the repositories instead. If your collection is already organized by folder, it's a lot simpler and less buggy. But I don't know if it'll address your issue.

4. System Settings->General->Keyboard&Mouse->Mouse->General->DoubleClick to open.

---

### Post by cdd on 2009-07-20
Thanks for your reply!

1. Unfortunately this didn't solve my problem with flash videos... but it seems to be a useful command anyway!

3. JUK looks like a great choice, but it won't allow me to access my network drive :/
I remember Ubuntu got an extra folder for mounted network volumes, it was called "gvfs" but I found nothing similar in Kubuntu.

4. Worked! :)

---

