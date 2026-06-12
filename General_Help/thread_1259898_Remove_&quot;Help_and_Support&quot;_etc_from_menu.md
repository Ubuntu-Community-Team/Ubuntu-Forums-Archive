---
title: "Remove &quot;Help and Support&quot; etc from menu?"
date: 2009-09-06
forum: General Help
---

### Post by ninjapirate89 on 2009-09-06
I am wondering if there is an easy way (such as with configuration editor) to remove "Help And Support", "About GNOME", and "About Ubuntu" from under the System menu. I never need these and I like to keep my menus clear of anything unnecessary.

---

### Post by ninjapirate89 on 2009-09-08
bump

---

### Post by ninjapirate89 on 2009-09-09
bump

---

### Post by dearingj on 2009-09-09
I haven't tried this, but I found this solution [here]("http://ubuntuforums.org/showthread.php?t=350790"):

delete gnome-about.desktop and ubuntu-about.desktop from /usr/share/applications:
```
sudo rm /usr/share/applications/gnome-about.desktop /usr/share/applications/ubuntu-about.desktop
```

That won't get rid of the "Help and Support" link, but it should get rid of "About Ubuntu" and "About GNOME"

---

### Post by ninjapirate89 on 2009-09-09
Thanks. I browsed to that folder and deleted those and found the one for Help And Support also. Now all three are gone from my menu. The only problem now is there are two horizontal separators in my menu instead of one but thats no big deal.

Edit -> See?

[ATTACH]128004[/ATTACH]

---

