---
title: "Nothing written in fstab"
date: 2011-01-31
forum: General Help
---

### Post by ephexeve on 2011-01-31
I've been having a lot of problems solving my HDD mounting problems and renaming. It finally worked, but I had to delete everything from fstab. As crazy as it sounds, it worked, when I turn my computer on, they automatically mount. They are all working fine. I will attach screen shots too.

As you can see my fstab is blank, I was just wondering, is this a problem? Or is it totally normal?

Thanks in advance.

---

### Post by ephexeve on 2011-01-31
Sorry, I forgot to mention, I tried to open fstab using the following commands. 

```

sudo -s
cd /etc
gedit fstab
```or

```

cp /etc/fstab /etc/fstab.bak
sudo gedit fstab
```I am using Ubuntu 10.10.

---

### Post by ephexeve on 2011-01-31
Anyone?

---

### Post by vanadium on 2011-01-31
Of course, your /etc/fstab file is not blank. But you'd better not touch it, unless you know exactly what you want to achieve.

---

### Post by ephexeve on 2011-01-31
It is, I deleted everything from there, because my mounting wasnt working. So I saved it blank, and it worked. Everything got back in place.

---

