---
title: "Normal or Plymouth bug?"
date: 2010-05-08
forum: General Help
---

### Post by Speed_arg on 2010-05-08
First of all, I have this pc:
[http://valid.canardpc.com/show_oc.php?id=1175020](http://valid.canardpc.com/show_oc.php?id=1175020)

It takes 13 secs from grub to desktop.

When booting up, from those 13 secs it is like this

9secs black screen
1sec ubuntu logo
3 secs wallpaper/gnome loading

Is it normal the logo to be sooo useless? (A 1sec logo is really useless)

---

### Post by TheNerdAL on 2010-05-08
You are a lucky one. Some people have Plymouth problems. But yours is just normal. You should be happy that you just have 1 second on the Ubuntu Logo. :)

---

### Post by Speed_arg on 2010-05-08
Oh thanks :D

---

### Post by TheNerdAL on 2010-05-08
> **Speed_arg said:**
> Oh thanks :D

Anytime, please mark this thread as solved if your question is answered. :)

---

### Post by WorMzy on 2010-05-08
Try typing the following command into a terminal:
```
gksu gedit /etc/initramfs-tools/conf.d/splash
```
Add the following to the file, and save:
```
FRAMEBUFFER=y
```
Then run:
```
sudo dpkg-reconfigure plymouth
```

Might work, might not.

---

### Post by Speed_arg on 2010-05-08
> **WorMzy said:**
> Try typing the following command into a terminal:
```
gksu gedit /etc/initramfs-tools/conf.d/splash
```
Add the following to the file, and save:
```
FRAMEBUFFER=y
```
Then run:
```
sudo dpkg-reconfigure plymouth
```

Might work, might not.
What will that do?

And, how can I mark it as solved?

---

### Post by TheNerdAL on 2010-05-08
> **Speed_arg said:**
> What will that do?

And, how can I mark it as solved?

I don't know what it does but if the only problem you have is a 1 second Ubuntu Splash Screen on boot up, I wouldn't worry. 

You go to Thread Tools -> Mark this thread as solved.

---

### Post by WorMzy on 2010-05-08
I don't know the mechanics behind it, but it works for me.

---

