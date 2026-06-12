---
title: "Adobe Flash Player install error"
date: 2009-06-29
forum: General Help
---

### Post by jdennis43 on 2009-06-29
Hi,
I just installed Ubuntu 9.04 in my computer and i'm trying to install the program
install_flash_player_10_linux.deb and install_flash_player_10_linux.tar.gz and on the
first one i got a error message saying Error: Dependency is not satisfiable: libcurl3 and the other one i couldnt even load. I have a Dell OptiPlex GX720 also running Windows XP  
so I can use my magicJack and my iPhone. Can you please help? Thanks.

---

### Post by lovinglinux on 2009-06-30
The second one is not an executable. It is probably source code compressed as tar, which means you would need to [compile](http://en.wikipedia.org/wiki/Compiling) [wikipedia.org].

The easiest way to install flash is to click [here](apt:flashplugin-nonfree) [apt-get], but this won't remove previous installed plugins.

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

If you want to install flash from Adobe and remove conflicting plugins at the same time I recommend to run the command below on a terminal:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by colau on 2009-06-30
> **lovinglinux said:**
> The second one is not an executable. It is probably source code compressed as tar, which means you would need to [compile](http://en.wikipedia.org/wiki/Compiling) [wikipedia.org].

The easiest way to install flash is to click [here](apt:flashplugin-nonfree) [apt-get], but this won't remove previous installed plugins.



If you want to install flash from Adobe and remove conflicting plugins at the same time I recommend to run the command below on a terminal:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```
+1 lovinglinux

After installing swfdec-mozilla and mozilla-plugin-gnash when I start firefox it freezes.
They are always a problem.
That's why these should be removed first if they are installed.
After removing them,there is no problem with firefox now.
```

apt-get install flashplugin-nonfree

```

---

