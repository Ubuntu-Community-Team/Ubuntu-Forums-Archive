---
title: "Deleting Gnome-Shell"
date: 2011-09-07
forum: General Help
---

### Post by ki4jgt on 2011-09-07
Installed Gnome-Shell (Gnome3) a few weeks back. Have been using it very well. No problems. Unfortunately it's acting buggy now. I can't do anything without it taking control of my mouse and throwing it ALL over the screen or disabling my keyboard completely. :-( I had to remove my laptop's battery and literally unplug it to get control of my keyboard and mouse again. Unfortunately I am unable to use the mouse and the keyboard within unity or Gnome-shell. Currently, I am using Links and the first terminal to access this site. Thank God I allowed my computer to automatically connect to wifi. Any and all help is appriciated. Basically I want to uninstall everything gnome (even Unity) and reinstall Unity (from scratch). If this is possible, it would be GREAT.

---

### Post by MG&amp;TL on 2011-09-07
I don't know, but won't

```
sudo apt-get remove --purge gnome-shell
```

do it?

The PPA purge function in ubuntu-tweak seems to work too.

For instructions on Unity, see here:

[http://linux-software-news-tutorials.blogspot.com/2011/05/how-to-remove-unity-in-ubuntu-1104.html]("http://linux-software-news-tutorials.blogspot.com/2011/05/how-to-remove-unity-in-ubuntu-1104.html")

Does it help?

---

### Post by ki4jgt on 2011-09-07
The problem is that the guy told me it would break Unity completely. He said there would be no coming back to Unity if without some major work. So, I was wondering if I could completely uninstall gnome-shell and Unity in the same command and then reinstall unity.

---

### Post by walt.smith1960 on 2011-09-07
What version, 11.04 or 11.10?  I'd take a look in Synaptic.  See if you have an entry "gnome-shell".  If you do, remove it.  I wouldn't think that would break Unity though I haven't tried uninstalling.  Both Gnome-Shell and Unity run on top of Gnome 3 in 11.10, not sure about 11.04 & earlier. Needless to say -but I'll say it anyway- back up anything important before doing anything that could terminally bork your box.

---

### Post by ki4jgt on 2011-09-07
> **walt.smith1960 said:**
> What version, 11.04 or 11.10?  I'd take a look in Synaptic.  See if you have an entry "gnome-shell".  If you do, remove it.  I wouldn't think that would break Unity though I haven't tried uninstalling.  Both Gnome-Shell and Unity run on top of Gnome 3 in 11.10, not sure about 11.04 & earlier. Needless to say -but I'll say it anyway- back up anything important before doing anything that could terminally bork your box.

It was carrying the problems over to Unity. Found a nice little site while in Links which walked me through uninstalling them both, removing gnome3's ppa and then reinstalling Unity. Would post the link but don't have it. I went through a few pages of Google to find it. Thanks guys for your help.

---

