---
title: "Mounting an offset within dd image"
date: 2011-03-08
forum: General Help
---

### Post by twjolson on 2011-03-08
I am writing a script, and I want the ability to mount dd created images at a specific offset.

For instance, using dd, you create an image of a whole hard drive, all partitions.  The script then comes and mounts the partition located at offset 63 (or whatever the user picks).

I do not see this option in the mount command.  No other searches turned up anything meaningful.  So I am bowing to the gurus.

Any help would be gratefully accepted.

---

### Post by twjolson on 2011-03-08
Or, if anyone knows a forums devoted to bash shell scripting, that'd be much obliged as well.

---

### Post by tredegar on 2011-03-08
**mount -o loop** can take an offset.

Maybe [this post]("http://www.linuxquestions.org/questions/linux-software-2/mounting-a-single-fat32-partition-inside-a-full-disc-image-776922/#post3798799") will help you.

---

### Post by aeiah on 2011-03-08
is there a reason why you dont treat the dd image like a physical device? you should be able to map the image as a device, and then mount the partitions contained within like normal. 

....


ok, ive just dug out a bookmark that explains the process, and it might end up being more complicated to script than mounting at an offset :P

[http://equivocation.org/node/107](http://equivocation.org/node/107)

ignore the kvm references, these are normal dd images of hard drives for all intents and purposes.

---

### Post by twjolson on 2011-03-08
> **tredegar said:**
> **mount -o loop** can take an offset.

Maybe [this post]("http://www.linuxquestions.org/questions/linux-software-2/mounting-a-single-fat32-partition-inside-a-full-disc-image-776922/#post3798799") will help you.

Wow, I have never seen offset as a parameter for -o.  In my defense, the man page for mount is quite long...

---

