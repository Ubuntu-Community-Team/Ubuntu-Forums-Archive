---
title: "graphics"
date: 2009-06-29
forum: General Help
---

### Post by ubunewtu on 2009-06-29
all right gang this is what happened i went to the add remove programs and had seen that there was an ati catylyst and graphic installer when i installed the programs and rebooted my screen came up black with some lines at the top and nothing else i went into safe mode and choose the try to fix graphics option automatically and it didnt work im able to get to a command line is there a way to uninstall the programs from there?

---

### Post by ~sHyLoCk~ on 2009-06-29
Yes there is a way to uninstall from command line if you remember the name of the package just use ```
sudo apt-get remove packagename
``` and reboot

---

### Post by colau on 2009-06-29
> **ubunewtu said:**
> all right gang this is what happened i went to the add remove programs and had seen that there was an ati catylyst and graphic installer when i installed the programs and rebooted my screen came up black with some lines at the top and nothing else i went into safe mode and choose the try to fix graphics option automatically and it didnt work im able to get to a command line is there a way to uninstall the programs from there?
```

sudo aptitude remove <packagename>

```
To remove the package and it's configuration files too
```

sudo aptitude purge <packagename>

```

---

### Post by ubunewtu on 2009-06-30
hey thanks alot gang that worked my next question is if there is an anti virus program provided by linux im trying to keep everything pure

---

### Post by colau on 2009-06-30
> **ubunewtu said:**
> hey thanks alot gang that worked my next question is if there is an anti virus program provided by linux im trying to keep everything pure
There is no virus in linux.

---

### Post by ubunewtu on 2009-07-05
no virus in linux? so i really dont need anti virus?

---

### Post by mhgsys on 2009-07-05
If you are just booting linux, and don't share files with a windows box
you won't need any anti-virus.

[http://ubuntuforums.org/showthread.php?t=912012](http://ubuntuforums.org/showthread.php?t=912012)

---

### Post by ubunewtu on 2009-07-11
hello ubuntu world heres the deal a few days ago i started playing urban terror the resson i mention this is that after downloading some maps i started getting three beeps on shut down and restarts of the pc it didnt do this until after the few maps i downloaded i guess my thing is 1) could i have downloaded something within the maps that my cumputer dosnt like 2)is it fixable without reinstalling the game.

---

### Post by earthpigg on 2009-07-12
> **ubunewtu said:**
> hello ubuntu world heres the deal a few days ago i started playing urban terror the resson i mention this is that after downloading some maps i started getting three beeps on shut down and restarts of the pc it didnt do this until after the few maps i downloaded i guess my thing is 1) could i have downloaded something within the maps that my cumputer dosnt like 2)is it fixable without reinstalling the game.

i suggest creating a new thread specific to your problem, and be more specific when you create this new thread:

how did you install this game? in WINE? from the repos?

---

### Post by TeamJ on 2009-07-12
Linux is virus free

---

