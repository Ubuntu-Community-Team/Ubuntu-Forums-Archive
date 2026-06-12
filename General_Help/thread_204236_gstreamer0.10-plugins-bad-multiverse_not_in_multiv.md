---
title: "gstreamer0.10-plugins-bad-multiverse not in multiverse repos ..?!"
date: 2006-06-26
forum: General Help
---

### Post by Loungefly on 2006-06-26
Hellooo,

I'm currently setting up all my plugins for multimedia and I have everything pretty much done except that I just noticed that gstreamer0.10-plugins-bad-multiverse is nowhere to be found in multiverse. I have all my extra repos active (backports, PLF, universe, multiverse etc) and  it's not listed :???: 

Does anyone know if it's been removed, or possibly moved to some other repo  somewhere else?

Any help would be greatly appreciated

---

### Post by mlind on 2006-06-26
[QUOTE=Loungefly]Hellooo,

I'm currently setting up all my plugins for multimedia and I have everything pretty much done except that I just noticed that gstreamer0.10-plugins-bad-multiverse is nowhere to be found in multiverse. I have all my extra repos active (backports, PLF, universe, multiverse etc) and  it's not listed :???: 

Does anyone know if it's been removed, or possibly moved to some other repo  somewhere else?

Any help would be greatly appreciated[/QUOTE]

```

$ apt-cache policy gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-bad-multiverse:
  Installed: 0.10.3-3
  Candidate: 0.10.3-3
  Version table:
 *** 0.10.3-3 0
        500 http://fi.archive.ubuntu.com dapper/multiverse Packages
        100 /var/lib/dpkg/status

```

It's there on multiverse, I just tried reinstalling it worked out fine

---

### Post by Loungefly on 2006-06-26
Ahh, that's it.

I just realized it's not in the Australia mirror of multiverse. I put your mirror in my sources and I have it now :)

Thanks so much for that :)

---

