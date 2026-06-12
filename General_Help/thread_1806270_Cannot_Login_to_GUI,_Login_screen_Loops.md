---
title: "Cannot Login to GUI, Login screen Loops"
date: 2011-07-17
forum: General Help
---

### Post by Linux BASHer on 2011-07-17
I have an Asus 1001P running Xubuntu 10.04. Seemingly out of nowhere the netbook is refusing to let me log in. It presents me with the login screen and I click on my name and type my password. Instead of logging in normally, I see a brief terminal screen and it takes me back to the login screen once again, rinse, wash, repeat.

I can login via one of the terminal screens without issue and it will actually let me log in to an xterm session, but not in xfce. I remember having this issue before, but I don't even remember how I solved it. I think I had it with 11.04 and just downgraded after several problems. If so, I'm guessing this might be the product of an update. I've searched the forums, but can't seem to find info specific enough to solve this issue. To add insult to injury it looks like my battery is going and I have to have it plugged in most of the time just to work on it.

---

### Post by Habitual on 2011-07-17
Login via a terminal.
```
mv .config .config.org
mv .gconf .gconf.org
```

Login via Ctrl+Alt+F7 or reboot.

Any change?

---

### Post by Linux BASHer on 2011-07-17
> **Habitual said:**
> Login via a terminal.
```
mv .config .config.org
mv .gconf .gconf.org
```

Login via Ctrl+Alt+F7 or reboot.

Any change?

Hmm. Unfortunately, no. :-k

---

### Post by Linux BASHer on 2011-07-18
Any other suggestions?

---

### Post by dino99 on 2011-07-18
mv .local .local.org

sudo dpkg-reconfigure xdm

or install something else, like gdm, kdm, ... instead of xdm

---

### Post by Linux BASHer on 2011-07-18
> **dino99 said:**
> mv .local .local.org

sudo dpkg-reconfigure xdm

or install something else, like gdm, kdm, ... instead of xdm

I get a very strange login- huge dialog box with tiny cursor. In any case, it loops just the same.

I foresee this netbook getting wiped.

---

