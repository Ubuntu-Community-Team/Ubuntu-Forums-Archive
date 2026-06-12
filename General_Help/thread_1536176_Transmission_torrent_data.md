---
title: "Transmission torrent data"
date: 2010-07-21
forum: General Help
---

### Post by emoguitarist06 on 2010-07-21
I currently have Ubuntu 9.10 32bit and I want to upgrade to Ubuntu 9.10 64 bit tonight

I do have my /home on a separate partition so when I upgrade I won't lose my data just will have to reinstall programs of course

Anyways I currently have Torrents in progress or that are paused in Transmission and I noticed there is no .transmission fold in my home folder so I am scared of losing my inprogress torrents!
Of course I'll still have my partial or .part files but will transmission still remember that I needs to continue downloading these torrents if I format the / (root) folder? 
(remember I will not be formatting the /home folder)

---

### Post by NFblaze on 2010-07-21
Backup your

```
/home/<username>/.config/transmission/
```

folder. When you have your new installation, after installing transmission. You can copy that folder into your new installation.

---

### Post by emoguitarist06 on 2010-07-21
> **NFblaze said:**
> Backup your

```
/home/<username>/.config/transmission/
```

folder. When you have your new installation, after installing transmission. You can copy that folder into your new installation.

OH awesome! Thanks for the quick replay and simple solution!
I was looking for .transmission and didn't even think to look in .config!

---

