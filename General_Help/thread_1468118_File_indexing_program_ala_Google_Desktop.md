---
title: "File indexing program ala Google Desktop"
date: 2010-05-01
forum: General Help
---

### Post by prshah on 2010-05-01
Hello,

I am using Ubuntu Lucid 64-bit.

I've just finished a new install, and would like to install a file indexing / search package similar to Google Desktop.

I know Google Desktop is available for Linux, but would prefer an open-source application, such as beagle. The problem with beagle is that it is apparently not being maintained.

Are there any (modern) alternatives or should I stay with Google Desktop?

Please advise, thanks in advance:

---

### Post by gogolink on 2010-05-25
I have the same problem.  I have tracker search tool installed (which worked for me on karmic) -- but have no idea how to actually get it to index my files.  Feel totally stupid about that...

Would it be more modern to use gnome-do to search file content?  Can anyone share their experience with that?  (Or recent experience with tracker, beagle, or anything similar...)

---

### Post by BoneKracker on 2010-05-25
I find Secure Locate (slocate) more than adequate.  But, if by "modern" you mean "gui", that ain't it.

---

### Post by gogolink on 2010-05-25
Actually, tracker search tool seems to be working fine now.  I had enabled indexing under system > preferences > search and indexing, and restarted the daemon (as I was prompted to); that didn't seem to do it at first -- but I guess I was just too impatient.  Now it's indexing.

---

### Post by BoneKracker on 2010-05-25
It is probably set up to only index when the system is below a certain load level, or to operate at a certain "nice" level.  In other words, it gives way either when the system is working hard or when higher-priority tasks are being performed.  I see there's a "throttle" control in the configuration dialogs; it probably adjusts this.

---

### Post by jerenept on 2010-05-25
In order to index files, you need to open a terminal and enter 
```
sudo updatedb -v
```
and enter your password.
you will not get any visual feedback for the password. This is normal.
It will list each file it is indexing.
you can then go to 
Places>Search for Files and search
PS I am pretty sure this gets done automatically.... this is just a manual way to index the files

---

### Post by BoneKracker on 2010-05-25
> **jerenept said:**
> ```
sudo updatedb -v
```
That's just indexing for 'locate' and its variants (locate, slocate, rlocate, etc., depending on what you have installed).

---

### Post by Phocean on 2010-07-09
Same problem.
I have tested all the indexing programs around, and the only ones that do the work are Google Desktop and Beagle.

Tracker was an I/O monger, the gui is still behind and its results are not good.

Beagle is now pretty mature, discrete and indexes very well. So does Google desktop but it does not integrate very well on the desktop.

As Beagle is not actively maintained anymore, we are left with not much choice. I keep using it because it is the best, but aready we are lacking of the beagle addon for Firefox to index web surfing, as it is not compatible anymore with the latest version of Firefox.

Oh and it is funny to see that on every post about content indexing, some guys come up with locate or "I am rather organized so I don't need indexing at all"
It seems that they will never get the point.
I am organized, I know locate but I do need Beagle for my dayly work !

---

### Post by sgage on 2010-07-09
I've tried them all, and settled on recoll (it's in the repos). It is fast, gets good results, doesn't bog down the system, and can accomodate "helper apps" in order to index many kinds of files.

---

### Post by prshah on 2010-07-09
> **sgage said:**
> settled on recoll (it's in the repos). It is fast, gets good results, doesn't bog down the system, and can accomodate "helper apps" in order to index many kinds of files.

Wow, recoll looks good, based on it's wiki'd features. But it seems to be designed for KDE (qt, kicker applet), which means that for now atleast, I'll be sticking to [s]Gnome-Do[/s] Google Desktop.

---

### Post by Phocean on 2010-07-10
What do you mean by sticking Gnome-Do ? I may be missing something, but AFAIK it does index content at all...

---

### Post by prshah on 2010-07-10
> **Phocean said:**
> Gnome-Do ? AFAIK it does index content at all...

An unfortunate error; I meant Google Desktop. Physically here, mentally elsewhere...

---

### Post by tellapu on 2010-11-17
Has somebody found an applet or a tool that works with recoll (personal full text search), so you can search quicker (like with google desktop or beagle)?
Or is there a possibility to configure a hotkey (like F12) to start recoll quickly?

---

