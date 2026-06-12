---
title: "apt-get update error"
date: 2012-04-09
forum: General Help
---

### Post by whynot on 2012-04-09
Hi
I have a ubuntu system 11.10 x64 but when i try to update it gives 
NO_PUBKEY 2EA8F35793D8809A
this error. 
Is it possible anyway to add this key?
Thanks.

---

### Post by wojox on 2012-04-09
> **whynot said:**
> Hi
I have a ubuntu system 11.10 x64 but when i try to update it gives 
NO_PUBKEY 2EA8F35793D8809A
this error. 
Is it possible anyway to add this key?
Thanks.

Sure, open your terminal (Ctrl+Alt+T):
```
gpg --keyserver pgpkeys.mit.edu --recv-key  2EA8F35793D8809A     
```
```
gpg -a --export 2EA8F35793D8809A | sudo apt-key add -
```

---

### Post by whynot on 2012-04-09
> **wojox said:**
> Sure, open your terminal (Ctrl+Alt+T):
```
gpg --keyserver pgpkeys.mit.edu --recv-key  2EA8F35793D8809A     
```
```
gpg -a --export 2EA8F35793D8809A | sudo apt-key add -
```

Great job !
Thanks a lot and what about this errors? i removed some of the source list links but i couldn't figure it out.

[http://ppa.launchpad.net/alanbell/unity/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/alanbell/unity/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

[http://ppa.launchpad.net/alanbell/unity/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/alanbell/unity/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

[http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

[http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

---

### Post by wojox on 2012-04-09
If you go into Update Manager -> Settings -> Software Sources -> Other Software, you can remove those ppa's. :p

---

### Post by whynot on 2012-04-11
> **wojox said:**
> If you go into Update Manager -> Settings -> Software Sources -> Other Software, you can remove those ppa's. :p

Thanks.

---

