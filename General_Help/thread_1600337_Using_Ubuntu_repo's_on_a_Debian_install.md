---
title: "Using Ubuntu repo's on a Debian install?"
date: 2010-10-18
forum: General Help
---

### Post by AoSteve on 2010-10-18
I'm wanting a different OS to tinker with.  I was thinking just a plain ol` simple debian install; possibly a minimal.

Here's the question.   If I run a debian install; is there any way to install/use apt-get and the ubuntu repo's?

Reason being; there's a few deb's I'd like to keep around on both OS's and it would more then likely be easier to find in the ubuntu repo's then searching and/or compiling source.

---

### Post by mrtomservo on 2010-10-18
To my knowledge Debian uses apt-get already.  Debian should have very similar packages.  Could be wrong.  I think if you use the testing repositories for Debian you should be fine.

EDIT: If you already have your .deb 's, they should install just fine under Debian using the same tools you use in Ubuntu, ie, aptitude, dpkg, apt-get.

---

### Post by spikoley on 2010-10-18
Ubuntu is based off Debian and uses apt-get.  In fact, that is where Ubuntu got apt-get from.  You shouldn't have any issues finding programs for Debian.  Just install it normally and use Debian's repositories.

---

### Post by AoSteve on 2010-10-18
Hmm;  I thought it used pacman..  I hated pacman to be honest...  lol   I'll boot a vbox and check that out.   

Would it be able to pull packages from the ubuntu repo's in the case that the debian ones don't have the debs I need?

---

### Post by foxmulder881 on 2010-10-18
Debian uses apt and NOT pacman.

As above, you won't find much difference between the Debian repos and Ubuntu repos anyway. Perhaps a couple of differences in versions of software, but actual content should be almost 1:1.

---

### Post by AoSteve on 2010-10-18
[QUOTE=Debian Base Install Apt-Get command]This APT has Super Cow Powers.[/QUOTE]


YEAH!   It does have apt-get..  perfecto!   Out of all the different package managers I've played with so far; apt-get has been the easiest.

But to my suprise; as I figured...  One of the most needed is alarm-clock-applet which is my alarm for Ubuntu.   I'm not sure if I want to start looking up other names though.   Is it possible to just add the repo's in /etc/apt/sources.list ?

---

### Post by spikoley on 2010-10-18
> **AoSteve said:**
> But to my suprise; as I figured...  One of the most needed is alarm-clock-applet which is my alarm for Ubuntu.   I'm not sure if I want to start looking up other names though.   Is it possible to just add the repo's in /etc/apt/sources.list ?

I don't think its a good idea to mix the repositories because of differences in versions.

The best solution is to look for the .deb.

---

### Post by AoSteve on 2010-10-18
That's what I'm getting at in all respect.  I only need probably...  7 packages total to get the things I need and have a solid install of "my" setup.   Plus; the standard distro of debian right now; lenny I believe, only had gnome 2.2 if I'm correct here.   I always have gnome, whether or not I use it is a different story.   :)

---

### Post by cascade9 on 2010-10-18
> **AoSteve said:**
> YEAH! It does have apt-get.. perfecto! Out of all the different package managers I've played with so far; apt-get has been the easiest.

But to my suprise; as I figured... One of the most needed is alarm-clock-applet which is my alarm for Ubuntu. I'm not sure if I want to start looking up other names though. Is it possible to just add the repo's in /etc/apt/sources.list ?

Its in debian- 

[http://packages.debian.org/search?keywords=alarm-clock](http://packages.debian.org/search?keywords=alarm-clock)

BTW, +1 spikoley...its not a good idea to mix ubuntu and debian repos.  

> **foxmulder881 said:**
> Perhaps a couple of differences in versions of software, but actual content should be almost 1:1.
 
 There would be more than a 'couple' differnces in the versions. ;) 

> **AoSteve said:**
> That's what I'm getting at in all respect.  I only need probably...  7 packages total to get the things I need and have a solid install of "my" setup.   Plus; the standard distro of debian right now; lenny I believe, only had gnome 2.2 if I'm correct here.   I always have gnome, whether or not I use it is a different story.   :)

I think you are getting GTK+ and gnome mixed up. Lenny has gnome 1.2.22.2, GTK+ 2.12.11.

---

