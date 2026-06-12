---
title: "How do I get rid of pointless KDE libraries?"
date: 2012-01-23
forum: General Help
---

### Post by silverhaze06 on 2012-01-23
I downloaded kaffine a few days ago while testing out some media players and have since removed it. but even after that, when the update manager opens, it lists A TON of kde libraries I dont need since I have ubuntu and no more kde applications installed. I looked in my software sources but I dont see anything that would make all these kde libs pop up. Or is there something else that I'm missing?

---

### Post by snowpine on 2012-01-23
IF these libraries were installed as "dependencies" of kaffine, and you have removed kaffine, then you should be able to remove them with:

```
sudo apt-get autoremove
```

For more details

```
man apt-get
```

Keep in mind... there is no HARM to not removing these libraries (except a little bit of disk space and bandwidth) but a small possibility of breakage if you remove something because you don't understand what it's for but then decide later that you really needed it after all. ;)

---

### Post by silverhaze06 on 2012-01-23
I just tried ```
apt-get autoremove
``` and ```
apt-get autoclean
``` but the kde libs are are still coming up in the update manager.

---

### Post by Basher101 on 2012-01-23
you could disable certain packages from the recommended updates but i do not remember where and how...i kinda found it by accident back then...


but if i remember correctly, i gave you a warning that the update manager would spam you with recommended kde updates if you were to install a kde app right?

---

### Post by silverhaze06 on 2012-01-23
> **Basher101 said:**
> you could disable certain packages from the recommended updates but i do not remember where and how...i kinda found it by accident back then...


but if i remember correctly, i gave you a warning that the update manager would spam you with recommended kde updates if you were to install a kde app right?

Yeah I know, but I had to try.

---

### Post by Paqman on 2012-01-23
> **silverhaze06 said:**
> I just tried ```
apt-get autoremove
``` and ```
apt-get autoclean
``` but the kde libs are are still coming up in the update manager.

In that case they're still required by some other package you have installed, and therefore need them on your system. Sometimes apps that you don't think of as KDE have KDE/qt dependencies (eg: Skype)

They won't be loaded into memory until actually required though, so there's no harm in having them installed.

---

### Post by philinux on 2012-01-23
> **silverhaze06 said:**
> I downloaded kaffine a few days ago while testing out some media players and have since removed it. but even after that, when the update manager opens, it lists A TON of kde libraries I dont need since I have ubuntu and no more kde applications installed. I looked in my software sources but I dont see anything that would make all these kde libs pop up. Or is there something else that I'm missing?

You could try this method.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by silverhaze06 on 2012-01-23
> **Paqman said:**
> In that case they're still required by some other package you have installed, and therefore need them on your system. Sometimes apps that you don't think of as KDE have KDE/qt dependencies (eg: Skype)

They won't be loaded into memory until actually required though, so there's no harm in having them installed.  Ahh yes. I looked again in the software center and searched kde in my installed applications, then found a couple other small kde apps that I didn't download and removed them. Then tried the commands again. Now everything is gone! Thanks for the help guys!

---

