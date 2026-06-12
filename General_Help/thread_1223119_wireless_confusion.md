---
title: "wireless confusion"
date: 2009-07-25
forum: General Help
---

### Post by fattyxyz on 2009-07-25
i recently made a new build with jaunty 9.04 but i ran into the problem that i expected when i installed ubuntu.
I have my work pc downstairs running a linksys router on windows xp   and i heard about an edimax network adapter that works with ubuntu out of the box but when i heard linksys doesnt work with ubuntu i got very confused and decided to get a better opinion
so in summary:what i could do to connect ubuntu to linksys on xp?
i apoligize for any confusion.

---

### Post by Joeb454 on 2009-07-25
Moved to General Help :)

---

### Post by pastalavista on 2009-07-25
I'm confused. What do you mean the work PC is "running" the linksys router? Is it a wireless router? My linksys router has always worked perfectly with Ubuntu. If you would plug-in your Ubuntu PC via ethernet cable to the router, it should work fine.. long enough to download and install the drivers for your wireless card.. I'm guessing that's the problem you've got.

---

### Post by fattyxyz on 2009-07-25
it is a wireless router yes im sorry i didnt mention that. also i know that a wired method would indeed work but i dont have that kind of solution available to me cause running a cable throughout my house would not be acceptable. so i wanted to know what kind of card or otherwise that would work to get me onto my network along with my windows pc

---

### Post by pastalavista on 2009-07-25
My son packed up his desktop PC and carried it downstairs to connect to the router. 10 minutes later he had installed drivers for his wireless card, graphics card, wine (for his video games). Ubuntu can't put everything onto one 700mb CD (the DVD might have had your driver) but it is in the repositories freely available online.

---

### Post by 3rdalbum on 2009-07-26
> **fattyxyz said:**
> i recently made a new build with jaunty 9.04 but i ran into the problem that i expected when i installed ubuntu.
I have my work pc downstairs running a linksys router on windows xp   and i heard about an edimax network adapter that works with ubuntu out of the box but when i heard linksys doesnt work with ubuntu i got very confused and decided to get a better opinion
so in summary:what i could do to connect ubuntu to linksys on xp?
i apoligize for any confusion.

Any wireless router will work with Ubuntu, because the communication with the wireless clients follows a particular standard.

Your router is a stand-alone device. Windows XP is not running it. Windows XP is just accessing it, and your router works regardless of what's connected to it.

If you're having trouble connecting your Ubuntu machine to the router wirelessly, you're going to have to give us some information about what wireless network CARD you have. Just saying "it's a linksys" does not work, because Linksys uses a variety of different wireless chipsets from different vendors.

I'm going to give you some commands to put into the terminal, that should tell us what wireless chipset you have in your wireless card.

If it's a wireless card that's sitting in an expansion slot in your computer, type this:

```
lspci
```

If it's an external device that plugs into your USB port, type this:

```
lsusb
```

If it's built into your motherboard, then the information we need could be in either command.

Copy and paste the information from those commands into this thread, and we'll be able to help you.

---

