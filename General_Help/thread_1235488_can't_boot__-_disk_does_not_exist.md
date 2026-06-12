---
title: "can't boot  - disk does not exist"
date: 2009-08-09
forum: General Help
---

### Post by xavier0912 on 2009-08-09
Hi all,
 
Just new to Linux, so sorry if I'm not making sense ;)
 
I installed Ubuntu 9.04 in dual boot with Window$ 7. First boot was ok but after I installed all updates, the system froze completly. Hard reboot gave the ubuntu splash screen and after that:
 
"gave up waiting for root device" ...
"alert! /dev/disk/by-uuid/d403d8fa-097f-4ab6-b8d3-ef8dae5360e7 does not exist. Dropping a shell!"
 
anybody have any advise for me on this ?
 
Thanks a lot !
btw, Win is on disk sda1
Ubuntu on sdb4
 
Xavier

---

### Post by SlugSlug on 2009-08-09
> **xavier0912 said:**
> Hi all,
 
Just new to Linux, so sorry if I'm not making sense ;)
 
I installed Ubuntu 9.04 in dual boot with Window$ 7. First boot was ok but after I installed all updates, the system froze completly. Hard reboot gave the ubuntu splash screen and after that:
 
"gave up waiting for root device" ...
"alert! /dev/disk/by-uuid/d403d8fa-097f-4ab6-b8d3-ef8dae5360e7 does not exist. Dropping a shell!"
 
anybody have any advise for me on this ?
 
Thanks a lot !
btw, Win is on disk sda1
Ubuntu on sdb4
 
Xavier

when your droped to a shell type 
sudo vi /etc/fstab  use the arrow keys to find that line and you'll notice something like 

# / was on /dev/sdb5 during installation
UUID=632d7f39-c179-43ef-8a21-972e34860858 /   

replace the UUID=0857925792520   for what it says in the line above (May case /dev/sdb5)

press  'esc : wq'  to save and quit

reboot

---

### Post by xavier0912 on 2009-08-09
Thanks for the quick response !
 
When I type sudo vi /etc/fstab
I get:
/bin/sh: sudo: not found
 
I must be doing something wrong, sorry for the dumbness ! :)

---

### Post by xavier0912 on 2009-08-09
> **xavier0912 said:**
> Thanks for the quick response !
 
When I type sudo vi /etc/fstab
I get:
/bin/sh: sudo: not found
 
I must be doing something wrong, sorry for the dumbness ! :)
 
Just noticed that I could load the 2.28.11 kernel in the grub list, but not the 2.28.14
This last one now gives following error:
 
boot from (hd1,5) ext4 ....
starting up ...
[10.788320] Kernel Panic - not suncing: VFS: Unable to mount root fs on unknown-block(0,0)
 
and than just the cursor ...

---

### Post by SlugSlug on 2009-08-09
try it with out the sudo

---

### Post by SlugSlug on 2009-08-09
> **xavier0912 said:**
> Just noticed that I could load the 2.28.11 kernel in the grub list, but not the 2.28.14
This last one now gives following error:
 
boot from (hd1,5) ext4 ....
starting up ...
[10.788320] Kernel Panic - not suncing: VFS: Unable to mount root fs on unknown-block(0,0)
 
and than just the cursor ...


humm well if you load the old kernel and type sudo grub-install 

it may help... ?

---

### Post by xavier0912 on 2009-08-09
It says install_device not specified ...
Is this sdb5 in my case ?
 
Thanks !

---

### Post by SlugSlug on 2009-08-09
> **xavier0912 said:**
> It says install_device not specified ...
Is this sdb5 in my case ?
 
Thanks !


not sure , do a sudo update-grub instead

---

### Post by xavier0912 on 2009-08-09
gives the same error as the last one, the kernel panic.
 
Should I reinstall the new kernel maybe ?

---

### Post by SlugSlug on 2009-08-09
> **xavier0912 said:**
> gives the same error as the last one, the kernel panic.
 
Should I reinstall the new kernel maybe ?


guess you could try

---

### Post by xavier0912 on 2009-08-09
Okay I'll try that one later.
Thanks for your help so far !
 
Greetz
Xavier

---

### Post by xavier0912 on 2009-08-09
looks like a reinstall did it !
I just selected everything I found for that kernel in synaptic en now it boots just fine.
 
Thanks again for the tips :)
 
Now I'll start fooling around in ubuntu.
 
Greetz
Xavier

---

### Post by SlugSlug on 2009-08-09
> **xavier0912 said:**
> looks like a reinstall did it !
I just selected everything I found for that kernel in synaptic en now it boots just fine.
 
Thanks again for the tips :)
 
Now I'll start fooling around in ubuntu.
 
Greetz
Xavier


nice one  :guitar:

---

