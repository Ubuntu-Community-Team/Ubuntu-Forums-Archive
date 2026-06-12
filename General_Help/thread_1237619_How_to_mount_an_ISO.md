---
title: "How to mount an ISO?"
date: 2009-08-11
forum: General Help
---

### Post by Tipped OuT on 2009-08-11
How do I mount an ISO in Kubuntu? It's just a regular ISO of a DVD movie. 

Thanks.

---

### Post by jaxxstorm on 2009-08-11
Make a directory

```

sudo mkdir /media/ImageMount

```

Then use mount to mount as normal

```

sudo mount /path/to/iso.iso /media/ImageMount/ -t iso9660 -o loop


```

You might need to add the loop module, if you do, just do 
```

sudo modprobe loop

```

and it should work.

---

