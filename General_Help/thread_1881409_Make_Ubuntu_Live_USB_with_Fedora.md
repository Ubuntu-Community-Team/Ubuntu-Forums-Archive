---
title: "Make Ubuntu Live USB with Fedora?"
date: 2011-11-15
forum: General Help
---

### Post by veidar45 on 2011-11-15
HI, I don't know if this is the right category for this or if it an offtopic, but how can I make a live USB with Fedora 15? I downloaded the ubuntu-10.04.3-desktop-amd64.iso file and tried to install it to USB flash (4GB) with Fedora liveusb-creator, but it seems that it is not suitable for OS different from Fedora and Sugar on Stick....


PLEASE help....I realized that Ubuntu is the better Linux, but I had problems with Ubuntu 11.10, so I switched for a while on Fedora....and now I want to roll back!

Thanks! :)

---

### Post by snowpine on 2011-11-15
Give Unetbootin a try, it's always worked well for me:

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by veidar45 on 2011-11-15
Well ok, I downloadet UNetbootin and chmod-ed it and when I start it, nothing happens and the program doesn't show up...


Edit: I must say, my Fedora OS installation is very new, so it may not have many required things for the program....

---

### Post by snowpine on 2011-11-15
> **veidar45 said:**
> Well ok, I downloadet UNetbootin and chmod-ed it and when I start it, nothing happens and the program doesn't show up...


Edit: I must say, my Fedora OS installation is very new, so it may not have many required things for the program....

Sorry, I did not realize you were so new to Fedora. Typically in Fedora we install packages using "yum" for example:

```
su -
yum install unetbootin
unetbootin
```

I hope that helps, good luck! :)

---

### Post by veidar45 on 2011-11-15
Oh yeah, I know about "sudo" and "yum", but I'm not used to using them (ex-Windows, hehe :D)...Thanks anyway! Much helped - everything is working now....I hope after 1 hour I'll be with Ubuntu 10.04 ;) :)

---

