---
title: "Is it ok/possible to install 'oneiric' PPA pkgs on Natty?"
date: 2011-06-07
forum: General Help
---

### Post by icarus74 on 2011-06-07
Hi,

Would like to upgrade to the latest version of Midori, which apparently is 0.3.6-1ubunt1 on the development branch, and I guess should be available under this PPA:
[https://launchpad.net/ubuntu/oneiric/amd64](https://launchpad.net/ubuntu/oneiric/amd64)

I am running Natty, upgraded to everything latest, on amd64. Is it okay/possible to this latest dev version of Midori ? Could someone explain how I might be able to do it ? Also, what might be the steps to undo ?

cheerss,
Icarus

---

### Post by doas777 on 2011-06-07
TBH, I'm not sure, but I think it would be a bad idea. that PPA will likely have 11.10 versions of your core software and configs, so it will upgrade your existing files accordingly. 

if you have a PPA for an individual app (say mplayer or vlc) then I wouldn't be that worried about it, but that looks like the entire system root. make sure you have backups before experimenting.

---

### Post by mc4man on 2011-06-07
First of all that's not a ppa you've linked, just a search page in launchpad.

Generally speaking a poor idea to install from a higher ubuntu 'version' though in this case you could install O's **current** Midori package.

Better to look for an actual natty ppa that has the current version and use that - Ex. here
[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

---

### Post by wildmanne39 on 2011-06-07
> **icarus74 said:**
> Hi,

Would like to upgrade to the latest version of Midori, which apparently is 0.3.6-1ubunt1 on the development branch, and I guess should be available under this PPA:
[https://launchpad.net/ubuntu/oneiric/amd64](https://launchpad.net/ubuntu/oneiric/amd64)

I am running Natty, upgraded to everything latest, on amd64. Is it okay/possible to this latest dev version of Midori ? Could someone explain how I might be able to do it ? Also, what might be the steps to undo ?

cheerss,
Icarus
Hi, I am running oneric and it is just for testing.

---

### Post by nothingspecial on 2011-06-07
> **mc4man said:**
> 

Better to look for an actual natty ppa that has the current version and use that - Ex. here
[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

+1, do this


```
sudo add-apt-repository ppa:webkit-team
sudo add-apt-repository ppa:midori
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by icarus74 on 2011-06-07
> **nothingspecial said:**
> +1, do this


```
sudo add-apt-repository ppa:webkit-team
sudo add-apt-repository ppa:midori
sudo apt-get update
sudo apt-get upgrade
```

Worked like a charm. Thanks @nothingspecial & @mc4man.

---

