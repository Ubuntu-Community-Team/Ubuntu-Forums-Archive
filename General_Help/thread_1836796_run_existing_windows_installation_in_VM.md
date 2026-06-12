---
title: "run existing windows installation in VM"
date: 2011-08-31
forum: General Help
---

### Post by loolooyyyy on 2011-08-31
is it possible?
i dont need access to files, i dont want install win again through vm, just want to run existing one in sda1 through VM, is it possible?

---

### Post by haqking on 2011-08-31
> **loolooyyyy said:**
> is it possible?
i dont need access to files, i dont want install win again through vm, just want to run existing one in sda1 through VM, is it possible?

you will get lots of answers and there are lots of threads on this.

I find the easiest way is to take an image of it using clonezilla then create a VM harddisk the same size or larger than the image you took, create the VM with settings, boot to the clonezilla live CD and enable the source where the image is from the VM menu and then image it back to your VM.

Easy peasy lemon squeezy ;-)

[www.clonezilla.org](www.clonezilla.org)

---

### Post by loolooyyyy on 2011-08-31
> **haqking said:**
> you will get lots of answers and there are lots of threads on this.

I find the easiest way is to take an image of it using clonezilla then create a VM harddisk the same size or larger than the image you took, create the VM with settings, boot to the clonezilla live CD and enable the source where the image is from the VM menu and then image it back to your VM.

Easy peasy lemon squeezy ;-)

[www.clonezilla.org]("http://www.clonezilla.org")

tanx for quick reply
sadly this way the changes done later to partition wont affect VM
anything else i can do?

---

### Post by haqking on 2011-08-31
> **loolooyyyy said:**
> tanx for quick reply
sadly this way the changes done later to partition wont affect VM
anything else i can do?

ahh you never said that ;-)

yes it is possible, there are a few threads on here, check out the virtualisation sub-forum and you will find some there, but dont multipost this request there.

also check out this

[http://en.gentoo-wiki.com/wiki/Running_a_VirtualBox_Guest_from_a_Real_Partition](http://en.gentoo-wiki.com/wiki/Running_a_VirtualBox_Guest_from_a_Real_Partition)

it is a gentoo wiki but principles are the same

also read here

[http://forums.virtualbox.org/viewtopic.php?t=1966](http://forums.virtualbox.org/viewtopic.php?t=1966)

---

### Post by bodhi.zazen on 2011-08-31
It is not easy or advised to run a Windows partition in a VM. This is because the virtual hardware is not the same as the physical hardware and Windows will complain. You will need to do a google search and learn how to write a hardware profile for windows.

It is far better to do a fresh install into a virtual hard drive or image your windows partition as advised.

---

### Post by loolooyyyy on 2011-08-31
> **bodhi.zazen said:**
> It is not easy or advised to run a Windows partition in a VM. This is because the virtual hardware is not the same as the physical hardware and Windows will complain. You will need to do a google search and learn how to write a hardware profile for windows.

It is far better to do a fresh install into a virtual hard drive or image your windows partition as advised.
oh yes i hate messing with windows, i dont know how to fix it when i messed up!
tanx to both of you

---

