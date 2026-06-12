---
title: "Conky translucence?"
date: 2010-01-19
forum: General Help
---

### Post by ownaginatious on 2010-01-19
I'm trying to setup a few additional Conky windows, and was wondering; is there a way to set the background of a conky window to semi-transparent? All I've been able to do is either make it a solid colour or transparent (I know it's only pseudo transparent, but that's okay).

Thanks :)

---

### Post by VCoolio on 2010-01-19
Try this lua script [here]("http://ubuntuforums.org/showpost.php?p=8006534&postcount=9312") or better: [here]("http://conky.linux-hardcore.com/?page_id=3002"). Also the newer version has real transparancy!

Edit: with newer version I mean 1.8.0, available [here]("https://launchpad.net/~norsetto/+archive/ppa")
You'll then need:
own_window_argb_visual yes
own_window_transparent yes

---

### Post by ownaginatious on 2010-01-20
Awesome; thanks! :)

I'm having a slight problem though; the function 'execibar', which is built into conky, doesn't seem to be working anymore. Rather than showing a progress bar that updates at a regular interval, it just shows a number instead.

Any ideas with how to fix that?

---

### Post by VCoolio on 2010-01-20
Sorry, I don't know. Are you sure your syntax is correct? Try asking [here]("http://ubuntuforums.org/showthread.php?t=281865"), and include your conkyrc.

---

