---
title: "Server Mirroring"
date: 2006-01-24
forum: General Help
---

### Post by mybers on 2006-01-24
Hi!

I would like to set up a secondary server with a complete mirror of my
main production machine. In case the first one fails I could (manually)
do a switchover. I don't need things like balancing, IP-takeover, etc.

The ideal solution should include automatic, online mirroring
of all file changes from master server to the secondary one.

What is your suggestion to solve the problem? Can Ubuntu server do this? if not can anyone suggest a linux distro capable of doing this.

Thanks in advance to all.


mybers

---

### Post by briancurtin on 2006-01-24
you are probably better off looking in the server area of this site, since this isnt much of a GNOME problem

---

### Post by shakin on 2006-01-24
[QUOTE=mybers]Hi!

I would like to set up a secondary server with a complete mirror of my
main production machine. In case the first one fails I could (manually)
do a switchover. I don't need things like balancing, IP-takeover, etc.

The ideal solution should include automatic, online mirroring
of all file changes from master server to the secondary one.

What is your suggestion to solve the problem? Can Ubuntu server do this? if not can anyone suggest a linux distro capable of doing this.

Thanks in advance to all.


mybers[/QUOTE]

I think the easiest way to do it is to identify which directories you want mirrored. Eg. MySQL, web site files, uploads, etc. and then use rsync to mirror them. Mirroring the core system isn't necessary. Rsync is good because it only copies changed parts of files, so after the initial rsync that gets all the files it will work really quick.

---

