---
title: "Save a list of all installed apps?"
date: 2009-07-22
forum: General Help
---

### Post by aaron424 on 2009-07-22
I am migrating from 32 bit ubuntu to the 64 bit on my new machine. Is there a way to save all installed applications and export them in a text file, perhaps so that as soon as I set up the new computer, I can run sudo apt-get install "everything". Thanks.

---

### Post by drs305 on 2009-07-22
There are two fairly easy methods, one CLI and one GUI:
CLI:
Run on old computer:
```

sudo dpkg --get-selections | grep -v "deinstall&#8221; >$HOME/Desktop/installed-packages 
```
Copy installed-packages to $HOME/Desktop on new computer 
```

sudo apt-get update
sudo dpkg --clear-selections
sudo dpkg --set-selections <$HOME/Desktop/installed-packages 	
sudo apt-get dselect-upgrade
```


GUI:
Synaptic: File > Save Markings As. Be sure to tick the "Save full state, not only changes" in the lower left or it will create a nearly empty file.

To restore, Read Markings.

---

### Post by sisco311 on 2009-07-22
never mind. i'm too slow. :)

---

### Post by aaron424 on 2009-07-22
Thank you very much.

---

### Post by aaron424 on 2009-07-22
sisco: What do you mean?

---

### Post by michy99 on 2009-07-22
Be aware, though, that not all 32-bit packages have a 64-bit equivalent.

---

### Post by aaron424 on 2009-07-22
But Ubuntu will just run them in 32 bit, correct?

---

