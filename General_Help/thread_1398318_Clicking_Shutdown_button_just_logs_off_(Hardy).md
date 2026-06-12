---
title: "Clicking Shutdown button just logs off (Hardy)"
date: 2010-02-04
forum: General Help
---

### Post by styxcoverbnd on 2010-02-04
I'm running a laptop and a desktop that both have Hardy on them. A few days ago I updated to 8.04.4 on both and since then when I click on the red Shutdown button and then click on 'Shutdown' it just logs me out. Anyone have this happen to them after the update? Any ideas on how to fix it?

*Please Note* I am not physically pushing the power button on the PC's. so unfortunately going to Gnome Top Panel Menu > System > Preferences > Power Management > General Tab Actions will not work to correct this issue

---

### Post by Monotoko on 2010-02-04
Try typing:
```
sudo shutdown -h now
```

into the terminal, tell me if that shuts down successfully

---

### Post by styxcoverbnd on 2010-02-04
> **Monotoko said:**
> Try typing:
```
sudo shutdown -h now
```

into the terminal, tell me if that shuts down successfully

Thanks, I will give this a try. What does the -h switch mean? I'm assuming Halt?

Edit: Oops sorry, I wasn't thinking, I'll do a man for the shutdown command

---

### Post by Monotoko on 2010-02-04
It means halt

```
Options:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

```


Edit: Sorry posted this before your edits ^.^

---

### Post by styxcoverbnd on 2010-02-05
I ran 
```
sudo shutdown -h now
```

on both my laptop and desktop and they both shutdown fine. After that I tried shutting down by clicking on the red shutdown button and they both shutdown ok. I'm not sure what was fixed (if anything), but since it seems to be working correctly I'm marking this as solved. Thanks for the assistance Monotoko

---

