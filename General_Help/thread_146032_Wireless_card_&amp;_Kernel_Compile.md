---
title: "Wireless card &amp; Kernel Compile"
date: 2006-03-17
forum: General Help
---

### Post by Dauphinfay on 2006-03-17
I have an Atheros based card (dwl-g630) and I want to compile a new kernel (2.6.15-6). What I don't understand is that with a standard install of ubuntu I am able to get the card working w/o using the cli to configure ndiswrapper. How do I setup so that I can do it the same way with the new kernel? Please point me in the right direction. TIA

---

### Post by Steve1961 on 2006-03-18
[QUOTE=Dauphinfay]I have an Atheros based card (dwl-g630) and I want to compile a new kernel (2.6.15-6). What I don't understand is that with a standard install of ubuntu I am able to get the card working w/o using the cli to configure ndiswrapper. How do I setup so that I can do it the same way with the new kernel? Please point me in the right direction. TIA[/QUOTE]

When you compile your new kernel make sure that you select support for the Atheros chipset when running make xconfig.  You could also use the existing ubuntu config file (you'll find it in /boot) and start by running make oldconfig.

---

