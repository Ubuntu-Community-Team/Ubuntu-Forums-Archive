---
title: "/dev/tty terminals 2 through 6 not spawning"
date: 2006-06-16
forum: General Help
---

### Post by SadaraX on 2006-06-16
I am not sure this is normal behavior, but my /dev/tty terminals number 2 through 6 are not spawing on bootup and I do not know what to do make them appear. These are the terminals that you access by pressing CTRL+ALT+F1 (or F2, F3, F4, F5, F6). Currently, only /dev/tty1 spawns, but nothing else. 

I have edited my inittab file to say 

1:2345:respawn:/sbin/getty 38400 tty1
2:2345:respawn:/sbin/getty 38400 tty2
3:2345:respawn:/sbin/getty 38400 tty3
4:2345:respawn:/sbin/getty 38400 tty4
5:2345:respawn:/sbin/getty 38400 tty5

But nonetheless, nothing appears.... Can anyone tell me a way to make those terminals exist on bootup?

---

### Post by Rui Pais on 2006-06-16
Hi,
i don't know what the "2345" means, but in my case i have:
> 1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

after the first, 2345 is replaced by 23 only.

Don't know if its what make the diference.

---

### Post by gwpritch on 2006-06-16
the 2345 simply refers to the runlevels that it applies to.

---

### Post by Rui Pais on 2006-06-16
[QUOTE=gwpritch]the 2345 simply refers to the runlevels that it applies to.[/QUOTE]
ummm, in that case, they are not the problem...

Thanks for the info, i didn't know that.

---

### Post by gwpritch on 2006-06-16
Why did you need to edit your inittab? Usually 6 are spawned by default.
Not that I've checked recently mind you.

---

### Post by mlind on 2006-06-16
[QUOTE=SadaraX]I am not sure this is normal behavior, but my /dev/tty terminals number 2 through 6 are not spawing on bootup and I do not know what to do make them appear. These are the terminals that you access by pressing CTRL+ALT+F1 (or F2, F3, F4, F5, F6). Currently, only /dev/tty1 spawns, but nothing else. 

I have edited my inittab file to say 

1:2345:respawn:/sbin/getty 38400 tty1
2:2345:respawn:/sbin/getty 38400 tty2
3:2345:respawn:/sbin/getty 38400 tty3
4:2345:respawn:/sbin/getty 38400 tty4
5:2345:respawn:/sbin/getty 38400 tty5

But nonetheless, nothing appears.... Can anyone tell me a way to make those terminals exist on bootup?[/QUOTE]

what's the output of
```

ps -A | grep tty

```

---

### Post by SadaraX on 2006-06-16
I edited the inittab because I thought that adding those numbers might make the terminals appears. It did not however.

ps -A|grep tty prints
 5603 tty7     00:00:07 Xorg
 5620 tty1     00:00:00 getty
 5623 tty2     00:00:00 getty
 5624 tty3     00:00:00 getty
 5625 tty4     00:00:00 getty
 5626 tty5     00:00:00 getty

CTRL+ALT+F2 through F6 show me blank consoles with a blinking cursor, but no ability to log in....

---

### Post by Ankur Dave on 2006-06-24
I have the same problem, except the output of ps -A | grep tty is
```

4575 tty7     00:00:39 Xorg

```
getty isn't running on tty1 either.
But I can get the login prompt to show up by running getty manually with
```

sudo getty 38400 tty1 &

```

---

### Post by mlind on 2006-06-25
Another forums user posted helpful info about tty problems
[http://ubuntuforums.org/showthread.php?t=203532](http://ubuntuforums.org/showthread.php?t=203532)

---

