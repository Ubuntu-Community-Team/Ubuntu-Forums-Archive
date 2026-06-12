---
title: "move old packages from local cache instead of remove?"
date: 2012-01-15
forum: General Help
---

### Post by loolooyyyy on 2012-01-15
hi, how can i "MOVE" old packaged (.deb) from /var/cache/apt/archives to another folder? (maybe /home/user/old-packs)
there is a command to totally remove them:
```
sudo apt-get autoclean
```apt-get autoclean: To remove all stored archives in your cache for packages that can not be downloaded anymore (thus packages that are no longer in the repository or that have a newer version in the repository).

however i want to **"move"** them

the output of auto clean is 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del lib**** x.y.z-7 [18.1 kB]
Del lib***** 4:0.1.2.30ubuntu1 [98.3 kB]
Del python 4:2.2.2-0ubuntu1 [662 kB]
.
.
.
.

```do you know a way to pipe it to mv? i'm not so good at shell scripting though

and by the way: autoclean does keep the archives i might need to reinstall (or even those i haven't installed yet), right?

---

### Post by Paqman on 2012-01-15
How bothered are you that it's only the old packages? Why not just copy the whole lot?

Btw, is there some reason you want to keep them? They're not really any use. If you want to install an older version of a package you can use Synaptic to grab the old version from the repos.

---

### Post by dino99 on 2012-01-15
Maybe you are as lazy as i am, so nautilus copy/paste is your friend. But do you really need to save packages ?

---

### Post by loolooyyyy on 2012-01-15
where i live internet fees are so high, paying about 350$ for what you only pay 7$
(and the speed i gain is 65KB/s at the best, not always, usually 50)
so every KBytes of archive i have downloaded is so precious to me, redownloading using synaptic is not an option.
and i do need my older version packages
so i just want the older archives out of that folder to one of my old external HDDs for later use and keep the newer ones right where they are

@dino: there are 8GB of archive/7800 packages, it can not be manually done
@paqman: i dont care about the backup itself, i want /var/cache/apt/archives/ as clean as possible

thanks to you both

---

### Post by Lars Noodén on 2012-01-15
Using varnish, squid or [apt-cacher](http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html) might help to reduce the amount that has to be downloaded a second time.  

It might be worth investing in a new router / modem where you can run server software like proxy/caches.  I've [built my own](http://www.bsdly.net/~lars/Viking/viking.html) and can run proxies, caches and torrents as I see fit.

---

