---
title: "Question about VLC"
date: 2010-09-19
forum: General Help
---

### Post by cptrohn on 2010-09-19
OK... I am playing a DVD with multiple copies of it's content on the disc... I am wanting to use VLC to try and find out which of the tracks is the right one for when I rip.... Anybody know how to do this?

---

### Post by Vaphell on 2010-09-19
you may want to rephrase the question
what is vlc supposed to do exactly? locate currently opened video chunk?

---

### Post by cptrohn on 2010-09-19
> **Vaphell said:**
> you may want to rephrase the question
what is vlc supposed to do exactly? locate currently opened video chunk?

No actually there is supposed to be a way for VLC to list what copy of the content that it is playing... on this particualr DVD there are multiple copies of the same thing.. but only one copy is the actual "good" copy..

---

### Post by Vaphell on 2010-09-19
no idea - i don't have any dvd with duplicated content to investigate


lsof -n -F -c vlc | grep "^n/media"

lsof lists used resources (including files), in this case assigned to vlc (-c vlc), grep filters out everything that doesn't look like /media/* (i assume your dvd is mounted in /media)
maybe you'll find that useful, maybe not

edit: doesn't work :/

---

### Post by cptrohn on 2010-09-19
> **Vaphell said:**
> no idea - i don't have any dvd with duplicated content to investigate


lsof -n -F -c vlc | grep "^n/media"

lsof lists used resources (including files), in this case assigned to vlc (-c vlc), grep filters out everything that doesn't look like /media/* (i assume your dvd is mounted in /media)
maybe you'll find that useful, maybe not

Thanks, I will give that a try and see what happens..

---

### Post by Vaphell on 2010-09-19
i predict not much will happen, i gave some random video dvd a spin and the physical files of the dvd were not listed, apparently they are not opened 'normally' by the system :/

---

### Post by howefield on 2010-09-19
> **cptrohn said:**
> OK... I am playing a DVD with multiple copies of it's content on the disc... I am wanting to use VLC to try and find out which of the tracks is the right one for when I rip.... Anybody know how to do this?

Would you know it when you see it ?

Browse the DVD in Nautilus, the thumbnails or file name might give the game away, or play each file in Totem till you get the right one.

---

### Post by mc4man on 2010-09-19
> I am wanting to use VLC to try and find out which of the tracks is the right one 

Just simply play the dvd in vlc, once the movie starts then click on 'Playback' and look under  'Title', that will give you the titleset to use.

should work for the vast majority of that style of structure protection.

---

