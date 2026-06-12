---
title: "nautilus-actions does not work"
date: 2010-05-05
forum: General Help
---

### Post by pwn on 2010-05-05
I created an action in nautilus-actions, but I don't see it when I right click on a file. This works fine on other distros.

---

### Post by inameiname on 2010-05-05
What version of Ubuntu are you using? If you are using Karmic, and updated it, sometimes newer versions mess up like that. I know if you have GetDeb's repos on your sources.list, the latest nautilus-actions for Karmic repo wont work.

---

### Post by mc4man on 2010-05-05
If you are using the newer version of n-a (2.29.4 - 2.30) then atm you'll need to use the full path in command box for any and all commands
simple ex.'s 
instead of gksu /usr/bin/gksu
instead of gedit, /usr/bin/gedit

If your action remains in red in nact then it's written or pathed  wrong

---

### Post by inameiname on 2010-05-06
Hmmm, I didn't know that. That makes sense as to why mine didn't work in Karmic. Though, it doesn't matter now as I use Lucid and have the latest from the repos, which works just fine.

---

### Post by mc4man on 2010-05-06
> Though, it doesn't matter now as I use Lucid and have the latest from the repos, which works just fine. 

It seems the need for absolute paths was fixed in the last update for n-a (lucid release), had been needed  prior to.

-> nautilus-actions (2.30.2-0ubuntu1)
 Slightly relax the validity rules of a profile, so that already
      existing actions may be still considered as valid, even when
      commands do not use an absolute path. (LP: #488612)
      (Nautilus Actions' actions don't show up in context menus)

---

### Post by inameiname on 2010-05-06
Yeah that was my thinking as to why it was working in Lucid.

---

