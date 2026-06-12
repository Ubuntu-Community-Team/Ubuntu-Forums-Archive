---
title: "ubuntu 12.04 networking issues (wireless / wired)"
date: 2012-05-24
forum: General Help
---

### Post by procfs on 2012-05-24
Hi,
I've just bought a new lenovo e420 and installed ubuntu 12.04 LTS on it. but I have weired networking issues as follows, ... 

[LIST]
[*]**home network**: wired connection is ok , but wireless is not ( connection establishes, but no ping or any access to the network ! as you may have noticed, others have the same problem too, like [here]("http://ubuntuforums.org/showthread.php?p=11960306")  , or [here]("http://ubuntuforums.org/showthread.php?t=1984317&highlight=lenovo+wireless+problem") , or [here]("http://ubuntuforums.org/showthread.php?t=1983054") )
[*]**office network** : no wired connection ! ( the exact same problem with wifi , I mean the connection is ok but there's no access to network )
[/LIST]
some tips ...

[LIST]
[*]the network configurations and routes are ok. for example the routes is the same as a PC which is already connected in the office network
[*]I've edited the NetworkManager.conf and removed the dns=dnsmasq ( to change /etc/resolv.conf and .... )
[*]no soft/hard blocked in rfkill list command
[/LIST]
I think it's a general networking bug ( not just a wireless issue) , any help ?
thanks in advance :)

---

### Post by procfs on 2012-05-24
hi again, 
let me add another thing that might help ...
( @office - wired connection )
```

root@laptop:~# tracepath 4.2.2.4
 1:  laptop.local                                     0.158ms pmtu 1500
 1:  laptop.local                                   2999.415ms !H

```

---

