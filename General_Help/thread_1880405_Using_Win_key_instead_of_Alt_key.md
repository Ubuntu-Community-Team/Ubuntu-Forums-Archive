---
title: "Using Win key instead of Alt key"
date: 2011-11-13
forum: General Help
---

### Post by yellowzelo on 2011-11-13
Hi, 

left Alt key on my laptop just stopped working (in any OS). Probably, I will not be able to fix it. I was thinking I could change functionality of Win key to Alt key, so I would use Win key instead of Alt. Do you have any ideas?

Thank you.

---

### Post by Spyderkid on 2011-11-13
well, it depends...

I'm not sure you can replace it's acctual function to serve as Alt, But you can change some of the shortcuts in Compiz and gnome config to use Superkey(win key) instead of alt

---

### Post by mutley89 on 2011-11-14
You can do this with xmodmap.  run the following:
```
xmodmap -pm
```You should get a line something like this:
```
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
```If so run:
```
xmodmap -e 'clear mod4'
xmodmap -e 'keysym Super_L = Alt_L'
```If this works as you want it to you can make it permanent by adding the last two lines to a file called '~/.Xmodmap'
Also you can use the 'xev' program to print out keycodes when you press a key, useful for figuring out what xmodmap calls each key.

---

### Post by yellowzelo on 2011-11-14
Thank you, guys.

---

### Post by shrek1 on 2011-11-14
did it worked yellozello ?

---

