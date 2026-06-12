---
title: "Desktop disappeared"
date: 2009-08-10
forum: General Help
---

### Post by PreBorn on 2009-08-10
I got Ubuntu on an Acer eee900 notebook, when installed it looked quite like this:

[IMG]http://i41.photobucket.com/albums/e290/DrDead4Ever/ubuntuhelp2.png[/IMG]

There was an option to change the basic menu setup, so i changed to a look quite like this one:
[IMG]http://i41.photobucket.com/albums/e290/DrDead4Ever/Ubuntuhelp1.jpg[/IMG]

[B]
But after i rebooted, I didn't get the upper and lower menu lines at all[/B]. Can anyone please help me to get it back to the first settings i had (1st picture)?

---

### Post by P4man on 2009-08-10
Try pressing alt+F2, then enter:
```

ubuntu-desktop-switcher
```

Then select the netbook remix interface again.

---

### Post by PreBorn on 2009-08-10
> **P4man said:**
> Try pressing alt+F2, then enter:
```

ubuntu-desktop-switcher
```Then select the netbook remix interface again.

```
-bash: ubuntu-desktop-switcher: command not found
```
any other clues?

---

### Post by P4man on 2009-08-10
Sorry, its 

```
desktop-switcher
```

If that fails, you may have to install it, though i think its installed by default with the netbook remix (which I dont have here). If not:

```
sudo apt-get install desktop-switcher

```

---

### Post by PreBorn on 2009-08-10
> **P4man said:**
> Sorry, its 

```
desktop-switcher
```If that fails, you may have to install it, though i think its installed by default with the netbook remix (which I dont have here). If not:

```
sudo apt-get install desktop-switcher

```


Running it in Terminal didn't work either, got alot of errors. But, i tried to make a shortcut with command ```
desktop-switcher
``` and that worked. Thanks alot for helping me :P:P

---

