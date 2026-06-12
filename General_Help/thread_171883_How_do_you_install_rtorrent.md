---
title: "How do you install rtorrent?"
date: 2006-05-07
forum: General Help
---

### Post by aeroshadow on 2006-05-07
Could someone walk me through this? Like, a list a steps would be fine.

- I got the tar.gz of libtorrent, tar'd it, cd'd into the directory, ./configure'd, make'd, make install'd, and make clean'd. Anyways, I think I installed it correctly, but I remember seeing some errors when I make'd it.

- I got the tar.gz of rtorrent, tar'd it, cd'd into the directory, and when I tried to ./configure, I got this:

checking for sigc++-2.0 libtorrent >= 0.8.0... Package libtorrent was not found in the pkg-config search path. Perhaps you should add the directory containing `libtorrent.pc' to the PKG_CONFIG_PATH environment variable No package 'libtorrent' found
configure: error: Library requirements (sigc++-2.0 libtorrent >= 0.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

What do I do?

---

### Post by testube_babies on 2006-05-07
Have you tried installing rtorrent through Synaptic?  It's in one of the extra repositories:

[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by aeroshadow on 2006-05-07
Huh? I'm pretty sure I have most of the repositories... which one exactly is it?

---

### Post by aeroshadow on 2006-05-08
I think rtorrent is only in the Dapper Drake repositories.

---

### Post by aeroshadow on 2006-05-08
Alright, I pretty much got it down; I just needed to use a little bit of "sudo" when make install'ing.

Could someone help me with which IP addresses to put in for the configuration files?

# The ip address reported to the tracker.
#ip = ?

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = ?

---

### Post by Gonzakpo on 2006-07-06
leave it blank.


Finally did you installed it from the repositories? or from their web page (latest version, it has to be built of course) ?

Because I want to install de latest version, but I'm not that experienced in linux. Should I install the sigc++2.0 lib ?

---

### Post by dimatrod on 2006-07-11
I can't somehow manage to make rtorrent work.  I used [the site's](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest&format=raw) original .rtorrent.rc file, only to enable the checking directory and saving in one directory (just for having it around, rtorrent complained when it didn't see this file), and it doesn't start torrents.  I then try dragging .torrent files to rtorrent, to no avail.  I installed it from the repos on Dapper by the way.

---

