---
title: "Any Media Managers, like ember + tvrename for windows?"
date: 2010-04-30
forum: General Help
---

### Post by knidsrok on 2010-04-30
At this point, the only programs I still use my Windows partition for are the various automated media managing apps like Ember media manager, Tvrename and Therenamer.

For those not familiar with the above programs, what they do is take your ripped/recorded TV and movie files, rename them according to an xbmc-friendly naming protocol, organize them in terms of directory structure, and even download screen shots and metadata for them.

Are there any good alternatives for Ubuntu?  If not, would running those windows programs on a virtual machine or with Wine work?  Which would be easiest/most stable?

---

### Post by drewsus on 2010-04-30
Im wondering the same thing, but Im just about to try Ember through WINE on Lucid. 
Ill report back, but I hope to hear that there is a nice Open Source alternative.

Drew

---

### Post by knidsrok on 2010-05-01
> **drewsus said:**
> Im wondering the same thing, but Im just about to try Ember through WINE on Lucid. 
Ill report back, but I hope to hear that there is a nice Open Source alternative.

Drew

Any luck?

I've tried installing tvrename via WINE before, but never got it working.  Spent a while chasing .NET compatibility issues down the rabbit hole.  

There seems to be a promising bit of open source software called Universal Media Manager in the works, but it's still pre-alpha.

I think at this point, our best bet is a virtual windows 7 installation.  I'm hoping it won't be too tricky to get Ember to play nicely with my ext4-formatted media drive.

---

### Post by drewsus on 2010-05-02
> **knidsrok said:**
> Any luck?

I've tried installing tvrename via WINE before, but never got it working.  Spent a while chasing .NET compatibility issues down the rabbit hole.  

There seems to be a promising bit of open source software called Universal Media Manager in the works, but it's still pre-alpha.

I think at this point, our best bet is a virtual windows 7 installation.  I'm hoping it won't be too tricky to get Ember to play nicely with my ext4-formatted media drive.

I ended up installing Ember within XP via VirtualBox. Worked great!
Set up the folders I wanted to scrape as shared folders and just pointed Ember to the proper folders for Movies and TV Shows. Worked like a dream!!

---

### Post by drewsus on 2010-05-22
Update: Ive been using FileBot (Java) instead of theRenamer

And just to save you a bit of time, for the renaming format, this is the regular expression I used: 
```
/home/drewsus/Videos/TV Shows/{n}{'/Series '+s.pad(2)}/{n} - {'S'+s.pad(2)}E{e.pad(2)} - {t}
```
[SIZE="4"][COLOR="Red"]BUT CHANGE **drewsus** TO YOUR USERNAME!![/COLOR][/SIZE]
Which will give you for example:
/home/drewsus/Videos/TV Shows/Dark Angel/Series 03/Dark Angel - S03E01 - Labyrinth
(and will not include "Series ##" and "S##" if the show is not part of a set of Series')
There website has more details on formatting, but this works well with Ember (which I am still using in VirtualBox)

Hope this helps some!

---

