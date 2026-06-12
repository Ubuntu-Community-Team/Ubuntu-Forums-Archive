---
title: "Fubar'd panels after cleaning off keyboard"
date: 2010-01-20
forum: General Help
---

### Post by Kabaal on 2010-01-20
As the topic states, yes I was stupid enough to hastily clean of my keyboard while at my desktop since I thought, hey what can happen?
Well apparently I can eff up my panels completely.

this is how they look: [http://img687.imageshack.us/img687/7653/screenshotvl.png](http://img687.imageshack.us/img687/7653/screenshotvl.png)

Or well, the top one atleast. I lost all current windows and I lost all text + the icons got a bit smaller. Did I activate some sort of low space mode and most importantly _**how do I get rid of it?**_

---

### Post by jamesisin on 2010-01-20
It's hard to tell from your image what's wrong with the panel because I don't know how you actually want it.

That said, you'll likely want to check out the gconf editing tool:

$ gconf-editor

This tool has a lot of power so use the usual precautions.  You'll want to look at the panels:

/ --> Apps --> Panel

Let us know if you get stuck on the particulars from there.

---

### Post by Kabaal on 2010-01-20
> **jamesisin said:**
> It's hard to tell from your image what's wrong with the panel because I don't know how you actually want it.

That said, you'll likely want to check out the gconf editing tool:

$ gconf-editor

This tool has a lot of power so use the usual precautions.  You'll want to look at the panels:

/ --> Apps --> Panel

Let us know if you get stuck on the particulars from there.

How did I manage to change those setting with keyboard commands though? :o

This is how it was before: [http://img694.imageshack.us/img694/3307/screenshot15v.png](http://img694.imageshack.us/img694/3307/screenshot15v.png)

I moved the icons around abit on the first screenshot since I had no idea what was wrong. I'm looking through gconf-editor now though.

---

### Post by rogue_0111 on 2010-01-20
How about right click on a blank spot on the top panel (in between firefox and Ubuntu logo) and click add panel?

---

### Post by Kabaal on 2010-01-20
> **rogue_0111 said:**
> How about right click on a blank spot on the top panel (in between firefox and Ubuntu logo) and click add panel?

I added a bottom panel earlier, it got the same look of the menu and such.

---

### Post by Kabaal on 2010-01-20
apparently it fixed itself automagically. The windows list started working again and the icons gained the right size. To get the menu back the way it was I removed my main menu thingie and added custom menu >_<

---

### Post by rogue_0111 on 2010-01-20
At least you're getting closer.

good luck

---

### Post by flabdablet on 2010-01-21
I don't tend to customize my panels a huge amount. If something goes badly wrong with them, I log out, then switch to a text console using Ctrl-Alt-F1 and log in, then issue the following commands:
```
sudo /etc/init.d/gdm stop #shut down the whole graphical environment
rm -rf .gconf/apps/panel #delete all the panel-related GConf settings
sudo /etc/init.d/gdm start #start up the GUI again
```
and log in again. All panels are then returned to their default state.

---

