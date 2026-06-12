---
title: "/root Partition Question"
date: 2009-10-17
forum: General Help
---

### Post by linux4life88 on 2009-10-17
I just had a quick question, if I have my partition setup like so:

/root
/home
swap

this means when I need to update Ubuntu from one version to the next all I have to do is reinstall the /root partition and my files located in /home will be left alone?

---

### Post by falconindy on 2009-10-17
Sure. Just tell the installer to mount your old /home partition as /home but **DO NOT FORMAT IT**. The swap will be picked up as a swap formatted partition and used automatically.

---

### Post by linux4life88 on 2009-10-17
> **falconindy said:**
> Sure. Just tell the installer to mount your old /home partition as /home but **DO NOT FORMAT IT**. The swap will be picked up as a swap formatted partition and used automatically.

I was pretty sure this was how it worked, I just wanted to be safe and not sorry. Thank you for the help.

---

### Post by mechro on 2009-10-17
> **falconindy said:**
> Sure. Just tell the installer to mount your old /home partition as /home but **DO NOT FORMAT IT**. The swap will be picked up as a swap formatted partition and used automatically.

Probably a dumb question but when the installer is making, for example, a new /home/Documents folder what does it do about the one already there?

---

### Post by falconindy on 2009-10-17
> **mechro said:**
> Probably a dumb question but when the installer is making, for example, a new /home/Documents folder what does it do about the one already there?
It doesn't do anything with it. It's not creating a new /home structure. The current one is left intact.

---

### Post by mechro on 2009-10-17
> **falconindy said:**
> It doesn't do anything with it. It's not creating a new /home structure. The current one is left intact.

So, for example, if Gnome has a major upgrade there is nothing in /home that would conflict with any new configuration it wants to do?:confused:

---

### Post by falconindy on 2009-10-17
That's up to you to figure out. This is exactly the reason I've been sure to keep my Jaunty /home partition as read only when I access it from Karmic.

---

### Post by mechro on 2009-10-17
> **falconindy said:**
> That's up to you to figure out. This is exactly the reason I've been sure to keep my Jaunty /home partition as read only when I access it from Karmic.

Understood. You confirmed what the OP asked. I prefer to keep my installations separate and just transfer across the personal data. :)

---

### Post by CatKiller on 2009-10-18
> **linux4life88 said:**
> I just had a quick question, if I have my partition setup like so:

/root
/home
swap


**No.**

You want **/** as a partition. In fact, you can't install without it.

/root is *root*'s Home folder. There should be virtually nothing in it. There's absolutely no purpose whatsoever in having that on a separate partition.

> **mechro said:**
> So, for example, if Gnome has a major upgrade there is nothing in /home that would conflict with any new configuration it wants to do?:confused:

Why would there be? Generally, Free software is backwards compatible in its handling of configurations. Software is **supposed** to be upgraded. It's what the package manager is **for**.

Future-compatible is a different matter, of course. Using a /home partition from 2009 with an install from 2001, say, is likely not to work. Straight upgrades, though, are widely deployed and widely tested.

---

