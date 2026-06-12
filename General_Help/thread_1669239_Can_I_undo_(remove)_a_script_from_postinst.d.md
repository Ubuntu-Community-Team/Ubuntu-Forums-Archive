---
title: "Can I undo (remove) a script from postinst.d"
date: 2011-01-17
forum: General Help
---

### Post by Mobidoy on 2011-01-17
I have followed a procedure to have the latest Nvida drivers but, it seem to act a little weird so, I would like to turn it around. 

While doing the procedure, I had to do a 

```
sudo install update-nvidia /etc/kernel/postinst.d
```

Is there a way to turn it back ?

---

### Post by Cavsfan on 2011-01-17
Just navigate to that directory and open it as Administrator and delete the script.

---

### Post by Cavsfan on 2011-01-17
That script installs the driver into a new kernel when one is installed.
I too backed away from that approach (the need to have the latest and greatest driver).

---

### Post by Mobidoy on 2011-01-17
Awesome Thanx

---

### Post by Cavsfan on 2011-01-17
> **Mobidoy said:**
> Awesome Thanx

You are welcome. Just make sure you reinstall nvidia-current or whatever driver you plan on using or you could be looking 
at a terminal screen the next time you have a kernel update. Myself I went back to Lucid with a clean install from Maverick.
The default nvidia driver is 195.36.24, which I can live with.

---

