---
title: "Synaptic not showing some packages..."
date: 2009-07-17
forum: General Help
---

### Post by cupevampe on 2009-07-17
Hello everyone!

I've reinstalled Ubuntu 8.10 after some distro hopping and this morning had some troubles getting wifi to work properly so i had to play around installing backports and madwifi

now

i dont know if this is related, but synaptic is not showing me some stuff that should be there like:

abuse (the game)
conky

and then since i've added them to source
remastersys
gnome do

why dont they show up in synaptic?
Npow i've deleted most entries from my sources.list, then added the proper lines again, but the issue persists.

can you help?

many thx!

PS I even tried to createe my source.list using [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) and also added all gpg... still no conky in synaptic.

---

### Post by kostkon on 2009-07-17
Try using the full search option (the button next to the quick-search input field) and not the quick-search one which does not work well, especially for newly added repos.

---

### Post by cupevampe on 2009-07-17
Googling i found the answer...

[http://krisrowland.wordpress.com/2009/04/04/fixed-synaptic-not-showing-searching-all-packages/](http://krisrowland.wordpress.com/2009/04/04/fixed-synaptic-not-showing-searching-all-packages/)

sudo update-apt-xapian-index

yay!

---

