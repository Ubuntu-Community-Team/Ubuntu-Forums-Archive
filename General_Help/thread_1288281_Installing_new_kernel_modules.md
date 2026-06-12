---
title: "Installing new kernel modules"
date: 2009-10-11
forum: General Help
---

### Post by RuleMaker on 2009-10-11
I'd like to get my acpi working but it requires [some kernel modules]("http://tldp.org/HOWTO/ACPI-HOWTO/loadmodules.html") which I don't have.
I have read a tutorial on how to compile new modules without recompiling the whole kernel [here]("http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html"), but I have no idea where could I get at least the source code for the required modules.

---

### Post by Lars Noodén on 2009-10-11
Please list each module you want.

---

### Post by RuleMaker on 2009-10-11
Button, fan, ac, thermal and processor.

---

### Post by Lars Noodén on 2009-10-11
There is the package lm-sensors which will give some control over the fan.

---

### Post by RuleMaker on 2009-10-11
Yeah, I have installed it but it seems that acpi uses another modules to get info about hardware.

I just wanted to get the acpi working too because conky uses it...

---

