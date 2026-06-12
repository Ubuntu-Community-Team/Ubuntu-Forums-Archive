---
title: "How do I delete a kvm guest?"
date: 2009-11-11
forum: General Help
---

### Post by thk on 2009-11-11
I'm trying to install a kvm guest with the following command. I used this command previously, but aborted the install. It seems virt-install ignores the --name switch? It seems to have created a guest with the name "c" and now I cannot run virt-install as it says the guest "c" is already created.

I have no idea where any state is stored by libvirt. I cannot find the guest. Its not listed by virsh, but does appear in virt-top. How can I delete the existing guest? 

```
root@robustus:/mnt/scratch/root/kvm# virt-install \
--connect=qemu:///system \
--name=windows-xp-testing -r 4000 --vcpus 4 \
--cpuset=auto --os-type=windows --os-variant=winxp64 \
--accelerate --disk path=./windows-xp-testing.qcow2,size=32 \
--network=bridge:br0 -vnc \
--cdrom=../SW_CD_Windows_XP_Professional_64BIT_English_iso_MLF_X13-39980.ISO 
ERROR    Guest name 'c' is already in use.

```

---

### Post by Fungyo on 2009-12-12
would also like to know, how?

---

### Post by mammothFoot on 2010-04-24
Hey,

Sorry to put back this old post, but I have had the same problem and found a solution :
```

virsh undefine c

```

Solution obtained thanks to the approved rtfm method.

mF

---

