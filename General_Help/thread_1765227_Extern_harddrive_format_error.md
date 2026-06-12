---
title: "Extern harddrive format error"
date: 2011-05-22
forum: General Help
---

### Post by jyu484 on 2011-05-22
I accidentally unplugged my external hard drive during a format, and now it is unrecognisable by my Ubuntu system.

How do I fix this?

---

### Post by ericzmeh on 2011-05-22
Could you unplug the drive, plug back in, and then run 
```

df -m 

```

:-]  Would help to see some output.  Does it not see the drive at all?

---

### Post by jyu484 on 2011-05-22
Thank you for your quick response!

Usually, the hard drive appears on my main desktop screen, but now it does now. I have tried re-plugging it.

After running the command you suggested, the system does not see it.

---

### Post by ericzmeh on 2011-05-22
Have u tried to use gparted to see if it can see the drive at all?  Also, try a different USB port if you can. n Is the drive spinning when you plug it in?

---

### Post by jyu484 on 2011-05-22
Using GParted fixed the problem. I just couldn't remember the name of the program. Thanks for your help.

---

