---
title: "Looking for a missing file name... (empathy status icon)"
date: 2010-10-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-10-01
I am looking for a missing status icon's file name
the one that empathy will flicker to when you get a message and the window is closed
the icon shows up if you are not using [FONT=Courier New]indicator-messages[/FONT] anyone know what it is and what it looks like also?

---

### Post by TyLLy_4 on 2011-03-15
there is an official bug report .... however i have changed my icon theme and the suggested fix doesn't work for me. 

here's a link. 

(post #12 & #18)

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/533109]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/533109")

---

### Post by pqwoerituytrueiwoq on 2011-03-16
thanks
solution:
```
cd /usr/share/icons/Humanity/actions/16
sudo ln -s im-message-new.svg notification-message-im.svg
cd ../22
sudo ln -s im-message-new.svg notification-message-im.svg
cd ../24
sudo ln -s im-message-new.svg notification-message-im.svg
sudo gtk-update-icon-cache -f /usr/share/icons/Humanity/
```

---

### Post by TyLLy_4 on 2011-03-16
This does not work for me as i changed the theme in favor of one downloaded from gnome-looks.org (Candy theme) 

I cant find a candy-theme directory in there :( 

any help?

---

### Post by pqwoerituytrueiwoq on 2011-03-16
my guess would be here
/usr/share/icons/Candy/16x16
/usr/share/icons/Candy/22x22
/usr/share/icons/Candy/24x24

---

### Post by TyLLy_4 on 2011-03-16
> **pqwoerituytrueiwoq said:**
> my guess would be here
/usr/share/icons/Candy/16x16
/usr/share/icons/Candy/22x22
/usr/share/icons/Candy/24x24


Like I tried to say earlier ..... none of my custom icon packs are there. Only the default ones :( 

My desktop looks quite different that the Screen shots in the bug report yet my IM icon blinks too when some one talks to me. 

(see SS attached) 

[http://i.imgur.com/D6R0h.jpg](http://i.imgur.com/D6R0h.jpg)

---

### Post by pqwoerituytrueiwoq on 2011-03-16
try this
```
locate Candy
```

---

### Post by TyLLy_4 on 2011-03-16
> **pqwoerituytrueiwoq said:**
> try this
```
locate Candy
```

How didnt i think of that!!!! 

Still .. no luck :( 


```

/home/l30/Dropbox/Dropbox/Cobra Power/Mynxx/rt_mynxx_j15/rt_mynxx_j15/html/com_rokcandy
/home/l30/Dropbox/Dropbox/Cobra Power/Mynxx/rt_mynxx_j15/rt_mynxx_j15/html/com_rokcandy/default.ini
/home/l30/Music/Compilations/Alternative/i am ghost-killer likes candy.mp3
/home/l30/Pictures/Sexy/candy_cane_omi_gibson--article_image.jpg
/home/l30/bin/Ubuntu Install/candy_icon_theme_1.0alpha2.tar.gz
/usr/lib/openoffice/basis3.2/share/config/symbol/l_candy.bmp
/usr/share/app-install/desktop/earcandy.desktop

```

Also attached SS so you can see that that is indeed the icon name .... 

[http://i.imgur.com/G2XOK.png](http://i.imgur.com/G2XOK.png)

---

### Post by pqwoerituytrueiwoq on 2011-03-16
it would help if i know how it was installed
maybe 
/home/$USER/.local/share/icons/Candy
edit:
maybe
/home/l30/bin/Ubuntu Install/Candy
edit2:
none of those result have "Candy" in the 
run *locate Candy* not *locate candy*

---

### Post by TyLLy_4 on 2011-03-17
Founded it! 

```

/home/l30/.icons/Candy/scalable/actions/stock_paste.svg
/home/l30/.icons/Candy/scalable/actions/stock_print-setup.svg
/home/l30/.icons/Candy/scalable/actions/stock_redo.svg
/home/l30/.icons/Candy/scalable/actions/stock_refresh.svg
/home/l30/.icons/Candy/scalable/actions/stock_right.svg
/home/l30/.icons/Candy/scalable/actions/stock_select-all.svg
/home/l30/.icons/Candy/scalable/actions/stock_stop.svg
/home/l30/.icons/Candy/scalable/actions/stock_top.svg
...
(keeps going with anohter 800 ressults or so)


```

Will try the fix in that directory in a few minutes .... 

Thx for your help

---

