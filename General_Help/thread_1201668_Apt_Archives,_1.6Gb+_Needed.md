---
title: "Apt Archives, 1.6Gb+ Needed?"
date: 2009-07-01
forum: General Help
---

### Post by MTGap on 2009-07-01
I was recently looking through /var/cache/apt/archives due to an error with installing a package and I noticed that inside was 1.6Gb of debian packages. 

Is there a need for these or are they regularly deleted after a certain time? I would prefer if I didn't have that much space taken up because is there even a need for them once you install the application or upgrade?

---

### Post by michy99 on 2009-07-01
There is really no need to keep them. If you need to reinstall you can just download again. To get rid of them, enter this in terminal.```
sudo apt-get clean
```

---

### Post by drs305 on 2009-07-01
You can type "man apt-get" in a terminal to see all the options for apt-get, including the good command  michy99 just gave you.

In addition to 'clean', there are also 'autoremove' and  'autoclean' for package collections. You can also use 'purge' and 'remove' for getting rid of specific apps but these have equivalents in Synaptic when you elect to uninstall a single app.

---

### Post by MTGap on 2009-07-01
Cool thanks, I knew about the autoremove, but didn't know that clean did that. Cool now I have almost 2GB back in space...

---

