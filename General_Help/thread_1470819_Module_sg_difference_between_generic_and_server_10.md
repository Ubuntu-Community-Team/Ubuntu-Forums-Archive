---
title: "Module sg difference between generic and server 10.04 x64"
date: 2010-05-03
forum: General Help
---

### Post by ithaca on 2010-05-03
Hi all,
some weeks ago I've installed ubuntu 10.04 beta desktop, in that version the module sg was present using modprobe (the sg.ko file was not present). I need the sg module because of some scsi driver that require it.
Today I've installed the 10.04 server  and modprobe sg returns a not found.
I would like to install it or make it visible as in the beta version. 
Can you help me?

Thanks

---

### Post by dino99 on 2010-05-03
dont know exactly what "sg" is but into synaptic there is packages: sg3-utils, libsgutils2-2

---

### Post by ithaca on 2010-05-03
Sg means scsi generic and I've read that in the versions previous to jaunty was a kernel module. Thanks for the suggestion I' check.

---

### Post by dino99 on 2010-05-03
> **ithaca said:**
> Sg means scsi generic and I've read that in the versions previous to jaunty was a kernel module. Thanks for the suggestion I' check.

maybe you can found some ppa with custom kernels but i doubt its really needed now

[https://launchpad.net/ubuntu/+ppas?name_filter=scsi](https://launchpad.net/ubuntu/+ppas?name_filter=scsi)

---

### Post by ithaca on 2010-05-03
For now what I noticed is that the command "modprobe sg" works only for the kernel versions 2.6.32.18 and 2.6.32.19 may I can try to use one of those

Makes sense for you?

---

### Post by dino99 on 2010-05-03
> **ithaca said:**
> For now what I noticed is that the command "modprobe sg" works only for the kernel versions 2.6.32.18 and 2.6.32.19 may I can try to use one of those

Makes sense for you?

yes of course, sometimes new kernels have regression sadly.

you might report a bug on launchpad, create an account before, against the kernel(s) giving you troubles.

into console:
ubuntu-bug "the complet kernel name used"

or 
ubuntu-bug linux
( every needed info is automatically grabbed and sent to devs)

note: are logs giving usefull errors ? (system admin log viewer)

---

### Post by ithaca on 2010-05-03
Now I'm trying to downgrade the kernel but with synaptic is it not possible because it has only the 2.6.32.21 and .20. (I mean on ubuntu 10.04 server)
Can you sugget me how to find a .19 kernel version?

Thanks a lot for your help.

---

### Post by dino99 on 2010-05-03
> **ithaca said:**
> Now I'm trying to downgrade the kernel but with synaptic is it not possible because it has only the 2.6.32.21 and .20. (I mean on ubuntu 10.04 server)
Can you sugget me how to find a .19 kernel version?

Thanks a lot for your help.

scroll down here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by ithaca on 2010-05-03
Thanks but seem that here are present only generic kernels until the version .13.... nothing about the server version.

---

