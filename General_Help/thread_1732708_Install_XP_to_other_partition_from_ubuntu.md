---
title: "Install XP to other partition from ubuntu"
date: 2011-04-18
forum: General Help
---

### Post by WolfGangS on 2011-04-18
I would like to install Xp to the other partition on my hard drive.

Currently I plan to use a usb install and boot from usb. (netbook)

But I was thinking maybe its possible to install ubuntu to the other drive from within ubuntu.

Is it?

If so how?

And if not ill just go ahead and make a usb.

---

### Post by beew on 2011-04-18
AFAIK there is no way to run or boot Windows off a usb (you can install Windows 7 with a usb, but from what I undrestand it would only work if you already have Vista installed and the usb only works on the machine that creates it so it is basically for upgrading). Someone claim to be able to do that on the internet but the people I know who have tried that all failed.

---

### Post by sanderd17 on 2011-04-18
maybe you can do something with the dd comand: [http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

but
[LIST]
[*]this will cause problems with your mbr, so you will have to reconfigure the mbr
[*]it is really risky. I would make a complete backup before I try it.
[/LIST]

In other words: yes you can, but it's not easy. Please read about the dd command and ask questions.

---

### Post by WolfGangS on 2011-04-18
> **beew said:**
> AFAIK there is no way to run or boot Windows off a usb (you can install Windows 7 with a usb, but from what I undrestand it would only work if you already have Vista install and the usb only works in the machine that creates it so it is basically for upgrading). Someone claim to be able to do that on the internet but the people I know who have tried that all failed.

I dont intend to run windows off of usb.

I plan to install windows from usb (which I have done before).

But thankyou anyway.

and

> **sanderd17 said:**
> maybe you can do something with the dd comand: [http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

but
[LIST]
[*]this will cause problems with your mbr, so you will have to reconfigure the mbr
[*]it is really risky. I would make a complete backup before I try it.
[/LIST]

In other words: yes you can, but it's not easy. Please read about the dd command and ask questions.

Thankyou as well I'll have a look.

---

### Post by WolfGangS on 2011-04-18
looks like if i had an image of my hardrive when it had XP installed I could use dd to write the image to the hard drive thus restoring windows.

But I don't I just have the iso for xp so I don't think dd can help me much.

---

### Post by beew on 2011-04-18
> **WolfGangS said:**
> I dont intend to run windows off of usb.

I plan to install windows from usb (which I have done before).

But thankyou anyway.
.

How did you do that? Would you be using BartPE?

---

### Post by sanderd17 on 2011-04-18
> **WolfGangS said:**
> looks like if i had an image of my hardrive when it had XP installed I could use dd to write the image to the hard drive thus restoring windows.

But I don't I just have the iso for xp so I don't think dd can help me much.

Maybe I didn't quite get your point.

Why do you want to move your xp installation?

don't you have enough space to install ubuntu? In that case, how is moving xp going to help you?

---

### Post by beew on 2011-04-18
> **sanderd17 said:**
> Maybe I didn't quite get your point.

Why do you want to move your xp installation?

don't you have enough space to install ubuntu? In that case, how is moving xp going to help you?

I think he already installed Ubuntu and wants to add a XP install alongside it.

---

### Post by WolfGangS on 2011-04-18
> **beew said:**
> I think he already installed Ubuntu and wants to add a XP install alongside it.

This

---

