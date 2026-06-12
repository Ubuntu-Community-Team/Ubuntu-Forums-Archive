---
title: "disable modules from kernel"
date: 2011-11-23
forum: General Help
---

### Post by JCM_Pico on 2011-11-23
Hi there,

I wonder if its possible to disable certain modules that I don't use, for instance the Card Reader.
I'm asking this because I'm getting huge filesystem logs due to a malfunction of the sdhci....
If yes how can I disable it 


```
[  864.140001] mmc0: Unexpected interrupt 0x04000000.
[  864.140006] sdhci: =========== REGISTER DUMP (mmc0)===========
[  864.140011] sdhci: Sys addr: 0xffffffff | Version:  0x0000ffff
[  864.140016] sdhci: Blk size: 0x0000ffff | Blk cnt:  0x0000ffff
[  864.140020] sdhci: Argument: 0xffffffff | Trn mode: 0x0000ffff
[  864.140025] sdhci: Present:  0xffffffff | Host ctl: 0x000000ff
[  864.140030] sdhci: Power:    0x000000ff | Blk gap:  0x000000ff
[  864.140035] sdhci: Wake-up:  0x000000ff | Clock:    0x0000ffff
[  864.140039] sdhci: Timeout:  0x000000ff | Int stat: 0xffffffff
[  864.140044] sdhci: Int enab: 0xffffffff | Sig enab: 0x04000000
[  864.140049] sdhci: AC12 err: 0x0000ffff | Slot int: 0x0000ffff
[  864.140053] sdhci: Caps:     0xffffffff | Caps_1:   0xffffffff
[  864.140058] sdhci: Cmd:      0x0000ffff | Max curr: 0xffffffff
[  864.140062] sdhci: Host ctl2: 0x0000ffff
[  864.140066] sdhci: ADMA Err: 0xffffffff | ADMA Ptr: 0xffffffff
[  864.140068] sdhci: ===========================================
```

---

### Post by hwttdz on 2011-11-23
lsmod will list currently loaded kernel modules
rmmod will remove a loaded module
I'm not quite clear on the differences between insmod and modprobe, but both I believe can be used to load modules.
Generally blacklisting a module is how you prevent it loading at startup. 
Also take a look at /etc/modprobe.d

So if you wanted to do this you'd blacklist the module and then restart.  Of course be careful.

---

### Post by hal8000 on 2011-11-23
I believe insmod and rmmod are deprecated now and the preferred way to load modules is with modprobe.


Also modprobe -r
will remove a module and also any depencies of the module.



Add your module to
/etc/modprobe.d/blacklist

Which will prevent it loading on boot.
Should your system fail to boot then load the live ubuntu cd, mount the / filesystem and restore /etc/modprobe.d/blacklist

---

### Post by JCM_Pico on 2011-11-24
I tryed to use modprob -r sdhci
and I got FATAL: Module sdhci is in use !!!!!!!!

How can I disable a module in use?

I'm willing to disable the module because I get huge log files...

ls /var/log/logsys
24G 2011-11-24 15:45 syslog

If you have any other idea to solve this I'm glade to consider it

---

### Post by matt_symes on 2011-11-24
Hi

From the terminal.

```
sudo bash -c "echo blacklist sdhci >> /etc/modprobe.d/blacklist.conf"
```

```
sudo reboot
```

Kind regards

---

### Post by tomgibson on 2012-05-19
I am having problems permenantly removing a kernel module from my system.

I  previously had libvirt and KVM installed on my computer, however I  decided to use virtualbox instead so removed KVM. Virtualbox complains  every time I boot that the kvm-amd module is loaded, if I do rmmod  kvm-amd it will then work, however this is annoying.

How can I  permanently remove the kvm-amd kernel module from my PC? I do not see  the sense in adding it to a 'blacklist' surely the module is then still  present on my system? It wasn't on my PC when I first installed ubuntu,  how can I return my installation to this state?

---

### Post by matt_symes on 2012-05-19
Hi

> **tomgibson said:**
> I am having problems permenantly removing a kernel module from my system.

I  previously had libvirt and KVM installed on my computer, however I  decided to use virtualbox instead so removed KVM. Virtualbox complains  every time I boot that the kvm-amd module is loaded, if I do rmmod  kvm-amd it will then work, however this is annoying.

How can I  permanently remove the kvm-amd kernel module from my PC? I do not see  the sense in adding it to a 'blacklist' surely the module is then still  present on my system? It wasn't on my PC when I first installed ubuntu,  how can I return my installation to this state?

Please post the output of 

```
ls /etc/init/qemu-kvm.conf
```

and 

```
dpkg -l | grep -E "qemu|kvm|libvirt"
```

Case is important. Small L after dpkg.

Finally

```
ls /usr/bin/kvm
```

Kind regards

---

