---
title: "Can someone please explain these instructions for me?"
date: 2011-08-01
forum: General Help
---

### Post by trinhfelix on 2011-08-01
As a first time linux user, I don't seem to understand the terminal commands as well as you guys. I'm using a Logitech G19 keyboard and need gnome15 to properly use it.
[http://www.gnome15.org/index.php?option=com_content&view=article&id=22&Itemid=33](http://www.gnome15.org/index.php?option=com_content&view=article&id=22&Itemid=33)

The instructions on this website confuse me, what is a Public Key? Do I just need to skip to the second step? I've tried this code:
```
sudo sh -c "echo deb http://www.gnome15.org:9999/$(lsb_release -cs) ./ >> /etc/apt/sources.list"
```
But nothing happens :(

Thanks for you help!

---

### Post by nothingspecial on 2011-08-01
> **trinhfelix said:**
> 
But nothing happens :(

Thanks for you help!

That's because it worked. In general, it only says anything if something goes wrong (error messages).

If the command succeeds, it just returns you to the prompt.

---

### Post by trinhfelix on 2011-08-01
> **nothingspecial said:**
> That's because it worked. In general, it only says anything if something goes wrong (error messages).

If the command succeeds, it just returns you to the prompt.

Thank you, that explains a lot.

I managed to get gnome15 installed but my solution was more complex.

---

