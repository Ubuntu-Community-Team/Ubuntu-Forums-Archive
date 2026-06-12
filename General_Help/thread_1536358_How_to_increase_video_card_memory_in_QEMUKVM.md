---
title: "How to increase video card memory in QEMU/KVM"
date: 2010-07-22
forum: General Help
---

### Post by nidzo732 on 2010-07-22
I've been using QEMU/KVM to try diferent operating systems , just for fun. But some systems reguire better graphics than the video cards offered in QEMU/KVM.I use a gui called Aqemu , it offers folowing GPUs:
-StdVGA(vesa 2.0)
-cirrus clgd 5446
-vmware video card
Is any of theese better than default?Is there any way to scale video memory (just like in VirtualBox)? I have to use VirtualBox when i try a system that reqires better GPU, and VB is much slower then QEMU/KVM.

---

### Post by dcstar on 2010-07-22
> **nidzo732 said:**
> I've been using QEMU/KVM to try diferent operating systems , just for fun. But some systems reguire better graphics than the video cards offered in QEMU/KVM.I use a gui called Aqemu , it offers folowing GPUs:
-StdVGA(vesa 2.0)
-cirrus clgd 5446
-vmware video card
Is any of theese better than default?Is there any way to scale video memory (just like in VirtualBox)? I have to use VirtualBox when i try a system that reqires better GPU, and VB is much slower then QEMU/KVM.

VM questions belong in the Virtualization forum.

---

### Post by nidzo732 on 2010-07-22
I've posted it there but i got no answer.

---

### Post by manzdagratiano on 2010-09-18
The above mentioned options are also available in the command-line version of qemu-kvm via the switches -vga std, or -vga cirrus, or -vga vmware, so there is no need to use the GUI. I am however myself looking for the answer to how to increase the video card memory in qemu.

---

