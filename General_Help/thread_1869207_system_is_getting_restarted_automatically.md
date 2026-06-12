---
title: "system is getting restarted automatically"
date: 2011-10-25
forum: General Help
---

### Post by c2tarun on 2011-10-25
Hi friends
I am using ubuntu 10.04 on my machine. My machine is bit old and slow so I cannot use latest version of ubuntu.

I am facing a strange problem, after using system for sometime my system automatically gets restarted.
Its not exactly a restart, I see a message of
* checking batter state
like we see when we shutdown laptop. Then everything goes blank and screen starts blinking with black and white strips in the top half portion

I am using computer and not a laptop, why am I seeing that message?
And why I am facing this problem, is there any way to look at the logs and get more information about what is happening?

---

### Post by zvacet on 2011-10-25
It is not really answer to your question,but if you have old comp then you can try to install lubuntu-dsktop.

```
sudo apt/get install lubuntu-desktop
```

If you want to remove gnome read [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

I was running ubuntu with LXDE on 192MB of ram.

---

### Post by c2tarun on 2011-10-25
> **zvacet said:**
> It is not really answer to your question,but if you have old comp then you can try to install lubuntu-dsktop.

```
sudo apt/get install lubuntu-desktop
```

If you want to remove gnome read [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

I was running ubuntu with LXDE on 192MB of ram.

so you do think that gnome is putting too much pressure on my system and that's why its getting restarted? There is nothing related to kernel?

---

### Post by zvacet on 2011-10-26
I don't know if that is kernel issue but with lubuntu your system will be faster if you have old comp with small ram.And correct command is

```
sudo apt-get install lubuntu-desktop
```

---

### Post by c2tarun on 2011-10-26
> **zvacet said:**
> I don't know if that is kernel issue but with lubuntu your system will be faster if you have old comp with small ram.And correct command is

```
sudo apt-get install lubuntu-desktop
```

I installed lubuntu-dsktop usin synatic but that problem persists.
A new problem is also started, now its whenevr I start the system a new untitled window is trying to open and my whole compter is blinking due to that. Can anyone pleasehelp

---

### Post by mastablasta on 2011-10-26
open the computer and check for any leaking or bulging capacitors. they could be on motherboard or graphics card. since you report strange lines etc. they could likely be faulty capacitors on graphics card. this is well known issue with a bit older mashcines. see here for more info on this and pics: [http://en.wikipedia.org/wiki/Capacitor_plague](http://en.wikipedia.org/wiki/Capacitor_plague)
 
it might not be this but sure sounds like it.
 
another thing can be overheating. make sure you clean all ventilators and vents and if necessary apply additional cooling paste to processor.
 
 
Lubuntu is light, however if you plan to use it longer it is better to do a fresh install and also you should use latest version. the 10.04 version was still more of experimental nature in term of system software bundled with it.

---

