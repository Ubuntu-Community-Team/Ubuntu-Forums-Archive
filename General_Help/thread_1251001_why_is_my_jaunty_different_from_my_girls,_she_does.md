---
title: "why is my jaunty different from my girls, she doesn't have right click resize option?"
date: 2009-08-27
forum: General Help
---

### Post by mejbr2003 on 2009-08-27
there are other differences as well.
we both installed from the same disc. me, about a year ago and her, just a couple of months ago.
she could really use the resize option that I have.
any enlightenment would be appreciated.

---

### Post by NoaHall on 2009-08-27
I don't understand - what do you want to resize? The partion or the window? The partion can be done by going to system -> admin -> partion manager
The window depends on the window theme - if it's the gdk one or emerald, and also if the application supports it.

---

### Post by mejbr2003 on 2009-08-27
I sorry, I wasn't clear at all.
what I was referring to was my ability to resize images ,on my desktop anyway, by right clicking. I get a resize option and she doesn't.
sorry for being confusing.

---

### Post by madnessjack on 2009-08-27
Do you mean icon images? It's an optional called something like change icon size on the right click iirc (sorry, at work atm, can't check)

---

### Post by NoaHall on 2009-08-27
Oh, okay. So when you click on it, there's no "Stretch icon" option? What type of account does she have? I'm guessing you've set up a limited account for her, so there are things she can't do. Or maybe you've installed extra things, when she hasn't.

---

### Post by Viva on 2009-08-27
Are you trying to resize images or stretch icons? If it is the former install [nautilus-image-converter]("apt:nautilus-image-converter")

---

### Post by scragar on 2009-08-27
You need to install nautilus-image-converter

```
sudo apt-get install nautilus-image-converter
```
Then restart your desktop(easiest way, not exactly the cleanest though):
```
killall nautilus
```

---

### Post by mejbr2003 on 2009-08-27
i don't mean icons...mainly its photos...i've shown her how to resize with gimp...but my version has a right click resize option.

---

### Post by Viva on 2009-08-27
> **mejbr2003 said:**
> i don't mean icons...mainly its photos...i've shown her how to resize with gimp...but my version has a right click resize option.

Install [nautilus-image-converter]("apt:nautilus-image-converter") as I said in the other post.

---

