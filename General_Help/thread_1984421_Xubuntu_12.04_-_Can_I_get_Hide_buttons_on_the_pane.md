---
title: "Xubuntu 12.04 - Can I get Hide buttons on the panel?"
date: 2012-05-21
forum: General Help
---

### Post by NTL2009 on 2012-05-21
In my current Ubuntu Lucid, I have a panel on the bottom with Hide buttons, so I can hide it when I want (I don't really like 'Auto-Hide').

I've installed Xubuntu 12.04 on an external drive to experiment with. I like it, and am getting it set like my old Ubuntu Lucid. But the Preferences only give a choice of Auto-Hide On/Off - no button option. (Panel is xfce4-panel-4.8.6).

Any trick way to get these Hide buttons in this panel?

-NTL2009

---

### Post by Jose Catre-Vandis on 2012-05-22
These two commands will unhide and hide the panel
```
xfconf-query -c xfce4-panel -p /panels/panel-0/autohide -s false
xfconf-query -c xfce4-panel -p /panels/panel-0/autohide -s true
```
You could add these to a launcher....

---

### Post by NTL2009 on 2012-05-22
Thanks. I just tried those in terminal, and I got:


> Property "/panels/panel-0/autohide" does not exist on channel "xfce4-panel".  If a new
property should be created, use the --create option.

I'm not really sure how to use the create option for this.

-NTL2009

---

### Post by rai4shu2 on 2012-05-22
It might be panel-1 or panel-2 instead of panel-0. Anyway, here's how to toggle in case you figure that out:

```
#!/bin/sh
HIDDEN=$(xfconf-query -c xfce4-panel -p /panels/panel-0/autohide)

if test $HIDDEN = false; then
  xfconf-query -c xfce4-panel -p /panels/panel-0/autohide -s true
else
  xfconf-query -c xfce4-panel -p /panels/panel-0/autohide -s false
fi
```

---

### Post by Jose Catre-Vandis on 2012-05-22
And it doesn't help that xfconf starts counting the panels from 0, when in panel preferences they start from 1 ;)

```
xfconf-query -c xfce4-panel -lv
```
should list all the panels and their contents for identification

---

### Post by NTL2009 on 2012-05-22
Thanks to both above - I had a bit of a brain phart earlier. I was trying this on 12.04, but then I read your replies when I was on my main 10.04 system, and entered the terminal commands there -  so apparently the commands changed.


Though I did guess that maybe the '0' is offset from their '1' in the GUI, so I did try that.

The commands seem to work (have not tested the script yet) - so thanks.

I will mark this 'solved' for now. I do think it would be good to have the same arrow options in Xubuntu panels as Lucid had, but the devs may have other issues with that.

-NTL2009

---

### Post by NTL2009 on 2012-05-22
OK, got a chance to try the script, and put a launcher for it in the top panel (0), to change the bottom panel (1). I just saved it as panel.sh and set the permissions to executable and pointed the launcher properties at it. 

It mostly does what I want, though it becomes 'unhidden' if I mouse over it, as it is back in 'auto-hide' mode then rather than really just 'hidden'. I my poke around those other properties to see if they might do this.

-NTL2009

---

