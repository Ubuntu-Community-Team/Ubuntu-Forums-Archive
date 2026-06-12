---
title: "Lucid Server, ubuntu-desktop does not autostart"
date: 2010-05-19
forum: General Help
---

### Post by ILMV on 2010-05-19
Hi all,

I have just setup two servers running 10.04 server and have installed the ubuntu-desktop as follows:

```
sudo apt-get install ubuntu-desktop
```

The problem is even though it says it has installed it will not auto-start...

I've tried this:

```
sudo mv /etc/init/gdm.conf /etc/init/gdm.disabled
```

```
sudo mv /etc/init/gdm.disabled /etc/init/gdm.conf
```

To enable/disable it (found it [here]("http://ubuntuforums.org/showthread.php?t=1479980")) but still not joy.

Any ideas?

Thanks,
Ben

---

### Post by wojox on 2010-05-19
If you need a gui then just download the Desktop CD and install LAMP.

---

### Post by ILMV on 2010-05-19
Thanks for your response

That's not how we setup our servers here, I've done a load of searching on the topic and 90% of the replies were people bitching and moaning about whether you should start from the desktop or server versions... I don't want to get into another flame war.

So if anyone can help with my problem of installing the desktop onto 10.04 server I would be very greatful.

Cheers! :popcorn:

---

### Post by ILMV on 2010-05-20
I've found the solution, thanks to kras1001 on [this thread]("http://ubuntuforums.org/showthread.php?t=1367907") for providing the answer!

---

### Post by inso_741 on 2010-05-20
now that you have found the solution you can mark this thread solved...:p

---

