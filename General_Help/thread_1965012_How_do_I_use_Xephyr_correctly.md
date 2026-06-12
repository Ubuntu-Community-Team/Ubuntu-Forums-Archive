---
title: "How do I use Xephyr correctly?"
date: 2012-04-24
forum: General Help
---

### Post by GameX2 on 2012-04-24
Hi,


I am attempting to run an older game using Wine, on Ubuntu 11.10.  Since the program force the use of 256 colors, I have to run it in Xephyr, and it's the first time I'm running anything in Xephyr, so I'm not sure if I do it correctly.

First, I installed Xephyr this way.  That worked:

```
sudo apt-get install xserver-xephyr
```

Next, I do this:

```
Xephyr :1 -ac -screen 640x480x8 &
DISPLAY=:1 xterm
```

I get a black windows.  Did Xephyr include a command-line?  I can't quite remember, I wonder if I messed up a setting?

Then to run the game, I need to open another terminal, and type:

```
DISPLAY=:1
cd ".PlayOnLinux/.../Forestia<etc>"
playonlinux FORESTIA.EXE
```

For some reason, the game has to be run with PlayOnLinux (Not with Wine only), otherwise, it produce at lot of random error messages...
And then my game start (Wow, that was freaky.  Never wondered running the game on PlayOnLinux rather than Wine would stop the errors messages from showing up! :O) in the Xephyr windows...  With music, and even with sound (Wine start it without sound).  The problem, is that the colors are complete crap! :mad:  That's far from 256 colors, and that's the only thing that would make the game unplayable!

Did I missed something?  Should I start the EXE from Xephyr instead of another terminal (How?)?
Is there an alternative solution?


Thanks you!

---

### Post by Toz on 2012-04-25
> The problem, is that the colors are complete crap! That's far from 256 colors, and that's the only thing that would make the game unplayable!There appears to be a limitation in X when trying to run in 8 bit mode when your default mode is 24-bit (See: [http://wiki.winehq.org/256ColorMode?action=show&redirect=ColorIndexMode]("http://wiki.winehq.org/256ColorMode?action=show&redirect=ColorIndexMode")). Having just experimented a bit, you can pass Xephyr the cc parameter to specify different colourmaps. I find the following to be most satisfactory on my system (not perfect, but pretty good):
```
Xephyr :1 -ac -screen 640x480x8 -cc 4 &
```
...(valid cc choices appear to be 1 to 6)

---

