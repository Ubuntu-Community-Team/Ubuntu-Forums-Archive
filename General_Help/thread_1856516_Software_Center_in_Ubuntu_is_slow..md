---
title: "Software Center in Ubuntu is slow."
date: 2011-10-08
forum: General Help
---

### Post by galacticaboy on 2011-10-08
I am using Ubuntu 11.04 and my Software Center is extremely slow. Why is that, it is like that with any of the Ubuntu Versions I have installed. Is that a bug or just my PC.

---

### Post by mibart on 2011-10-08
Perhaps Your computer is just old and slow? I don't find Software Center particularly slow, it behaves like any other application.

---

### Post by galacticaboy on 2011-10-08
When I install .deb files it goes super slow, or just install stuff from there in General, I use Synaptic to access the Repos or the terminal, and to install .deb files, I use GDebi, it is way faster.

---

### Post by Elfy on 2011-10-08
I've always found on the few occasions I've tried it that it was slow - or at least appeared to be so.

---

### Post by galacticaboy on 2011-10-08
I want to just remove it, but when I tried, it wanted me to remove the whole Ubuntu Desktop... it was weird, I don't want to break anything.

---

### Post by Elfy on 2011-10-08
If it's part of the default ubuntu-desktop then removing it will remove ubuntu-desktop, that though is a meta package. Nothing to worry unduly about. 

If in future you were going to upgrade to a new version I would be inclined to put it back.

---

### Post by galacticaboy on 2011-10-08
> **forestpiskie said:**
> If it's part of the default ubuntu-desktop then removing it will remove ubuntu-desktop, that though is a meta package. Nothing to worry unduly about. 

If in future you were going to upgrade to a new version I would be inclined to put it back.

I'm going to keep it because I find it handy for reviews on software, but for the most part I use Synaptic or the Terminal. I was just wondering if it was just my PC or if it was something everyone is experiencing.

---

### Post by Linuxisfast on 2011-10-08
It is slow and I always use Synaptic or cli, when I needs specific info then I open software center and check out the programs but I always install via cli or synaptic.

---

### Post by dcstar on 2011-10-08
> **galacticaboy said:**
> I am using Ubuntu 11.04 and my Software Center is extremely slow. Why is that, it is like that with any of the Ubuntu Versions I have installed. Is that a bug or just my PC.

There can be a problem when your selected repository does not handle "Translation" files correctly for your locale, it may help if you do this on your system in a terminal:

```
cd /etc/apt/apt.conf.d
gksudo gedit 80http
```
and add in the following code:
```
Acquire::http::Pipeline-Depth "0";
Acquire::http::No-Cache "true";
Acquire::http::Max-Age "0";
```
Save the file and restart Synaptic/Update Manager/Software Center and see if things are any better.

---

