---
title: "Volume Control Gone!"
date: 2010-06-12
forum: General Help
---

### Post by Oolongtea on 2010-06-12
I just freshly upgraded to 10.04 and I am not able to listen to anything due to me not having access to the volume control. It was not in the menu bar when I installed 10.04. May I get some help resolving this?

---

### Post by bigsmitty64 on 2010-06-12
Right click the top panel and click "add to panel" then find the "indicator applet" click add. :)

---

### Post by Oolongtea on 2010-06-12
I'm not seeing it. I went to the top panel and clicked add items and it wasn't in the list. Is that what you wished me to do?

---

### Post by bigsmitty64 on 2010-06-12
"indicator applet" isn't in the menu?

---

### Post by Oolongtea on 2010-06-12
nope.

---

### Post by bigsmitty64 on 2010-06-12
wait...you said you UPGRADED right?  What version did you upgrade from?

---

### Post by Jakiejake on 2010-06-12
> **Oolongtea said:**
> nope.

Did you search "indicator applet" in the search box in the add to panel window

---

### Post by Jakiejake on 2010-06-12
System -> Preferences -> Sound

---

### Post by Elfy on 2010-06-12
Try looking for Mixer when you right click and add to panel.

Indicator applet is in gnome - not seeing it in the xubuntu options here.

---

### Post by Oolongtea on 2010-06-12
What I meant by fresh was that I had 8.10 but I burnt a copy of 10.04 and installed that. I searched and no results.

---

### Post by Oolongtea on 2010-06-12
I just got mixer but I still don't have any sound.

---

### Post by bigsmitty64 on 2010-06-12
I haven't personally tried[ THIS]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/") but it looks like it may help you.

---

### Post by bigsmitty64 on 2010-06-12
If you got the volume control back then forget what I just posted. Maybe look in the sound properties now and see if anything is muted?

---

### Post by Jakiejake on 2010-06-12
> **bigsmitty64 said:**
> I haven't personally tried[ THIS]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/") but it looks like it may help you.

GNOME Is Ubuntu

---

### Post by bigsmitty64 on 2010-06-12
> **Jakiejake said:**
> GNOME Is Ubuntu
?

---

### Post by Elfy on 2010-06-12
> **bigsmitty64 said:**
> ?

I think it's a reference to your link to the remove gnome panels blog in a xubuntu thread.

---

### Post by j_arquimbau on 2010-06-12
There was an applet which let you install gnome applets in xubuntu, but I don't remember the name right now. I'm going to look round there. By the way, did you try to look for mixer like someone said?


[EDIT] I found it! Have a look here:
[http://bapoumba.wordpress.com/2008/01/04/add-gnome-applets-to-the-xfce-panel/](http://bapoumba.wordpress.com/2008/01/04/add-gnome-applets-to-the-xfce-panel/)

---

### Post by bigsmitty64 on 2010-06-12
> **forestpiskie said:**
> I think it's a reference to your link to the remove gnome panels blog in a xubuntu thread.

whoopsie?  :)  didn't see that.

---

### Post by Oolongtea on 2010-06-13
shouldn't there just be a simple volume control and not this complex one?

---

### Post by Oolongtea on 2010-06-16
I figured it out lol. All I had to do was enter this code. Thanks for all your guys help :)

```
sudo apt-get gnome-volume-control-applet
```

---

