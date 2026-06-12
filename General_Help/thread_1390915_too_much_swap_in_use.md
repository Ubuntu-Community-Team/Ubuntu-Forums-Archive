---
title: "too much swap in use"
date: 2010-01-26
forum: General Help
---

### Post by anaconda on 2010-01-26
I have a strange problem.

I have 1GB of RAM, and 2GB of swap.But currently ubuntu (8.04) is USING
329MB of RAM and 622MB swap 

And the machine is very slow, probably because it uses too much swap, even if swap shouldn't be needed at all..  

I had the same problem a few hours ago, and a reboot helped for a few hours.. but now the situation is back.

wtf?

---

### Post by plucky on 2010-01-26
> **anaconda said:**
> I have a strange problem.

I have 1GB of RAM, and 2GB of swap.But currently ubuntu (8.04) is USING
329MB of RAM and 622MB swap 

And the machine is very slow, probably because it uses too much swap, even if swap shouldn't be needed at all..  

I had the same problem a few hours ago, and a reboot helped for a few hours.. but now the situation is back.

wtf?

You could use ```
sudo swapoff -a
``` to turn off swap and dump the contents back to memory and then turn it back on with ```
sudo swapon -a
```


OR

To make the system use the swap partition less you should add the parameter "vm.swappiness=10" to the end of the file /etc/sysctl.conf

```
gksudo gedit /etc/sysctl.conf
```

Add the line at the end of the file ```
vm.swappiness=10
```

And reboot.

Good Luck

---

### Post by warfacegod on 2010-01-26
Another solution is to install Ailurus. It can change your swappiness and it allot of other useful tools as well.

---

### Post by anaconda on 2010-01-26
Hey,
Thanks plucky and warfacegod.

the swapoff swapon thing worked, and I also changed the swappiness value. 

And I will check out ailurus too
.

---

### Post by warfacegod on 2010-01-26
There's another one called Ubuntu Tweak. It makes finding some system settings allot easier.

---

