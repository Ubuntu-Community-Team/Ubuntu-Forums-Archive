---
title: "Install gcc 4.6 safely"
date: 2011-09-29
forum: General Help
---

### Post by MattPhillips on 2011-09-29
Hi,

I'm using 10.04 (will probably wait for 12.04 to upgrade) and I want to install the latest version of gcc.  I currently have 4.4.3, and when I try apt-get upgrade or anything like that it tells me that I already have the newest version.  Now, going to the website and downloading gcc 4.6 is straightforward enough, but I've seen a lot of posts where people have gotten into trouble trying to just to a simple install of a new version of gcc on top of an old one (which is pretty much all I know how to do).  I develop in Qt fwiw though this is presumably a general issue.  But problems will be along the lines of Qt not being able to find gcc or something like that.

So could anyone tell me a 'safe' way to manually upgrade gcc, since there doesn't seem to be a way to do it using standard tools?  And the simpler/step-by-stepwise the explanation, the better. :)

---

### Post by Phantom7748 on 2011-12-20
I know this thread is a couple months old, but I would also like to know this, just got Bit.Trip Runner through the Humble Indie Bundle, but it returns the error that I need glibcxx 3.4.15, which I believe is in gcc-4.6. I'm not to great with compiling from scratch, and I don't want to break previous versions.

Edit: I am still running 10.04 as well. So I can't go to a package manager and upgrade.

---

### Post by Yudley on 2012-01-21
Bump. I need gfortran-4.6 on my lucid (10.04) badly ... don't wanna compile

Don't wanna disturb the existing 4.4.3 ecosystem ... (I wanna invoke it as gfortran-4.6 on the command-line while gfortran still points to 4.4.3)

Any ideas for side-by-side "safe" setup/install?

we can do it for older versions (I already have 4.4.3 and 3.4.6) why can't we do it for newer ones?

---

