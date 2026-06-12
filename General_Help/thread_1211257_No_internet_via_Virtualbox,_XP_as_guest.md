---
title: "No internet via Virtualbox, XP as guest"
date: 2009-07-12
forum: General Help
---

### Post by ump001 on 2009-07-12
I've installed xp as a guest OS, but i'm being prompted to install all the drivers? not sure why these are not being picked up as usual. Would this effect the guest OS access the internet via the main host OS?

If so, can i download all the required XP drivers from somewhere all at once?

Have searched thr forum and read many posts. Some point to installing Victualbox directly from the site which i have done and also changing the network card options which i have also tried.

---

### Post by ump001 on 2009-07-13
bump!

---

### Post by sanemanmad on 2009-07-13
More details please..

IP address of guest, network Host is on ie(192.168.x.x) and can you ping anything at all. 

Please post results of this command in terminal of virtual host, do not use sudo either, this command must be ran as user who started the virtual machine. ```
VBoxManage showvminfo "your_vm_name_here"
```

basically this shows the configuration details of the VM

---

### Post by Freezing on 2009-07-13
have you tried fixing the settings for network adapter on virtual box.

---

