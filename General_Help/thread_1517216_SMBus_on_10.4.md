---
title: "SMBus on 10.4"
date: 2010-06-24
forum: General Help
---

### Post by Frogster on 2010-06-24
Can somebody tell me what the SMBus actually does? I have found descriptions of what it is but not what it is used for.

Does my pc suffer by not having it working and if so how do I get it to work?

---

### Post by mooreted on 2010-06-24
It can be used for monitoring, triggering events, acpi or pretty much whatever the motherboard or chipset manufacturer wants to use it for.

What makes you think yours isn't working? Is there something your computer can't do? Is it a VIA chipset?

From a terminal do:

lspci

You should see something like:

SMBus: nVidia Corporation MCP61 SMBus (rev a2)

---

### Post by Frogster on 2010-06-25
Good morning 

Thank you for the reply

lspci returned this

```
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)

```

Amongst many other items

So I guess it is there and working. The reason I asked was that "Hardware Lister" stated that it wasn't working. Everything seems to work on the pc and I was intrigued. 

Your reply is greatly appreciated thank you :p

---

