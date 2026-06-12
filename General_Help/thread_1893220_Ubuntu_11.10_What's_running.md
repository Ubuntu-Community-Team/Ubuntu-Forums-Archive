---
title: "Ubuntu 11.10 What's running?"
date: 2011-12-09
forum: General Help
---

### Post by dreamquartz on 2011-12-09
I am trying to figure out how to determine what is running.
By the looks of it it is a very well hidden option.

Can anyone help?

---

### Post by pretty_whistle on 2011-12-09
> **dreamquartz said:**
> I am trying to figure out how to determine what is running.
By the looks of it it is a very well hidden option.

Can anyone help?
I have Ubuntu 11.10 and I found it, it's called "System Monitor".  It's listed under "SYSTEM" in Unity.

Maybe that will be the same on yours if you have Lubuntu.

---

### Post by dFlyer on 2011-12-09
from a terminal just run:

ps -aux

or 

top

---

### Post by bluexrider on 2011-12-09
> **dFlyer said:**
> from a terminal just run:

ps -aux

or 

top

"ps -aux" = will give you static information

"top" = will give you live information

---

### Post by pretty_whistle on 2011-12-09
> **bluexrider said:**
> "ps -aux" = will give you static information

"top" = will give you live information
Yeah, top.

I forgot about that one.

---

### Post by oldtimer7777 on 2011-12-09
> **dreamquartz said:**
> I am trying to figure out how to determine what is running.
By the looks of it it is a very well hidden option.

Can anyone help?

sudo apt-get install htop

Really handy task manager like app

---

### Post by dreamquartz on 2011-12-19
That worked.  Thanks

---

