---
title: "fonts are different and smaller"
date: 2012-07-25
forum: General Help
---

### Post by thatjohnpaul on 2012-07-25
Okay, I installed Wine, and I'm not 100% sure if it's the cause, but I realized that I have a bunch of new fonts that I don't want, and my existing fonts look different and are smaller. I am 90% sure that it's because of Wine and the packages it comes with, so I uninstalled it from the Ubuntu Software Center, and then purged it and the files it came with from the terminal. However, my fonts are still different and smaller. It could be that it wasn't Wine (I think it was?) or that I was unsuccessful in purging ALL the files it came with. (Note: I definitely didn't zoom in or out by accident with ctrl + or ctrl -.)

Any ideas as to what happened, and/or how I can fix my fonts?

---

### Post by asmoore82 on 2012-07-26
This has bugged me for years. I love the fonts in Linux just the way they are and I have to tiptoe around installing wine so as not to make my fonts become blocky and nearly unreadable.

I think you need to remove the packages that were automatically installed with wine as dependencies. Luckily, the wonderous package management system remembers which packages were explicitly requested as opposed to packages that were installed as dependencies. This should do the trick...

```
sudo apt-get autoremove
```

After that, I think you can ```
sudo apt-get install wine
``` to avoid them being auto-installed with wine.

---

### Post by thatjohnpaul on 2012-07-26
> **asmoore82 said:**
> This has bugged me for years. I love the fonts in Linux just the way they are and I have to tiptoe around installing wine so as not to make my fonts become blocky and nearly unreadable.

I think you need to remove the packages that were automatically installed with wine as dependencies. Luckily, the wonderous package management system remembers which packages were explicitly requested as opposed to packages that were installed as dependencies. This should do the trick...

```
sudo apt-get autoremove
```After that, I think you can ```
sudo apt-get install wine
``` to avoid them being auto-installed with wine.

Thank you!!

---

