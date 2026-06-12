---
title: "installing custom fonts"
date: 2009-07-26
forum: General Help
---

### Post by windows-killer on 2009-07-26
I was looking around to install some custom fonts in ubuntu.
I found the fonts I liked and they are in .ttf true type fonts format, how can install that?
Can I install all types of formats ?

---

### Post by wojox on 2009-07-26
Open Terminal:

```
sudo cp myfont.ttf /usr/share/fonts/truetype
```

---

### Post by meeples on 2009-07-26
if you go to your home folder, and press "CTRL + H" there should be a folder named ".fonts" if not make one.

and whenever you have a new .ttf just put it in there and thats it installed.


there working on making installing fonts alot easier, hopefully it makes it to karmic :D

---

### Post by wojox on 2009-07-26
Oh mac fonts:

```
wget http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz
```

```
tar zxvf macfonts.tar.gz
```

```
sudo mv macfonts /usr/share/fonts/
```

```
sudo fc-cache -f -v
```

---

### Post by ibexslam on 2009-07-26
The .fonts folder in my home directory did not work for me.  I installed a font to the usr folder and that worked OK, yet another font I installed there is not showing up in my applications.  Something is not right.

I.

---

### Post by windows-killer on 2009-07-26
and how do I start using the fonts?

---

### Post by ibexslam on 2009-07-26
You know, I just tried that
"sudo fc-cache -f -v"
...and it fixed my font problem right up.  For the record.

I.

---

