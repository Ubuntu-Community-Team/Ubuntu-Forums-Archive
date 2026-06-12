---
title: "Best way to switch from gnome to kde?"
date: 2006-06-04
forum: General Help
---

### Post by circadianhelix on 2006-06-04
Just wondering whether this can be as simple as using syanptic?

apparently from my latest experience with "xchat" gnome is too basic.

i'm not sure.

the only thing so far which will make me keep windows is mirc that is unless wine handles it properly.

anyway. kde might be worth a go.

---

### Post by meng on 2006-06-04
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

If you have the space, it's worthwhile keeping both KDE and GNOME just in case you want to go back later.

---

### Post by circadianhelix on 2006-06-04
cheers man will do

thanks for the quick reply :)

---

### Post by Nordoelum on 2006-06-04
First do a:
```
$sudo aptitude remove ubuntu-desktop
```
and then:
```
$sudo aptitude install kubuntu-desktop
```

Then you will have KDE instead of GNOME.

---

### Post by %hMa@?b&lt;C on 2006-06-04
ubuntu-desktop is a meta package, not a real package, removing ubuntu-desktop wont do anytihng

---

### Post by circadianhelix on 2006-06-04
I just went ahead with the info given...

sudo aptitude update 

sudo aptitude install kubuntu-desktop

will this in effect be the same as a straight kde install?

---

### Post by Nordoelum on 2006-06-04
[QUOTE=jeffc313]ubuntu-desktop is a meta package, not a real package, removing ubuntu-desktop wont do anytihng[/QUOTE]
What does that mean?

---

### Post by meng on 2006-06-04
The k/x/ubuntu-desktop package is a big box that all the default applications come in. (Those defaults applications are listed as dependencies, and the box itself doesn't really do anything except hold it all together.)

Now, if you want to remove one of those components, well, you have to remove the k/x/ubuntu-desktop package too, because officially it's dependent on the component you're discarding. But really all that happens is that you're being forced to throw out the "box".

---

### Post by Nordoelum on 2006-06-04
I have run an remove ubuntu-desktop. Can that have inflicted my GDM error?

---

### Post by meng on 2006-06-04
If you only removed ubuntu-desktop, it should not have changed anything "real" on your system.

---

### Post by Nordoelum on 2006-06-04
I used aptitude.

---

### Post by jan on 2006-06-04
Why would you want to do that? :D

---

### Post by Nordoelum on 2006-06-04
To remove everything that had something to do with Ubuntu, since I am using Xubuntu on my server.

---

