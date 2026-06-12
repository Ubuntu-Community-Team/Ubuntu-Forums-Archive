---
title: "Which nvidia driver version is Ubuntu really using?"
date: 2010-07-21
forum: General Help
---

### Post by gnik1 on 2010-07-21
Under hardware drivers, it says that version 173 is being used. 
[IMG]http://foo.gearsector.com/foo/images/hardware.png[/IMG]

But under xserver settings version 256.35 is being used.
[IMG]http://foo.gearsector.com/foo/images/xserver.png[/IMG]

Which one is right? Are both versions being used? Do I need to update a another part of ubuntu to properly use the driver 256.35?

Thanks in advance

---

### Post by 3Miro on 2010-07-21
Of the two I would trust the Nvidia center, furthermore, why have you installed the 1.73 driver as opposed tot he latest recommended one. I am not even sure if the 1.73 is in deed the 1.73, this would look too old for me, but I cannot be sure.

At any rate this is some sort of a bug, whether it is in the readings of the Nvidia center or the package.

---

### Post by Frogs Hair on 2010-07-21
I have bug report filed on the jockey as it relates to the 256.35 driver . My jockey shows no Nvidia driver in use and X-Server Settings shows 256.35 to be in use. Synaptic pkg manager shows no other driver installed. I installed from the ppa so I'm wondering if there is a problem with the ppa.

---

### Post by 3Miro on 2010-07-21
> **Frogs Hair said:**
> I have bug report filed on the jockey as it relates to the 256.35 driver . My jockey shows no Nvidia driver in use and X-Server Settings shows 256.35 to be in use. Synaptic pkg manager shows no other driver installed. I installed from the ppa so I'm wondering if there is a problem with the ppa.

If you get it from a non-official ppa then it probably doesn't register with jockey. I am not sure if this qualifies as a "bug", but this is not the case here anyway. The driver here was installed via jockey.

---

### Post by endotherm on 2010-07-21
173 is the package version, but the actual build of the driver is 256.53. since they are differant executables (the driver is only a small peice of the package) they would have different version control numbers. it's even likely that the package contains several low level drivers, and one is selected at install. 

ATI does the same. their package is 10.3 or somthing, but the driver version itself is a much longer number.

---

### Post by gnik1 on 2010-07-21
ok, so i can be confident that the driver 256.35 is being used then


I have noticed a huge performance difference since updating the driver and now all effects are enabled. Firefox can have many tabs open without causing the screen to grey out when changing tabs.

What a relief. 

THanks

---

### Post by Frogs Hair on 2010-07-21
> **3Miro said:**
> If you get it from a non-official ppa then it probably doesn't register with jockey. I am not sure if this qualifies as a "bug", but this is not the case here anyway. The driver here was installed via jockey.

I worded that wrong , the jockey shows nvidia current installed but not in use and there are no other drivers present.

---

