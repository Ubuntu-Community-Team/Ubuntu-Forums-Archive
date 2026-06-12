---
title: "How to install multimedia codecs in Lubuntu"
date: 2010-06-15
forum: General Help
---

### Post by geovino on 2010-06-15
How to install multimedia codecs in Lubuntu?

---

### Post by mkvnmtr on 2010-06-15
Are they not in the Synaptic package manager?

---

### Post by xzased on 2010-06-15
Have you tried medibuntu? add it to your repos, apt-get update && apt-get install w32codecs (or w64codecs if you are on 64-bit version)

---

### Post by kerry_s on 2010-06-15
> **geovino said:**
> How to install multimedia codecs in Lubuntu?

use synaptic to install the ubuntu-restricted-extras or xubuntu-restricted-extras, if you don't want everything.

---

### Post by geovino on 2010-06-15
> **kerry_s said:**
> use synaptic to install the ubuntu-restricted-extras or xubuntu-restricted-extras, if you don't want everything.

I installed ubuntu-restricted-extras but VLC still can't play DVDs.I also have libdvdread4 installed. something is missing.

At least flash videos and live streaming music are playing.

---

### Post by geovino on 2010-06-15
when I run VLC it tries to open and then closes. there are two CD ROM's on this PC. the main one says rewritable on it, so I don't know if it reads DVDs, the other is a DVD ROM. maybe vlc is trying to read from the wrong one, how do read from either CD ROM?

---

### Post by xzased on 2010-06-15
for dvd&#347; you would need libdvdcss2 from the medibuntu repos

---

### Post by geovino on 2010-06-15
installed mediubuntu repos and libdvdcss2. But it still can't play. what else is needed?

---

### Post by proggy on 2010-06-15
> **geovino said:**
> installed mediubuntu repos and libdvdcss2. But it still can't play. what else is needed?
you`re sure you have a dvd player?:confused: anywhos go here and add evrything [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by geovino on 2010-06-15
> **proggy said:**
> you`re sure you have a dvd player?:confused: anywhos go here and add evrything [http://www.medibuntu.org/](http://www.medibuntu.org/)

I've got VLC installed. I've always used that in other distros.

I've just installed w32codecs, I"m copying files so I'll wait until later and reboot. that usually works.

---

### Post by geovino on 2010-06-16
just rebooted and still VLC can't play DVD. what else could be missing?

---

### Post by bailout on 2010-06-17
Have you tried following the instructions on this page.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Chame_Wizard on 2010-06-17
> sudo aptitude install ffmpeg ffmpeg-dbg
Works always.:guitar:

---

### Post by geovino on 2010-06-17
> **Chame_Wizard said:**
> Works always.:guitar:

Thanks, I'll try those if the client ever used the DVD, she may not. But I'll keep it in mind for future use. 

Otherwise Lubuntu works great on her old Compaq pc!

---

### Post by shaulreznik on 2011-10-01
sudo apt-get install lubuntu-restricted-extras

---

### Post by oldos2er on 2011-10-01
Closed, necromancy.

---

