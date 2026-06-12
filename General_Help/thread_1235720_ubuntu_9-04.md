---
title: "ubuntu 9-04"
date: 2009-08-09
forum: General Help
---

### Post by kadaj6 on 2009-08-09
i installed it yesterday ssuccesfully but now i have 4 partitions to choose from...
ubuntu 9-04 kernel......
ubuntu 9-04 kernel.....(recovery)
ubuntu 9-04 kernel......
ubuntu 9-04 kernel......(recovery)

why is that?

---

### Post by snowpine on 2009-08-09
They aren`t partitions, rather various kernel options. Choose the first one; it`s your newest kernel. 

The second option is `recovery mode` which you won`t use except in case of an emergency.

The third option is the old kernel (from before you ran the update manager) which is good to have as an option in case there`s a problem with the new kernel. The fourth option is the recovery mode for the old kernel.

Hope that clears it up...

---

### Post by kadaj6 on 2009-08-09
oh thx ^^ 
that really helps
so the old ones are the one the give me for testing

---

### Post by snowpine on 2009-08-09
It is totally normal; nothing to worry about... just choose the first one, and be glad you have the other options in case there is a problem. 

The `kernel` is the most important part of linux, which controls your hardware. Sometimes you will get a new kernel through the update manager. This makes sure your system is up to date with the latest hardware drivers.

---

### Post by scouser73 on 2009-08-09
> **kadaj6 said:**
> i installed it yesterday ssuccesfully but now i have 4 partitions to choose from...
ubuntu 9-04 kernel......
ubuntu 9-04 kernel.....(recovery)
ubuntu 9-04 kernel......
ubuntu 9-04 kernel......(recovery)

why is that?

> They aren`t partitions, rather various kernel options. Choose the first one; it`s your newest kernel.

The second option is `recovery mode` which you won`t use except in case of an emergency.

The third option is the old kernel (from before you ran the update manager) which is good to have as an option in case there`s a problem with the new kernel. The fourth option is the recovery mode for the old kernel.

Hope that clears it up...

Follow this tutorial for removing old kernels - [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by snowpine on 2009-08-09
> **scouser73 said:**
> Follow this tutorial for removing old kernels - [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

Why?? It is a good idea to keep a spare kernel, just in case...

---

