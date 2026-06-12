---
title: "How do I uninstall customs installed fonts?"
date: 2010-05-14
forum: General Help
---

### Post by Arachan on 2010-05-14
Hello, 

I use a font creator program and I installed some of the fonts I made by opening them in font viewer and selecting "install font". To cut a long-ish story short, they now seem to overwrite some of my normal system fonts. 

How do I remove them?

Thanks,
Arachan.

---

### Post by wojox on 2010-05-14
They should be in here 

```
/etc/fonts/fonts.conf
```

And here

```
/usr/share/fonts
```

```
/usr/local/share/fonts
```

```
/home/<username>/.fonts
```

You'll probably have to go in as root and delete them. The easiest way would be 

```
gksudo nautilus
```

Then refresh the font cache

```
sudo fc-cache -f -v
```

---

### Post by Arachan on 2010-05-14
Hello,

I found them in 
```
/home/<username>/.fonts
```

Thanks for the quick useful reply,
Arachan.

---

### Post by wojox on 2010-05-14
Cool your welcome. :)

---

