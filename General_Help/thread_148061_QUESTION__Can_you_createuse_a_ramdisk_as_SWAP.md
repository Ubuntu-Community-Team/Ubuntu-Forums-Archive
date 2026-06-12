---
title: "QUESTION : Can you create/use a ramdisk as SWAP?"
date: 2006-03-21
forum: General Help
---

### Post by DaBruGo on 2006-03-21
My reason for asking is this ...

I have a usb memory stick with a "server" configuration loaded on it, because it takes up a small amount of space on the sandisk unit. (I am going to add a minimalist GUI later.)

My PC would have at least 256MB of ram, so I was wondering if I can setup a ramdisk as swap space instead of using a swap partition on the memory stick, since swap space apparently really ages the usb flash drives. (Also, which is better on flash units, ext2 or ext3?)

If this is possible, how would I go about doing this (howto/tutorial etc)?


DAVE

---

### Post by rmjokers on 2006-03-21
I think you would be better off just disabling swap completely than trying to use part of the system RAM as swap.  This would be less efficient than just using the RAM as RAM.  Is there a particular reason why you need a swap partition?

---

### Post by ssam on 2006-03-21
i agree with rmjokers you should probably disable swap. just commend out the swap line in your fstab, or use the swapoff command.

with flash memory you want to limit the nuber of writes. i'd imagine ext2 to be better (i assume the journaling requires extra writes). also use the noatime option (this prevents a write on every read). maybe look at laptop mode for caching writes. also you could turn off some of the logging.

---

### Post by AndrewCaul on 2006-03-21
Using a RAM disk for swap isn't a good idea. Basically you'd be storing RAM in RAM, defeating the very purpose of a swap file. Simply disabling it will be just as, if not more, effective.

---

### Post by DaBruGo on 2006-03-21
Thanks everyone,

I am just trying to limit the amount of activity on the usb memory stick to a minimum (only writing what is necessary to save files/settings etc) to extend the unit's life. So what you all are saying is let the RAM do all the work unless I really need to save data to the memory stick. (I should skip the usage of swap alltogether.) Am I understanding this right?

Also, I was wondering if there are some apps that require a swap file to function properly in linux?


DAVE

PS : Got any thoughts on this [link]("http://ubuntuforums.org/showthread.php?t=148058")

---

