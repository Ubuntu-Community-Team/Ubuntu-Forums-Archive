---
title: "Cant install anything"
date: 2010-02-24
forum: General Help
---

### Post by heroinbob545 on 2010-02-24
ive just installed Karmic Koala and after updating and getting drivers i cant install anything whether it be through synaptics or sudo or the .deb it just hangs any help would be great

---

### Post by lotharmat on 2010-02-24
If you type 
```
sudo apt-get update
```
into a terminal do you get any output?

---

### Post by thecyborgus on 2010-02-24
I dont know if it's related or not but im getting massive timeouts on the repositories right now preventing me from installing anything that way.

---

### Post by heroinbob545 on 2010-02-24
this is what ended up hapening 
[img]http://i47.tinypic.com/b7yj39.jpg[/img]

---

### Post by patchwork on 2010-02-24
That's good output.  Now enter

```
sudo apt-get install <package_name>
```

and post any errors that occur

---

### Post by heroinbob545 on 2010-02-24
i tried installing DeVeDe and mplayer and it went through this time but normally it would hang right at 0% and cause me to need a force quit

---

### Post by heroinbob545 on 2010-02-24
thanks for the help it seems to be working fine now probably was just me doign something sutpid

---

### Post by corruptnova on 2010-02-24
> **heroinbob545 said:**
> thanks for the help it seems to be working fine now probably was just me doign something sutpid

If it happens again, switch your repo urls. I was having the same problem earlier with timeouts and connectivity. Switching to [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive) has fixed it, so I guess one or more of the servers is having a problem.

---

