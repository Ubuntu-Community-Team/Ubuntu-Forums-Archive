---
title: "Themes do not appear - &quot;contents unreadable&quot;"
date: 2012-04-29
forum: General Help
---

### Post by hugom on 2012-04-29
Hi there,

I'm using gnome shell on 11.10 and am trying to install themes. This one here ... [http://craazyt.deviantart.com/art/Black-n-White-GTK-v1-291269596](http://craazyt.deviantart.com/art/Black-n-White-GTK-v1-291269596)

I extract the folder and put it in usr/share/themes and then go to change the theme but the option for that one is not there. Inside the themes folder there is a white 'x' on the folder I put on there and it under properties it says contents unreadable.

It does this with a lot of themes but some work as well. Any help would be great thanks.

---

### Post by hugom on 2012-04-30
anyone?

---

### Post by hugom on 2012-05-02
bump

---

### Post by hugom on 2012-05-05
Anyone?

---

### Post by Zvlwab on 2012-05-05
```
sudo chmod -R +rw /usr/share/themes/foldername
```

although you should actually place custom themes in ~/.themes/

---

### Post by hugom on 2012-05-05
Thanks i'll give that a try.

Even when I put them in .themes I still get the same problem though.

---

### Post by hugom on 2012-05-05
Just tried it. The command works but when I go to change the theme it still doesn't appear?

---

