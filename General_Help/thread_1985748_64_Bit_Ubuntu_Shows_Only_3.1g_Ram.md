---
title: "64 Bit Ubuntu Shows Only 3.1g Ram"
date: 2012-05-23
forum: General Help
---

### Post by TheYetiWakes on 2012-05-23
Having 4gb of ram installed I would imagine the 64bit version of Ubuntu would show it all but it only states 3.1g?  Is this a quirk of Ubuntu or something more?  

free -m shows:

```
             total       used       free     shared    buffers     cached
Mem:          3136       2990        146          0        167       1588
-/+ buffers/cache:       1234       1902
Swap:         3197          5       3192


```

---

### Post by Vaphell on 2012-05-23
maybe you have some integrated gfx chip that uses some ram for its purposes?

---

### Post by kanikilu on 2012-05-23
900+MB seems like an awful lot for the system to be reserving for integrated video. I have a desktop with 8GB of RAM and the integrated Intel graphics is only using ~256MB.

Maybe your BIOS needs to be updated or there is a setting in there to enable a 64-bit OS?

[http://ubuntuforums.org/showthread.php?t=979441](http://ubuntuforums.org/showthread.php?t=979441)

---

### Post by TheYetiWakes on 2012-05-23
> **Vaphell said:**
> maybe you have some integrated gfx chip that uses some ram for its purposes?

Wouldn't think it is that.  Setup is a separate Radeon X1900XT graphics card on an Aus P5WDH Deluxe motherboard. I've done a search around and seen a couple of posts with the same query but no answers.

---

### Post by oldfred on 2012-05-23
Is BIOS showing all 4GB?

Try running memory test from grub menu.  Sometimes one bank of memory is bad. You can remove & clean contacts with an eraser and remove bits with alcohol before reinserting. 

Just to confirm version.
```

uname -a
```

---

### Post by jadtech on 2012-05-23
not saying this apply s how ever it looks and sounds like it fits to me .. 

[http://askubuntu.com/questions/32272/why-does-ubuntu-only-show-3gb-of-ram](http://askubuntu.com/questions/32272/why-does-ubuntu-only-show-3gb-of-ram)

rad through all the solutions to the end

---

### Post by TheYetiWakes on 2012-05-24
> **oldfred said:**
> Is BIOS showing all 4GB?

Try running memory test from grub menu.  Sometimes one bank of memory is bad. You can remove & clean contacts with an eraser and remove bits with alcohol before reinserting. 

Just to confirm version.
```

uname -a
```

Yes, BIOS shows the lot.  It also shows up in the dual boot to windows so I'm assuming its not a physical problem.

---

### Post by plucky on 2012-05-24
What about the ```
uname -a
```?

---

### Post by eleftg on 2012-05-24
look for something like "memory remap" or "memory extension" in your bios settings and enable it. It will do the trick

---

### Post by TheYetiWakes on 2012-05-24
> **plucky said:**
> What about the ```
uname -a
```?

It outputs the following, 64 bit Ubuntu: 

> Linux Desktop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by TheYetiWakes on 2012-05-24
> **eleftg said:**
> look for something like "memory remap" or "memory extension" in your bios settings and enable it. It will do the trick

Well done Sir, that sorted it.  Now reporting 3.9g.  Thank you very much.

---

