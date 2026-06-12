---
title: "Ubuntu Software Center"
date: 2011-11-28
forum: General Help
---

### Post by Bungraman on 2011-11-28
Hi all,

I am very new to ubuntu, hence why I am here.  I have ubuntu 11.10 installed (Latest version) and I had a "quick start" icon for the Software Center, but now it has vanished.  I have tried searching my computer and I can't find any reference to it at all now.  

The only place that resembles some sort of software center is "DASH HOME", but in my limited exposure to ubuntu/linux it isn't the same.  I like the functionality of the software center to read about software you are about to install, but DASH HOME doesn't do that.

What must I do to re-install this software center functionality/icon/quick start icon thingy.

Regards

Bungra

---

### Post by BC59 on 2011-11-28
Looks very strange.

Anyway you can open a terminal and try to reinstall it:
CTRL+ALT+T and execute

```
sudo apt-get install --reinstall software-center
```

---

### Post by Bungraman on 2011-11-28
Thanks BC,

But please excuse my total lack of knowledge, how does one launch the "terminal"?

Bungra

PS.  I am soooo illiterate to the ways of the ubuntu force.

---

### Post by Bungraman on 2011-11-28
BC, 

I found it, terminal that is.  Ran that code, now the software-center is back.

Thanks so much.

Bungra   :D

---

### Post by BC59 on 2011-11-28
You are welcome.
Please change the thread status to [SOLVED] from thread tools.

---

### Post by philinux on 2011-11-28
> **Bungraman said:**
> BC, 

I found it, terminal that is.  Ran that code, now the software-center is back.

Thanks so much.

Bungra   :D

If you loose an app from the launcher do this.

Open the dash and search for the app. For SC you would just type software and then run the app. It will now be in the launcher as it's actually running. You can now right click the icon and from the list tick Keep in Launcher.

---

