---
title: "Problem With Kernel"
date: 2006-05-18
forum: General Help
---

### Post by hbinded on 2006-05-18
Hi, I just finished compiling the kernel (2.6.12-10-386). So far so good. The main reason for compiling was to enable support for my pci-raid card. It's an ITE8212. I finished compiling without errors and installed it accordingly. On a reboot into the new kernel, I got some error about not loading a module for the shell. I was then logged into a very limited shell. What could I have done wrong? 

p.s. Where can one get the logs the kernel outputs when booting?

---

### Post by steve.horsley on 2006-05-18
man dmesg
dmesg > boot.messages

---

