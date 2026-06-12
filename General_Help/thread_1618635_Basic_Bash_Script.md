---
title: "Basic Bash Script?"
date: 2010-11-10
forum: General Help
---

### Post by emoguitarist06 on 2010-11-10
I want to be able to run one command or scrip that I can make executable to be able to open a 
X server (Xephyr) and than open my chroot and open a program into that X

Under **Using Xephyr** at this tutorial:
[http://wiki.mandriva.com/en/Development/Howto/Chroot#Launch_X_Applications_inside_the_chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot#Launch_X_Applications_inside_the_chroot)

There are [COLOR="Red"]three commands[/COLOR] I have to run
*Outside of Chroot*
```
$ Xephyr -ac -fullscreen :1
```
(I added -fullscreen)

This causes a black screen to open up

**Normally** I would then open a [COLOR="Red"]separate terminal[/COLOR] and do the next two commands
```
$  export DISPLAY=localhost:1
$ ./home/phillipguy/Downloads/pcsx2
```

and Viola pcsx2 opens up in Xephyr... but I just want a do it all script

Anyone?

---

### Post by cipherboy_loc on 2010-11-10
The code:

```

#!/bin/bash

Xephyr -ac -fullscreen :1 &
sleep 5
export DISPLAY=localhost:1 &
/home/phillipguy/Downloads/pcsx2 &

exit 0

```

---

### Post by emoguitarist06 on 2010-11-10
Great Try but it's only opening the X

I'm sorry I left out one command

To get into chroot
```
sudo chroot /var/chroot
```
now once I'm in chroot is when I run the next two commands export.....

---

