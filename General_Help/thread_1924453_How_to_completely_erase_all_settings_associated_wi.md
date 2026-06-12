---
title: "How to completely erase all settings associated with a program?"
date: 2012-02-12
forum: General Help
---

### Post by coldjeanz on 2012-02-12
Basically I installed Midori web browser today, but I did something weird to it and now there some things wrong with it. The icon for the program has taken on some really strange symbol which is NOT the icon for the actual program, I can't delete any of the bookmarks I put into the program. It's really a mess and I need to start over however removing the program did nothing. When I reinstalled it all the settings were still there.

How do I go back to the point where it was completely fresh as if I had never installed it in the first place?

---

### Post by cbowman57 on 2012-02-12
try ```
sudo apt-get purge midori
```

---

### Post by bluexrider on 2012-02-12
remove related configuration files to midori

```
sudo rm -rf ~/.midori
```
and

```
sudo rm -rf ~/.config/midori

```

This removes user settings from the application

---

### Post by coldjeanz on 2012-02-12
No luck. The stupid thing just refuses to go away.

Although I did find out what is causing the different icon. There's something called "Discover-Elementary" installed which I think came with the installation of Midori and it thinks I'm using that for some reason. I can't figure out how to uninstall the "Discover-Elementary" thing though, what do I type in to purge that?

---

### Post by Rafterman414 on 2012-02-12
I found some success using Synaptic Package Manager and then checking under the section that says Not Installed (Residual Config) This is for programs that you had previously installed but there is still some stuff left behind. Once you find what you want to remove mark it for complete removal

---

### Post by winh8r on 2012-02-12
sudo apt-get remove midori --purge

---

### Post by coldjeanz on 2012-02-12
> **Rafterman414 said:**
> I found some success using Synaptic Package Manager and then checking under the section that says Not Installed (Residual Config) This is for programs that you had previously installed but there is still some stuff left behind. Once you find what you want to remove mark it for complete removal

Sorry I'm a bit confused, where is the "Not Installed" section located?

BTW Midori seems to be completely removed but the "Discover-Elementary" thing is still installed. I feel that if I can remove this then everything should be good but the problem is that I can't even click on it which means it's not actually there.

---

### Post by VH-BIL on 2012-02-12
Check if there is any other hidden config files or directories in your home directory and remove them. I am not familiar with that browser so make sure that the config file you are about to delete is for the browser you want to remove.

```
find ~/ -name '*midori*'
```

---

### Post by coldjeanz on 2012-02-12
> **VH-BIL said:**
> Check if there is any other hidden config files or directories in your home directory and remove them. I am not familiar with that browser so make sure that the config file you are about to delete is for the browser you want to remove.

```
find ~/ -name '*midori*'
```

Actually this is what finally worked. I did a search for "elementary" and there was some file sitting in the .local/share/applications folder that I had to delete. Thank you!

---

### Post by VH-BIL on 2012-02-13
> **coldjeanz said:**
> Actually this is what finally worked. I did a search for "elementary" and there was some file sitting in the .local/share/applications folder that I had to delete. Thank you!

welcome :)

---

