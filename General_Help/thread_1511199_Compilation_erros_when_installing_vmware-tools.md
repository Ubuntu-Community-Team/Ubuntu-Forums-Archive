---
title: "Compilation erros when installing vmware-tools"
date: 2010-06-16
forum: General Help
---

### Post by rshackleford on 2010-06-16
I am running into errors when trying to install vmware-tools from Vmware Workstation. There are no precompiled modules that work and trying to compile the modules yields fatal errors for every module. I would love to run 10.04 LTS but my hands are somewhat tied if I can't get vmware-tools to install. Performance is terrible without them.

---

### Post by dabl on 2010-06-16
I'm not sure exactly what you're attempting to do, but I'll tell you what works reliably (3 Linux OS's on 3 different computers).

1. Download VMware Player -- get the .bundle package, 32-bit or 64-bit as applicable.

[https://www.vmware.com/tryvmware/?p=player](https://www.vmware.com/tryvmware/?p=player)

2. Copy the downloaded file into /tmp, shut down the X server with ```
sudo service gdm stop
```, and run the installer from the /tmp directory with ```
sudo sh VM{Tab-to-complete)
```

3. When it is done installing VMware Player, restart X with ```
sudo service gdm start
```

4. Use the "Create a new VM" feature, pick your virtual hard disk size, and install from your bootable CD.

5. After installation, on first boot of the VM, it offers to install VMware tools.  Accept, and let it install them.

6. Restart the VM and you should be in good shape.

I've done this with Win XP and Win 7 -- I haven't done it with a Linux VM.

---

### Post by rshackleford on 2010-06-16
Thanks for your reply.
 
What I am trying to do is install 10.04 as a guest vm on Vmware workstation running on XP. that is successful but when I try to install vmware-tools on the 10.04 guest it blows up with a bunch of compiler errors

---

