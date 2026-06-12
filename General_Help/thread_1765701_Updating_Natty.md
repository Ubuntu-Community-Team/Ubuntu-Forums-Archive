---
title: "Updating Natty"
date: 2011-05-23
forum: General Help
---

### Post by paulmcg421 on 2011-05-23
Hey,

I've recently upgraged to 11.04 from 10.10(which was a smooth upgrade) but i've been recently getting an error when trying to update, doing it through the update manager it fails to download repository information telling me to check my Internet connection(and I assure you I am online) I've tried restarting my connection and computer but I get the same issue.

I then tried it through command line typing "sudo apt-get update" and it runs away connecting to headers until it gets to the end and I get error lines saying.

```

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```Anyone know why I'm getting this issue ?

---

### Post by snowpine on 2011-05-23
System->Administration->Software Sources and uncheck the box for the 10.10 CD-ROM.

Alternately, edit /etc/apt/sources.list with your favorite text editor and delete that line from the file.

---

### Post by paulmcg421 on 2011-05-23
that did that trick, thanks a bunch ! ! :)

---

