---
title: "my kernel is broken after updating !!helppp"
date: 2010-01-26
forum: General Help
---

### Post by ibrahim.k on 2010-01-26
I have used a program called kernel chick to update my kernel i am using 9.10 karmic but after the update operation many things are broken the tasks bar is not working also i cant close my active windows !!! the is no close or minimize shorcuts pleaseee helpp me


can i get the old kernel back ??

:(

---

### Post by lotharmat on 2010-01-26
> **ibrahim.k said:**
> I have used a program called kernel chick to update my kernel i am using 9.10 karmic but after the update operation many things are broken the tasks bar is not working also i cant close my active windows !!! the is no close or minimize shorcuts pleaseee helpp me


can i get the old kernel back ??

:(


What version of GRUB do you have?

---

### Post by ibrahim.k on 2010-01-26
**Dude i am a newbie can you please tell me what is the GRUB ?**




> **lotharmat said:**
> What version of GRUB do you have?

---

### Post by ibrahim.k on 2010-01-26
I can boot successfully how can i know what is my GRUB anyway ?

---

### Post by apjone on 2010-01-26
I am note sure if this is update related or not but last night both a work mate and myself had issues with 9.10 not booting. It appears that for some reason the root partition can not be mounted and you are dropped into maintenance mode with a simple shell. Not thinking ( dead on feet from work ) I just did 

```

fsck -a
mount -a

```

followed by CTRL+D to resume booting. This fixed the issue. I have not looked through my logs yet (probably wont be able to spot it now) to see what caused this.

Just a heads up though! :D

---

### Post by ibrahim.k on 2010-01-26
Thank you very much my friend but I can boot already !!! the problem is that there is no icons or shortcuts to close, minimize or maximize a windows also the gnome panel is not working 



> **apjone said:**
> I am note sure if this is update related or not but last night both a work mate and myself had issues with 9.10 not booting. It appears that for some reason the root partition can not be mounted and you are dropped into maintenance mode with a simple shell. Not thinking ( dead on feet from work ) I just did 

```

fsck -a
mount -a

```followed by CTRL+D to resume booting. This fixed the issue. I have not looked through my logs yet (probably wont be able to spot it now) to see what caused this.

Just a heads up though! :D

---

### Post by apjone on 2010-01-26
my bad........... didnt read post completely.

---

### Post by ibrahim.k on 2010-01-26
its okay never mind thank you for ur help

---

### Post by ibrahim.k on 2010-01-26
help :(

---

