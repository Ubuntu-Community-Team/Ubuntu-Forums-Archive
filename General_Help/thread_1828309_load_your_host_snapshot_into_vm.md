---
title: "load your host snapshot into vm"
date: 2011-08-18
forum: General Help
---

### Post by tweakmy on 2011-08-18
Hi there,

Is there a possiblity to load your host snapshot into a virtualmachine and how?

Which vm would you use?

KVM or virtualbox or others?

Thanks in advance.


if this question has raised before (maybe rephrase in other way), please direct me to the link. Many thanks.

---

### Post by lmarmisa on 2011-08-18
> **tweakmy said:**
> Hi there,

Is there a possiblity to load your host snapshot into a virtualmachine and how?

Which vm would you use?

KVM or virtualbox or others?

Thanks in advance.


if this question has raised before (maybe rephrase in other way), please direct me to the link. Many thanks.

Yes, this is possible if you are running Ubuntu. I have done it several times. Do not try it with Windows. 

I recommend to make a backup of your system and then restore it on a VM. You can use Clonezilla for that backup.

In relation with a virtualization program, I like to use [VirtualBox]("http://www.virtualbox.org/") .

---

### Post by tweakmy on 2011-08-19
just checked clonezilla.

Is there a possibility to like somehow load your current snapshot without having to stop your current host and load it to the vm directly?

I would like this option to test a new enviroment after a patch to see whether it is still working before I performed actual on the host.

---

