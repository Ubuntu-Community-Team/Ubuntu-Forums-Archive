---
title: "Ubuntu (Maverick, 64-bit) won't load at all"
date: 2011-04-05
forum: General Help
---

### Post by Ghostlove on 2011-04-05
So I upgraded to Natty, didn't like it and decided to go back to Maverick. Got out my trusty Live CD and reinstalled, no problem. Unfortunately now it just takes me to the screen with the list of possible OSes to start, and when I press enter it says:

```
error: symbol not found: 'grub_os_area_addr'.
```

I don't appear to be able to do anything from there. I've had so much trouble with this blinking computer lately that I'm even considering going back to Windows. Can anyone help me, please?

---

### Post by An Sanct on 2011-04-05
Hello!

My first try would be to reinstall grub from the Live CD

```

sudo mount /dev/sd**XY** /mnt  sudo 
grub-install --root-directory=/mnt /dev/sd[B]X
[/B]
```Taken from [this thread]("http://ubuntuforums.org/showthread.php?p=10440484").

PS.
where X and Y most probably are "a" and "1" so:
```

sudo mount /dev/sda1 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda
```

---

