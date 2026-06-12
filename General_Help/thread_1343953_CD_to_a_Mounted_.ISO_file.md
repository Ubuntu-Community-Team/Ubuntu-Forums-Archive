---
title: "CD to a Mounted .ISO file"
date: 2009-12-02
forum: General Help
---

### Post by Captain_Falafel on 2009-12-02
I mounted an .iso file and want to change directories to it in the terminal to install it rather than burning it to a CD.. how can I change directory to it?

thanks in advance.

---

### Post by endBc on 2009-12-02
Depends on where you mounted it. Should be in /media.

---

### Post by Captain_Falafel on 2009-12-02
> **endBc said:**
> Depends on where you mounted it. Should be in /media.

I checked in media.. it's not there.
my problem I guess is finding where I mounted it. I right clicked on the file and hit 'open with mounter'.. the file directory that I see in nautilus is really weird, with lots of random characters.

---

### Post by BitJunkie on 2009-12-02
Open a terminal and type: mount
You should be able to find it in the output.

---

### Post by Captain_Falafel on 2009-12-02
> **BitJunkie said:**
> Open a terminal and type: mount
You should be able to find it in the output.

Thanks for the quick responses.. I scratched the graphical mounting option and like you said, mounted it via command line.

```
sudo mount -o loop [file] [location]
```

I know where it is now xD :popcorn:

---

