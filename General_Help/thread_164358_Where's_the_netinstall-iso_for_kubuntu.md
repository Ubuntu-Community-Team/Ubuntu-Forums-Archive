---
title: "Where's the netinstall-iso for kubuntu?"
date: 2006-04-22
forum: General Help
---

### Post by Bear Knuckle on 2006-04-22
And don't tell me there is none! I can't find it anywhere, I only found an iso for ubuntu, but I want to use kubuntu in any case.

Anyone knows where to find a mini.iso for kubuntu?

---

### Post by Qrk on 2006-04-22
There is none. 

The netinstall doesn't include the packages that differentiate Ubuntu from Kubuntu so you can use the same for both. Under the skin, Kubuntu and Ubuntu are the same thing. 

However, I am not sure if there is a choice in the installer about whether to download KDE or Gnome packages. Its a good bet there will be, as Debian offers this choice and Ubuntu's installer does not change much from Debian's.

If it does not give the choice, you can do a server install, (type server when the cd boots) and do a:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by Bear Knuckle on 2006-04-23
Thank you, I will try to install ubuntu using kde, which in my eyes should result in kubuntu or try the install server way.

I am not used to limitations because of the desktop environment. That's not really linux, don't you think so?

---

