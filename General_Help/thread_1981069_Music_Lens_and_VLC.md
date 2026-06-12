---
title: "Music Lens and VLC"
date: 2012-05-16
forum: General Help
---

### Post by evilsoup on 2012-05-16
I have VLC set as the default application for opening both video and audio files; I've also right-clicked on a bunch of different kinds of files (including an .MP3 file). Using the video lens, when I click on a video it does indeed use VLC.

With the Music Lens, however, it uses Rhythmbox. Which I prefer not to use. Is there any way to make these files open with VLC instead?

EDIT: oh and this is Ubuntu 12.04 with Unity 2D.

---

### Post by Derek Karpinski on 2012-05-16
System Settings (Cog in upper right corner) > Details > Default applications

---

### Post by evilsoup on 2012-05-16
Thanks, but I already have VLC set as the default for music, and for videos. I think this is a problem with the Music lens... would this count as a bug? I would certainly expect the Music lens to respect the default application selection... 

Unfortunately, this makes the Music lens borderline-unusable for me (Rhythmbox is just *too* heavyweight). The Video lens works perfectly fine... but then, the Video lens seems to be based off of the filesystem, whereas the Music lens appears to be based on Rhythmbox - it seems to search by metadata rather than filename/path.

So, does anyone have an idea how to fix this? To make these things open in VLC rather than Rhythmbox?

---

### Post by I8NY on 2012-05-16
right click on the file type that is opened with music lens and under properties there is a tab called open with. you can chose the program you want that type of file to open with. down side to this is you have to do it to each different file type.

---

### Post by evilsoup on 2012-05-16
I've done that too :P
If I open the files from within nautilus, they open in VLC as they should. It is only from the Music lens that I have this problem.

---

### Post by wojox on 2012-05-16
When in doubt (may work) :
```
gksudo gedit /etc/gnome/defaults.list
```

---

### Post by evilsoup on 2012-05-16
OK I just want ot be clear - you're suggesting I should change instances of 'rhythmbox.desktop' to 'vlc.desktop' in /etc/defaults.list ? Of course I'll make a backup first..

---

### Post by wojox on 2012-05-16
> **evilsoup said:**
> Of course I'll make a backup first..

of course since it is a bit hackish. :P

---

### Post by evilsoup on 2012-05-16
That was more for the benefit of anyone googling this thread in the future, if that had worked. Unfortunately it didn't - I changed a line in that file from
audio/x-mp3=rhythmbox.desktop
to
audio/x-mp3=vlc.desktop

I also tried totem.desktop, but that didn't work either. I suspect that the Music lens is hardwired to use Rhythmbox, which has a certain logic about it since it seems to base searches off of the Rhythmbox database rather than the file manager, but still goes against what I would expect.

Thanks for trying to help :). I'll post a link to the bug here when I've filed one.

EDIT: [here]("https://bugs.launchpad.net/unity-lens-music/+bug/1000429") it is. If anyone else is affected, please follow that link and click 'this bug affects you'.

---

