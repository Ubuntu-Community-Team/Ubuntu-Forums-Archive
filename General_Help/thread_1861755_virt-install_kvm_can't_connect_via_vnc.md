---
title: "virt-install kvm can't connect via vnc"
date: 2011-10-16
forum: General Help
---

### Post by morrty11 on 2011-10-16
I'm trying to install a Windows Server 2003 virtual machine with virt-install.

I type in:
```
sudo virt-install --connect qemu:///system -n vm0 -r 4096 --vcpus=1 -f /home/ryan/vms/vm0.qcow2 -s 120 -c /home/ryan/vms/images/win2k3cd1.iso --vnc --noautoconsole --os-type=windows --os-variant=win2k3 --hvm --network=bridge:br0
```

I can't vnc to the vm. I type:
```
sudo netstat -anltp | grep "LISTEN"
```

and nothing comes up for vnc. or even in the 5000-6000 port range.

how do I get my server (Ubuntu 10.04 LTS) to listen to the vnc port?

---

### Post by morrty11 on 2011-10-16
Alright, apparently my issue was that virt-install was just taking forever to create the hard drive. I specified a 120GB hard drive for it and it won't let you VNC into the VM until it is finished creating the hard drive and installing the VM. Once it was done doing this I was able to see my VM with
```
sudo virsh list --all
```

Then I was able to connect via VNC.

---

