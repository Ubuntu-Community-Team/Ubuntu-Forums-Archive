---
title: "Unable to login after removing Unity"
date: 2011-04-22
forum: General Help
---

### Post by blairm on 2011-04-22
Hi,

Decided to give Unity desktop a try this afternoon on my Maverick desktop - bad mistake. Found it very slow so I removed it. After that I restarted and all I get after logging in is a white screen.

I don't get an option at login to use KDE or anything else for that matter, so I'm hoping someone can give me some idea how I can rectify this.

Really don't want to wipe the install and start over because I don't have a separate home partition (think I've learned my lesson on that front) and there's a lot of stuff I need to keep on this machine.

Cheers,

Blair

---

### Post by blairm on 2011-04-22
Don't like replying to my own posts, but for anyone else who strikes this probem, here's what worked for me:

sudo apt-get remove gnome shell

That response said gnome shell couldn't be found, but it suggested that I run sudo apt-get autoremove to get rid of a bunch of stuff - which I did.

After doing that did I did sudo apt-get unity (just in case) and then sudo restart gdm. 

Cheers,
 
Blair

---

