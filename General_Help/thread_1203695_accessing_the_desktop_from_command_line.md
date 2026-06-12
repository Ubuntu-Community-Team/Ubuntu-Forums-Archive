---
title: "accessing the desktop from command line?"
date: 2009-07-03
forum: General Help
---

### Post by gazz1982 on 2009-07-03
I seem to have a big problem, we had a power cut and now when I boot ubuntu to the login screen it flickers like its stuck in a loop. I can load to command line, once in the command line I can logon. Is there a command to load the desktop? I am trying to get the server working again so I can have remote access to copy stuff off and see if i can reinstall the ubuntu front end. Thanks for any help

---

### Post by linuxmagick on 2009-07-03
You could try the command startx.  But if there's any problem with the display drivers or the xorg configuration, etc, you may not get a graphical desktop and will just end up at the command line again.  If you're planning on re-installing anyway, the easiest thing to do would be to just boot from the Ubuntu Live CD and then copy your important data from there to another hard drive or system across the network.

---

### Post by michy99 on 2009-07-03
What happens if you enter```
startx
```

---

### Post by linuxmagick on 2009-07-03
> **michy99 said:**
> What happens if you enter```
startx
```

It will initialize an X session (i.e. start a graphical desktop session).  You can type the command man startx at a command prompt to see more information about it in the manual pages.

---

### Post by gazz1982 on 2009-07-03
Thanks, I've already tried startx it didnt work, is there anyway of reinstalling ubuntu without wiping any data? the back end (command line) seems fine its just the front end which is screwed!

---

### Post by linuxmagick on 2009-07-03
Come to think of it, I've never even tried to re-install Ubuntu, so I don't really want to comment too much on something I'm not familiar with doing.  However, I can offer the advice of searching the forums to see if anyone else has that answer.  And doing a quick Google search revealed this:  [http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings]("http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/") However, as I said before, I can't vouch for how well it will work.

Even if you find the method you're looking for, I would still strongly recommend backing up anything you don't want to risk losing to another hard drive, external drive, or another computer over the network.  You should be able to do this from the Ubuntu Live CD.  You never know what could happen.

---

