---
title: "Disabling screensaver during mplayer for Xubuntu"
date: 2012-05-01
forum: General Help
---

### Post by GammaPoint on 2012-05-01
Hi, I'd like to disable the screensaver from coming on when I use mplayer, since obviously I don't want movies to be interrupted by it. Of course I can always manually adjust the screensaver timings before and after watching a movie, but that's super lame. 

There are basically two options available in mplayer for doing something like I want:

1). The -stop-xscreensaver: I passed this to mplayer on Xubuntu and it didn't fix it, so presumably the commands embedded in that aren't compatible with the environment on Xubuntu.
2). The other option is the heartbeat-cmd, which is supposed to be used like so (says the man page):
```


              EXAMPLE   for  xscreensaver:  mplayer  -heartbeat-cmd  "xscreen&#8208;
              saver-command -deactivate" file

              EXAMPLE   for   GNOME   screensaver:   mplayer    -heartbeat-cmd
              "gnome-screensaver-command -p" file

```

so it looks like to try this option I have to know either the xscreen-saver-command or the gnome-screensaver-command? How do I find out which one I am using, and what the proper command is? Is Xubuntu even using one of these two, or is it something different?

Thanks for the help!

---

### Post by Toz on 2012-05-01
Have a look here: [http://forum.xfce.org/viewtopic.php?id=6920]("http://forum.xfce.org/viewtopic.php?id=6920").

---

### Post by GammaPoint on 2012-05-01
> **Toz said:**
> Have a look here: [http://forum.xfce.org/viewtopic.php?id=6920]("http://forum.xfce.org/viewtopic.php?id=6920").

Thank you Toz. I used the following mplayer command and it worked just fine. I didn't realized that "xscreensaver-command" was literally the command I was supposed to use and not some placeholder.

```

mplayer -xineramascreen 1 -heartbeat-cmd "xscreensaver-command -deactivate" -fs 
```

---

