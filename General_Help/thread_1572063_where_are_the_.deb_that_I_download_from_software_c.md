---
title: "where are the .deb that I download from software center?"
date: 2010-09-10
forum: General Help
---

### Post by ibrabeicker on 2010-09-10
so I just bought a notebook and I want to take a lot of programs that i downloaded from ubuntu software center and install them on the notebook without having to downloading them all again

where are these packages? Or does ubuntu doesn't download them at all?

---

### Post by Thelasko on 2010-09-10
[http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)

---

### Post by howefield on 2010-09-10
> **ibrabeicker said:**
> where are these packages?


/var/cache/apt/archives

---

### Post by gandaran on 2010-09-10
they are in /var/cache/apt/archives, just copy them to the same directory in the other computer then install them normally using apt-get or synaptic package manager.
and if you want to remove the download cache run the clean command 
```
sudo apt-get clean
```

---

