---
title: "No text in GNOME due to a Gentoo locale mixup"
date: 2009-09-10
forum: General Help
---

### Post by night_fox on 2009-09-10
Hi, I've just installed Gentoo on my laptop in such a way that Gentoo and Ubuntu share my home directory. GNOME on Gentoo changed my locale to something en_GB, but when I booted into Ubuntu and logged in, no text was visible, not even in firefox.

How can I get my text back in a way that works with both ubuntu and gentoo?

P.S. I don't really understand what a locale is.

---

### Post by night_fox on 2009-09-11
bump

---

### Post by ankspo71 on 2009-09-11
Hi,
Did you try to change the locale in Gentoo to see you could get the locales to match? Btw, I don't even know how you were able to share your home directory with another linux distro. If sharing your home directory is a must, you should try that with a debian/ubuntu based distro. If I remember right, Gentoo is quite different of a linux. Sorry I can't be of more help.
James

---

### Post by ankspo71 on 2009-09-11
Ooooh Ok. Now I know how you shared your /home directory. You did it during setup where you told gentoo to use ubuntu's (or vice versa) /home partition and told it not to reformat it. I never thought of doing that before. You might have better luck syncing your files to each distro (rather than sharing an entire system partition), or create a non system partition to share all of your files. I hope someone has an easy fix for you.
James

---

### Post by night_fox on 2009-09-11
Thanks for replying ankspo71. Sharing the home directory is an absolute must and some stupid locale problem shouldn't stop me from doing it.

This is really annoying. The only sudoer is the user for whom no text appears, and I haven't installed wireless internet in gentoo. So I think I'll add a user in gentoo, do the whole gentoo gnome thing and see what files gentoo gnome spews out.

---

### Post by ankspo71 on 2009-09-11
Actually, creating different users for each distro *might* help you. I mean, in Ubuntu you could create username(a) and Gentoo make username(b). Maybe they won't clash that way, but then you wouldn't have the same user's home folder either. I suppose this would only help if the locales are stored in the /home/<user>/ directory anyways.

I'm wondering if Gentoo isn't using the same fonts as Ubuntu too, or maybe the same fonts aren't installed. You fight need to check that out too.

Hope you get it working.
James

---

### Post by night_fox on 2009-10-06
It was a stupid gconf thing that gentoo changed.

---

