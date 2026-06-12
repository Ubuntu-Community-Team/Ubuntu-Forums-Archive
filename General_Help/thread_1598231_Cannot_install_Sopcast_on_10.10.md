---
title: "Cannot install Sopcast on 10.10"
date: 2010-10-16
forum: General Help
---

### Post by davo2001 on 2010-10-16
Hi all, 

I can't seem to install sopcast on 10.10. i enter:

"sudo apt-get update && sudo apt-get install sopcast-player sp-auth"

and its results in:

"Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead."


Same process works fine in 10.04 LTS.

Any pointer are welcome.

---

### Post by happyisland on 2010-10-16
I have the same problem in 10.10. Sopcast worked perfectly in 10.04...

---

### Post by kinka-dzs on 2010-10-18
The problem is due with the python bindings for VLC (the player).

Check this blog, **'Mazebane'** looks very active on it,

[http://blog.mattrudge.net/2010/10/11/sopcast-player-on-ubuntu-10-10-maverick-meerkat/]("http://blog.mattrudge.net/2010/10/11/sopcast-player-on-ubuntu-10-10-maverick-meerkat/")

**Meanwhile someone found a workaround using ruby:**
[http://www.sablog.me/post/1237588407/sopcast-ubuntu-maverick]("http://www.sablog.me/post/1237588407/sopcast-ubuntu-maverick")

hope someone finds a solution soon... trying myself too.

---

### Post by kinka-dzs on 2010-10-20
works now:
[http://blog.mattrudge.net/2010/10/11...erick-meerkat/]("http://blog.mattrudge.net/2010/10/11...erick-meerkat/")

---

### Post by sabotatore on 2010-10-21
> **kinka-dzs said:**
> 
**Meanwhile someone found a workaround using ruby:**
[http://www.sablog.me/post/1237588407/sopcast-ubuntu-maverick](http://www.sablog.me/post/1237588407/sopcast-ubuntu-maverick)

 Hello, I packet it to .deb package sopcast-runner and public on launchpad [URL="http://git.sablog.me/sopcast-runner/"]http://git.sablog.me/sopcast-runner 
[/URL]

---

### Post by happyisland on 2010-10-24
> **kinka-dzs said:**
> works now:
[http://blog.mattrudge.net/2010/10/11...erick-meerkat/]("http://blog.mattrudge.net/2010/10/11...erick-meerkat/")

This worked for me. Thanks guys!

---

