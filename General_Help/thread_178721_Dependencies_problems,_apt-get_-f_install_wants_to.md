---
title: "Dependencies problems, apt-get -f install wants to remove everything!"
date: 2006-05-18
forum: General Help
---

### Post by TFleck on 2006-05-18
The problem started when I tried to install orpheus, and it wasnt avaliable in my repositories. I downloaded the package from here: [http://packages.ubuntulinux.org/dapper/sound/orpheus](http://packages.ubuntulinux.org/dapper/sound/orpheus)
It required some dependecies, so I downloaded them from de same website.They were: libgcc1, libghttp1 and gcc-4.0-base
Everythink went fine.
But when I opened synaptic, it said there were broken packeges. I tried to fix them with apt-get -f install. But It said it needed to remove several programs, gnome-desktop and firefox among them. And I answered 'yes'.
After removing almost 500mb of files, there were no more broken packages, but I wanted the programs removed back!
So I tried to install them. First one was firefox, It needed a dependency - libidl0 - and synaptic said it will not me installed. So I seached for the package and installed this one: [http://packages.ubuntu.com/breezy/libs/libidl0](http://packages.ubuntu.com/breezy/libs/libidl0)
Other ones were needed and I also installed them.
But, this time, when I tried to install firefox, synaptic said there were more broken packeges. I tried another sudo apt-get -f install. This time there were more programs to be removed, but I answed 'no'. Now i'm here trying to find a way to fix this.
What should I do?

---

### Post by raovq on 2006-05-18
check your repositories.

"sudo gedit /etc/apt/sources.list"

my bet is that you have a dapper repository in there.

something like this happened to me the other day.

---

### Post by tseliot on 2006-05-18
Type this and you will have back all the apps that come with Ubuntu by default:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by TFleck on 2006-05-18
I think I installed a dapper package, and thats making the conflict. But the problem is that when I try to remove that package it says that I need to remove almost everything intalled here.

---

### Post by TFleck on 2006-05-18
Is there a way to reinstall everething? I mean, removing all packages installed and get a fresh ubuntu, without formatting?

---

