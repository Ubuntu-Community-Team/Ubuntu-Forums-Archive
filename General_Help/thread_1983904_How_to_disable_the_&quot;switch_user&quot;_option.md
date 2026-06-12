---
title: "How to disable the &quot;switch user&quot; option?"
date: 2012-05-20
forum: General Help
---

### Post by lisanels47 on 2012-05-20
I have clients that select "switch user" when someone else is logged on the system.  Our client computers are not fast, so although it works, it tasks the resources bad.  Can we disable the option to "switch users?"

---

### Post by mc4man on 2012-05-21
Well this will achieve that though not sure if exactly what you desire

Graphically set in dconf-editor, shown in screen, or from cli
```
gsettings set com.canonical.indicator.session user-show-menu false
```

If so then keep in mind that a user can set back to true if they know where or the command.

Supposedly dconf has a key lock system though I'm not sure if it works in Ubuntu
Basic - 
[https://live.gnome.org/dconf/SystemAdministrators](https://live.gnome.org/dconf/SystemAdministrators)

---

### Post by lisanels47 on 2012-05-21
Thank you!  This is what I am looking for, but the directories shown have nothing in them... prob a thing with Unity and 12.04.

This does get me going down the right road.  I'll see what else I can find on dconf and unity.

---

### Post by mc4man on 2012-05-21
> **lisanels47 said:**
> Thank you!  This is what I am looking for, but the directories shown have nothing in them... prob a thing with Unity and 12.04.

This does get me going down the right road.  I'll see what else I can find on dconf and unity.

Not sure what you mean by that - "directories shown have nothing in them", are you looking in [COLOR="Red"]d[/COLOR]conf-editor
(or just running the gsettings com.

---

### Post by lisanels47 on 2012-05-21
The directory /etc/dconf and children directories are empty.  Nothing really in them:

root@lisa-Inspiron-1545:/etc/dconf# ls -R
.:
db  profile

./db:
gdm

./profile:
gdm
root@lisa-Inspiron-1545:/etc/dconf# 

The document you referenced talked a lot about the stuff there... Or not there I guess....

---

### Post by mc4man on 2012-05-21
> **lisanels47 said:**
> The directory /etc/dconf and children directories are empty.  Nothing really in them:

root@lisa-Inspiron-1545:/etc/dconf# ls -R
.:
db  profile

./db:
gdm

./profile:
gdm
root@lisa-Inspiron-1545:/etc/dconf# 

The document you referenced talked a lot about the stuff there... Or not there I guess....
I tried that every which way, doesn't seem to work (as far as locking a key

Here's a question on Ask Ubuntu where it was 'sorta' implied in the answer that it 'could' work though I'm not sure that Rinzwind actually did get it to _work at all for any key_
(it didn't work in regards to the question
[http://askubuntu.com/questions/132175/how-to-store-a-dconf-key-as-read-only](http://askubuntu.com/questions/132175/how-to-store-a-dconf-key-as-read-only)

---

