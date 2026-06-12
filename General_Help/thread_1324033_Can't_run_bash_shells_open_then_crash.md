---
title: "Can't run bash shells: open then crash"
date: 2009-11-12
forum: General Help
---

### Post by Arlanthir on 2009-11-12
I'll try to explain all the steps, but they make no sense to me.

I wanted to try KDE, so I aptitude'd it. 
I fixed the usplash and cursor problems with the commands (and selections):

```

sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
sudo update-alternatives --config x-cursor-theme
```


Then I realized some of my applications were autostarting on both Gnome and KDE, which I didn't want.

Removing them from one DE removed them from the other too, so I wrote an IF statement to check whether $DESKTOP_SESSION was set to 'gnome' and if so, run gnome-do.

To test it, I ran it a few times under gnome and it worked. I wrote it on .bashrc and logged out. Then I logged in KDE and when I opened konsole, it crashed. I logged back in gnome and gnome-terminal also crashed on open. I deleted my IF from .bashrc and rebooted. No change.

Now I can only run sudo shells or konsole -e sh. I already reinstalled bash and gnome-terminal with no success. Any ideas?

**EDIT:**Nevermind that, accidentally added an 'exit 0' from the previous test script to .bashrc, not good. *head on wall*

---

