---
title: "GRUB2 Dual Root Partition Woes"
date: 2010-10-18
forum: General Help
---

### Post by J&#7885;hn on 2010-10-18
Hi All

A little while ago I upgraded a stack of machines from Hardy to Lucid. I kept the Hardy install and created a new partition for Lucid's root directory, expecting GRUB to correctly identify which root partition belonged to which OS installation, but it doesn't.

It incorrectly assigns all detected OSes to the same root partition which causes issues when the Hardy install is selected from the grub menu (as it tries to use the Lucid root partition).

As a workaround I manually created a grub script to appear at the top of the selection list when update-grub is invoked, but the problem now is whenever a machine is updated to a new kernel release I have to manually edit each machines grub files all over again to setup the menu correctly.

Has anyone any ideas for a workaround with this? It's a real pita.

Thanks

John

---

