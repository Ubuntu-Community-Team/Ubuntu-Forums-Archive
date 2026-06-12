---
title: "Ubuntu Top Panel help"
date: 2010-03-19
forum: General Help
---

### Post by SlashHeist on 2010-03-19
So I was just messing around with stuff, and I accidentally deleted the top panel completely. I got it back, but the volume icon for changing the volume and what not is gone, and I can't figure out how to get it back. As well as the icon for showing you if your connected to the internet and what network your connected to is gone as well. 

How do you get them back?

---

### Post by dragonboss on 2010-03-19
Right click the panel > add to panel > notification area

---

### Post by anksush on 2010-03-19
not sure if it will be exactly same for gnome but for KDE when I faced this problem following steps helped (copied from blog entry - [http://makegadgetswork.blogspot.com/2010/03/kubuntu-blog-entry.html]("http://makegadgetswork.blogspot.com/2010/03/kubuntu-blog-entry.html")):

2. Restoring the default panel at bottom of the screen?

Once I finished installing Kubuntu as per the instruction from above link, I started playing around and ended up deleting the panel thus learning about how to get that back. In the process I learnt important lesson on making a backup of setting as soon as you have configured system to your first level of satisfaction as if you do not take this precaution you will have to start all over again.

The steps I took were:as below:

&#9702; Goto Applications tab, click on Settings &#8594; Terminal and open the terminal, Type following commands:

&#9702; sudo cp -R ~/.kde .kde_backup

&#9702; sudo rm -rfv .kde

&#9702; kquitapp plasma-desktop

&#9702; sudo restart

This is it. Now once the system restarts, your panel will be in place. However you will have to put all your configuration again. So to avoid that in future, repeat first two steps and next time you end up in similar situation all you need to do is give this command sudo cp -R ~/.kde_backup .kde and you should be good to go.

---

### Post by SlashHeist on 2010-03-20
> **dragonboss said:**
> Right click the panel > add to panel > notification area

Thanks. Worked

---

