---
title: "Does  qemu-kvm not support qcow2 encryption?"
date: 2010-02-28
forum: General Help
---

### Post by roeland on 2010-02-28
I just tried to create a qemu qcow2 image with encryption:

```
qemu-img create -e -f qcow2 foo.qcow2 100G
Formatting 'foo.qcow2', fmt=qcow2 size=107374182400 encryption=on cluster_size=0
```

Hmm, it's some time ago I played with qemu, but I think it's supposed to ask for a password. If I start the image with
```
qemu foo.qcow2
```
it just says 'QEMU [Stopped]' in the popup terminal window. It starts normally without the encryption option on qemu-img.

Is encryption known to be broken? Is this perhaps  specific to qemu with KVM patch or to the 64-bit version?

Ubuntu 9.10
qemu-kvm 0.11.0-0ubuntu6.3
Linux wallace 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

---

### Post by bodhi.zazen on 2010-03-26
> **roeland said:**
> I just tried to create a qemu qcow2 image with encryption:

```
qemu-img create -e -f qcow2 foo.qcow2 100G
Formatting 'foo.qcow2', fmt=qcow2 size=107374182400 encryption=on cluster_size=0
```Hmm, it's some time ago I played with qemu, but I think it's supposed to ask for a password. If I start the image with
```
qemu foo.qcow2
```it just says 'QEMU [Stopped]' in the popup terminal window. It starts normally without the encryption option on qemu-img.

Is encryption known to be broken? Is this perhaps  specific to qemu with KVM patch or to the 64-bit version?

Ubuntu 9.10
qemu-kvm 0.11.0-0ubuntu6.3
Linux wallace 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

I came across your post today, lol

See : [http://blog.bodhizazen.net/linux/kvm-how-to-use-encrypted-images/](http://blog.bodhizazen.net/linux/kvm-how-to-use-encrypted-images/)

---

### Post by roeland on 2010-03-26
Thanks a lot, Bodhi. I had only recently figured it out myself, by way of this bug report on the Redhat site (they co-develop KVM I think):
[https://bugzilla.redhat.com/show_bug.cgi?id=491381](https://bugzilla.redhat.com/show_bug.cgi?id=491381)

To others who may run into this, Bodhi's blog gives the most useful solution.

---

