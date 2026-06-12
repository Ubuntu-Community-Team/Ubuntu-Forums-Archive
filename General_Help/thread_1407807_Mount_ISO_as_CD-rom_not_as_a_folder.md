---
title: "Mount ISO as CD-rom not as a folder"
date: 2010-02-15
forum: General Help
---

### Post by 3DCGdesign on 2010-02-15
I can't run the Macrium Ubuntu Recover CD, it just fails for some reason.
But I have Kubuntu 9.10 x64 freshly installed.

I was hoping if I could mount the Macrium Ubuntu Recovery ISO as a drive from within Linux it would "play" and allow me to recover my Vista backup.

I followed these instructions: 
[Mount ISO as CD-rom not as a folder ]("http://ubuntuforums.org/showpost.php?p=2318893&postcount=2")

**It works, and the Iso is mounted, but I don't know what to do to get the now virtual "CD" in the virtual "drive" to "spin up" ... to "play"... that is, to "boot"... whatever you want to say.**

I'm not trying to play a virtual CD or game, I'm trying to recover my Vista backup when I can't boot Vista.

(I'm actually trying this as an option.  My Vista is currently running fine, I'm doing it in preparation for when Vista fails to boot next time ... like it did to me about a week ago.)

---

### Post by paulmmj on 2010-02-15
Download a program called "GMount-iso", it's in the repository, and mount your .iso to a "Filesystem/media/cdrom0." Then it acts like a CD and not a folder.

---

### Post by ironclaw on 2010-02-16
Are you referring to the ISO of the rescue CD provided by Macrium Reflect? It is meant to be burnt to a CD to be booted from, and you can't really run it from within another OS.

---

