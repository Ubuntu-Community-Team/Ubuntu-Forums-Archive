---
title: "Calculator with conversion"
date: 2012-07-11
forum: General Help
---

### Post by icegood on 2012-07-11
There was nice gnome calculator in prev distros.
Now i cannot find any with hex<->dec convert support in 12.04.
What can you suggest?

---

### Post by sisco311 on 2012-07-11
You have to set the *Mode* to *Programming*.

---

### Post by miegiel on 2012-07-11
> **icegood said:**
> There was nice gnome calculator in prev distros.
Now i cannot find any with hex<->dec convert support in 12.04.
What can you suggest?

I use qalculate and <3 it. (I'm on debian right now, but last time I checked it's in the ubuntu repo's too.)
```
sudo apt-get install qalculate
```

---

### Post by icegood on 2012-07-11
> **sisco311 said:**
> You have to set the *Mode* to *Programming*.
In 12.04 i'm not able to do so.

> **miegiel said:**
> I use qalculate and <3 it. 
Yeah, nice one. That what i need. Other question - how to create gnome binding for it to replace default one?

[https://answers.launchpad.net/ubuntu/+source/gcalctool/+question/195942](https://answers.launchpad.net/ubuntu/+source/gcalctool/+question/195942)
  - has no deal anymore. Gnome lost somewhere own key bindings :(

---

### Post by icegood on 2012-07-11
> 
In 12.04 i'm not able to do so.

It sucks! The reason probably is that main menu of window is available only on top of whole desktop, not in calc window itself. Damn interface! Whom idea it was?

---

### Post by Vaphell on 2012-07-11
lol
apple's ;-)


[http://askubuntu.com/questions/10481/how-do-i-disable-the-global-application-menu](http://askubuntu.com/questions/10481/how-do-i-disable-the-global-application-menu)

---

### Post by icegood on 2012-07-12
> **Vaphell said:**
> lol
apple's ;-)

Worse! Windows! :D
OK, so what about key bindings?

---

### Post by Vaphell on 2012-07-12
aren't they in System settings > keyboard?

i have to say that doing it right (changing the default app) in case of calculator category is not trivial in gnome. Did they hardcode the damn thing? Disabling built-in 'calculator' and creating a custom shortcut may be the only way to achieve that. 

I also thought about replacing gnome-calculator (symlink to gcalctool) with a symlink to qalculate - it would work if the system runs 'abstract' gnome-calculator and not the specific binary.
i have a multimedia key for calc but unfortunately it doesn't work inside VM so i can't test it (and i can't be bothered to reboot to another system).
edit: changed the combo to something that is captured in VM and it doesn't work, so somewhere gcalctool is explicitly assigned to 'calculator' category.

---

### Post by sisco311 on 2012-07-12
You can always use dpkg-divert to override a package's version of a file.

```
sudo dpkg-divert --local --rename --add /usr/bin/gcalctool
sudo ln -s **/path/to/qualculate/or/any/other/app** /usr/bin/gcalctool
```

You can remove the diversion with:
```
sudo dpkg-divert --local --rename --remove /usr/bin/gcalctool
```

---

