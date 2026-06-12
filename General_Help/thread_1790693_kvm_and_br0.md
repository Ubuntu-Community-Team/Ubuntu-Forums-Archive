---
title: "kvm and br0"
date: 2011-06-25
forum: General Help
---

### Post by hvn on 2011-06-25
Hi,

I have a question on the use of kvm and qemu. My hardware won't run the kvm and qemu-kvm packages. So I've only installed qemu. Now I want to do a remote connection via the br0 interface. However, after checking my network settings, all I have is eth0, lo and virbr0. According to some online docs, I would have to create br0 myself, after installing kvm. Is this correct, i.e. is it impossible to have the br0 interface without having kvm installed?

Thank you.

---

### Post by matthew.mattoon on 2011-10-12
Hi,

A bridged network interface does not require KVM.  So you should be able to configure and use it the same following a tutorial created for KVM.

Here is an article I wrote a while back on bridged interfaces in Ubuntu.

[http://blog.allanglesit.com/2011/02/create-a-bridged-interface-in-ubuntu/](http://blog.allanglesit.com/2011/02/create-a-bridged-interface-in-ubuntu/)

-matt

---

