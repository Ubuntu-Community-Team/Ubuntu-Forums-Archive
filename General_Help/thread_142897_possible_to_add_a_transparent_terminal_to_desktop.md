---
title: "possible to add a transparent terminal to desktop?"
date: 2006-03-11
forum: General Help
---

### Post by harty83 on 2006-03-11
Howdy,

Is it possible to add a transparent terminal (with no borders, menus, etc) to the desktop?  I'm picturing a transparent terminal that starts up everytime I log in and plants itself to the corner of my desktop without showing it in the task bar.

Alan

---

### Post by bluevoodoo1 on 2006-03-11
Might be able to do it with Eterm, though it will show up in the task bar (not sure it that can be changed or not). Look at my screenshot link.

---

### Post by Klejs on 2006-03-11
Yes that'd be great, please someone who knows how to do it tell us...

---

### Post by Klejs on 2006-03-11
After reading the BlackBox HOWTO posted by [COLOR="Blue"]bluevoodoo1[/COLOR] I found the way to create the transparent Eterm. Just install Eterm by apt-getting it: 

```
sudo apt-get install eterm
```

When done you can start the transparent terminal by typing:

```
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x35+13+495 -f lightgrey
```

Hope it will help you...

---

### Post by dresnu on 2006-03-11
ooops... already answered...  sorry

---

### Post by gingermark on 2006-03-11
Check out YaKuake - you can make it transparent, and it's really nice.

---

### Post by harty83 on 2006-03-12
I think I can deal with yakuake.  It may even be better than having a terminal embedded on my desktop because I can call it up over any applicaiton with a push of a button.  Thanks!

---

### Post by bluevoodoo1 on 2006-03-12
There's also tilda, which is similar to yakuake... (I've never tried either)

[http://tilda.sourceforge.net/tildashots.php](http://tilda.sourceforge.net/tildashots.php)

---

