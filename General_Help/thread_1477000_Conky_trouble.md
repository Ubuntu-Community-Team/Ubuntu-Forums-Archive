---
title: "Conky trouble"
date: 2010-05-08
forum: General Help
---

### Post by Lovefist233 on 2010-05-08
I have this problem with conky, it appears to be stuck in a fixed area, If I add to it or increase the font size then some elements are pushed below the boundary and become invisible.
[Heres a side by side comparison]("http://imgur.com/W25w3")
[And Heres the config file for the image on the left]("http://pastebin.com/EacFNCDK")

Any help would be greatly appreciated.
Also, I am new to Ubuntu, had it for a day now, it's a lot more different to Fedora than I expected but I like it so far.

---

### Post by dino99 on 2010-05-08
This is a dummy package to ease transition to the new packaging scheme.
It may be safely removed after upgrade/installation.

this package is not installed by "default" with ubuntu-desktop

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

### Post by stinkeye on 2010-05-08
> **dino99 said:**
> This is a dummy package to ease transition to the new packaging scheme.
It may be safely removed after upgrade/installation.

this package is not installed by "default" with ubuntu-desktop

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

What does all that mean???

These are the settings in your config you need to look at
```
minimum_size 300 1024
maximum_width 512
```

Try not setting a maximum width or minimum length by using
```
minimum_size 300
maximum_width
```

---

### Post by Lovefist233 on 2010-05-08
Thanks stinkeye, I already tried this... seems very weird that it won't work for me.

*edit: I figured it out, I am a fool, restarting conky after changing the config is what I needed to be doing.

---

