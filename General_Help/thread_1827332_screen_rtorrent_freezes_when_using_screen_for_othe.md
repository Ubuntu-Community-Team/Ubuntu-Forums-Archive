---
title: "screen rtorrent freezes when using screen for other programs"
date: 2011-08-17
forum: General Help
---

### Post by mulllhausen on 2011-08-17
i use screen rtorrent and it always works fine by itself. however if i also open another instance of screen then the rtorrent session freezes! maybe i am not opening multiple screens correctly? here is an example:

```

$ screen rtorrent # works fine - i can move around with the arrow keys and the page refreshes when things like the download rate change
$ ctrl a+d # exit rtorrent and return to the shell
$ screen cp /tmp/x1 /tmp/x2 # assume x1 is very large so this takes a long time
$ ctrl a+d # exit the copying and return to the shell
$ screen -ls
There are screens on:
        26608.pts-0.hostname (18/08/11 10:15:39)     (Detached)
        8329.pts-0.hostname  (17/08/11 13:44:00)     (Detached)
2 Sockets in /var/run/screen/S-username.
$ screen -r 8329.pts-0.hostname # resume rtorrent and now it is frozen - i cannot move around with arrow keys and the page never updates

```does anyone know a solution? i have a feeling this problem is repeatable - you could try using ```
screen top
``` instead of my copying example above to simulate it.

is there some control command i can press in screen to fix it or should i run rtorrent with more screen options in the first place?

i am using rtorrent version 0.8.2 and screen version 4.00.03jw4 (FAU) 2-May-06

cheers
peter

---

### Post by mulllhausen on 2011-08-18
also, now that my copying has finished and there is only a single screen session left i have full control of the screen again!

i tried ```
screen top
``` and the rtorrent screen session actually works fine with this running aswell. so the problem is definitely due to the screened copying command...

well i tried copying in a different location using screen and it did not freeze rtorrent so i guess it must just be that i was copying from an external hard drive over usb 1.1 and that rtorrent was saving to this same external hard drive (/tmp/x1 and /tmp/x2 before were just examples).

so maybe it is more of a kernel issue or a usb bus issue? anyway i know how to avoid it now :)

---

