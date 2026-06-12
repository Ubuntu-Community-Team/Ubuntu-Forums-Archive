---
title: "Editing iso???"
date: 2009-07-24
forum: General Help
---

### Post by Orwhaleca on 2009-07-24
Is it possible to edit the iso file prior to burning it, to automatically install ubuntu-restricted extras? also, is it possible to edit it so that it has wmaker by default instead of GNOME?

---

### Post by hetx on 2009-07-24
Googled it for you

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

ps that was just the first hit, didn't really read it. You can find more guides with remastersys

---

### Post by Orwhaleca on 2009-07-24
Thank you. I'll try this.

---

### Post by Slim Odds on 2009-07-24
You might want to think of a better title next time.

This isn't really "editing an ISO", it's recreating or creating a new ISO from an existing one.

---

### Post by Orwhaleca on 2009-07-24
I don't even feel like deigning to respond to your reply in kind. Webster's shows the definition of edit as "to modify or add to (data or text)".

---

### Post by iponeverything on 2009-07-24
I thought the title was fine. While maybe the choice of words could have been a bit better, it was clear from the title what you meant and I think that is the intent of language.  

I am not one that cares that much about descriptive subjects and have noticed that sometimes the less descriptive or oddly titled post, generally garner more views -- i click on them just out of curiosity..

That aside remastersys is what should be looking at to recreate the iso after have edited the correct configuration files.

I might be as easy as adding custom .deb to the iso that will be installed last that will change the default via perhaps 

/etc/X11/default-display-manager

---

