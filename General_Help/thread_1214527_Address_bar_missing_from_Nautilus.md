---
title: "Address bar missing from Nautilus"
date: 2009-07-16
forum: General Help
---

### Post by Digital Ninja on 2009-07-16
Just installed Ubuntu 9. 

At first, address bar was there and worked as usual, but after installing 
all my applications (gftp, vlc, apache, mysql...) through Synaptic manager 
i noticed that somehow the address bar from Nautilus dissapeared. 

If i press Ctrl+L i can get it to show and work with it, but as soon as I 
have it out of focus by clicking anything alse, the bar dissapears again. 

I don't see any options on showing/hiding the address bar in Nautilus 
options.

What to do?

---

### Post by nelamvr6 on 2009-07-16
To the left of the location bar you'll see an icon that looks like a pencil hovering over a pad of paper.  If you hover your mouse over that the tool tip should pop up saying "Toggle between button and text based location bar".

Click this icon.

---

### Post by Digital Ninja on 2009-07-16
i don't understand how, but yes, that actually made the address bar appear on every new Nautilus and it stays on .... thanks.

---

### Post by MattPhillips on 2010-11-20
Hi,

I'm a little late to this thread, but I'm having the same problem--Ctrl-L gets me the location bar (thanks nelamvr6) but I don't see the icon you mentioned.  I'm using 10.04.  Anybody know what to do?  Thanks--

Matt

---

### Post by matt_symes on 2010-11-20
Hi

Open a terminal and type (case sensitive)

gconf-editor

In the tree navigate to

apps->nautilus->preferences

Check "always use location entry" in the right hand side pane.

If for whatever reason gconf-editor is not installed, at the terminal type

sudo apt-get install gconf-editor

Then enter you password. You will not see it as you enter it. This is normal

Kind regards

---

### Post by dcstar on 2010-11-20
> **MattPhillips said:**
> Hi,

I'm a little late to this thread, but I'm having the same problem--Ctrl-L gets me the location bar (thanks nelamvr6) but I don't see the icon you mentioned.  I'm using 10.04.  Anybody know what to do?  Thanks--


The icon not longer exists in 10.04 and later versions.

---

### Post by lazylew on 2010-12-11
> **matt_symes said:**
> Hi

Open a terminal and type (case sensitive)

gconf-editor

In the tree navigate to

apps->nautilus->preferences

Check "always use location entry" in the right hand side pane...
Thank you sir, this is great!

---

