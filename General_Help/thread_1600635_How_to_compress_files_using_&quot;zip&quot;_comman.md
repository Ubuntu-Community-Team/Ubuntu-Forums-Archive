---
title: "How to compress files using &quot;zip&quot; command into two parts."
date: 2010-10-19
forum: General Help
---

### Post by limitfan on 2010-10-19
Thanks for your answers in advance.

---

### Post by aeronutt on 2010-10-19
Once a large zip file is created, I use the 'split' and 'cat' commands to manage the sizes.

---

### Post by limitfan on 2010-10-19
Can you give me an example?
I'm not familiar with these commands.

---

### Post by Gibbs on 2010-10-19
Yeah. Create the archive then split it.

```
split -d -b**500m** file.zip file.zip
```

^ Untested. It *should* split file.zip with **500mb** as the max size for each split.

---

### Post by limitfan on 2010-10-19
> **Gibbs said:**
> Yeah. Create the archive then split it.

```
split -d -b**500m** file.zip file.zip
```

^ Untested. It *should* split file.zip with **500mb** as the max size for each split.

That's right. :)

---

### Post by mastablasta on 2010-10-19
Zip has plenty of options. Used to know this back in the DOS days, but i kind of forgot them since i started using norton/total commander. so here is a link to the manual:
[http://lowfatlinux.com/linux-zip-manual.html](http://lowfatlinux.com/linux-zip-manual.html)
 
BTW a good Linux alternative for total commander is Krusader.

---

### Post by MooPi on 2010-10-19
I generally use tar and gzip for that function. something like this:
```
tar -cf folder.tar folder && gzip folder.tar
```
Unzipping =
```
gunzip folder.tar.gz && tar -xf folder.tar
```

---

