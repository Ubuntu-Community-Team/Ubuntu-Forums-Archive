---
title: "Installing .tar.gz and other terminal things that i dont seem to understand!!"
date: 2009-11-10
forum: General Help
---

### Post by KennyGJE on 2009-11-10
Can someone explain to me very detailed(screenshots would help) how to install flash player 10 with the .tar.gz thingy , since the .deb wont work. Please help me with this, if u watch my other topic you'll see the problems i've got.

---

### Post by Bunnybugs on 2009-11-10
Go to your terminal (Applications>Accesories>Terminal) and type:

```
**sudo apt-get install flashplugin-nonfree**

```

This will install your flashplayer!

---

### Post by 73ckn797 on 2009-11-10
> **KennyGJE said:**
> Can someone explain to me very detailed(screenshots would help) how to install flash player 10 with the .tar.gz thingy , since the .deb wont work. Please help me with this, if u watch my other topic you'll see the problems i've got.


Try this link:
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

Do you have restricted extras loaded? That would include flash.

---

### Post by BarisBlaq on 2009-11-10
Try running up Synaptic and installing "flashplugin-installer" package. It's a meta package that installs the lates supported for Ubuntu.

No need to deal with debs or tarballs imo.
=)

---

### Post by KennyGJE on 2009-11-10
> **BarisBlaq said:**
> Try running up Synaptic and installing "flashplugin-installer" package. It's a meta package that installs the lates supported for Ubuntu.

No need to deal with debs or tarballs imo.
=)
I've tryed it didnt work.

---

### Post by KennyGJE on 2009-11-10
> **Bunnybugs said:**
> Go to your terminal (Applications>Accesories>Terminal) and type:

```
**sudo apt-get install flashplugin-nonfree**

```This will install your flashplayer!
That didnt work either!:(
[IMG]http://i33.tinypic.com/2jahmv8.png[/IMG]

---

### Post by BarisBlaq on 2009-11-10
Could you translate what it says in the screen shot there?
=))

---

### Post by KennyGJE on 2009-11-10
> **BarisBlaq said:**
> Could you translate what it says in the screen shot there?
=))
it says it couldnt find the package flashplayer-nonfree

---

### Post by BarisBlaq on 2009-11-10
Run Synaptic, from menu Setttings, then Repositories, and make sure "multiverse" is checked?

---

### Post by KennyGJE on 2009-11-10
> **BarisBlaq said:**
> Run Synaptic, from menu Setttings, then Repositories, and make sure "multiverse" is checked?
I didnt find anything saying multiverse, could u tell me like the other guy did like system=>Sympatic... That way?? :P It seems everything that shuld be checked is checked to me, just tell me where to find it so that i can make sure .. :P

---

### Post by Bunnybugs on 2009-11-10
[IMG]http://i34.tinypic.com/bai42.png[/IMG]

That's what it says... been looking on the net, but can't find the solution... came to think about it, it doesn't work over here either... got myself a great headbreaker!8)

---

### Post by BarisBlaq on 2009-11-10
System > Administration > Synaptic package manager
Then
Settings > Repositories
And make sure 4th from top "Software restricted by copyright (multiverse)" is checked.


I think that might be the problem, but I'm not 100% sure.

---

### Post by Bunnybugs on 2009-11-10
> **KennyGJE said:**
> I didnt find anything saying multiverse, could u tell me like the other guy did like system=>Sympatic... That way?? :P It seems everything that shuld be checked is checked to me, just tell me where to find it so that i can make sure .. :P

Run Synaptic, go to the menu bar, select 'Edit', and go to 'Mark all upgrades'

If everything is fine, this will upgrade flashplayer, if you have installed some of it already through synaptic

---

### Post by SuperSonic4 on 2009-11-10
> **Bunnybugs said:**
> Go to your terminal (Applications>Accesories>Terminal) and type:

```
**sudo apt-get install flashplugin-nonfree**

```

This will install your flashplayer!

> **BarisBlaq said:**
> Try running up Synaptic and installing "flashplugin-installer" package. It's a meta package that installs the lates supported for Ubuntu.

No need to deal with debs or tarballs imo.
=)

> **BarisBlaq said:**
> Run Synaptic, from menu Setttings, then Repositories, and make sure "multiverse" is checked?

How about answering the question guys? :lolflag:

0. Are you using 32bit or 64bit. use ```
uname -m
``` to find out. Paste here if unsure


**64 bit**

```
wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

Navigate to the directory you downloaded it to (although wget uses the current folder)

```
tar -xvzf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

```
mkdir ~/.mozilla/plugins
``` (if this errors ignore it - it means the directory exists which is fine

```
mv -v libflashplayer.so ~/.mozilla/plugins
```

Restart firefox


**32 bit**

```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz

```

Navigate to the directory you downloaded it to (although wget uses the current folder)

```
tar -xvzf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

```
mkdir ~/.mozilla/plugins
``` (if this errors ignore it - it means the directory exists which is fine

```
mv -v libflashplayer.so ~/.mozilla/plugins
```

---

### Post by KennyGJE on 2009-11-10
Allright, but the 32bit or 62bit doesnt matter now cuz I just figured it out :D When I went to check if that thing was checked I noticed a scroll down list, wich said Download from: and then I scrolled down to Main server, it was on the Norwegian Server! So then I got all these updates and stuff and now it works :D Thanks alot guys, couldnt have done it without you ):P

---

