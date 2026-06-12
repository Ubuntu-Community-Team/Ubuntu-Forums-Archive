---
title: "Ubuntu keeps going read-only"
date: 2010-10-27
forum: General Help
---

### Post by xtheunknown0 on 2010-10-27
Around a month ago I installed Ubuntu 10.04 as a virtual machine on VBox and I was really happy. But then after a while I would try to run a graphical program, launching it from a command in the CLI and I would get errors saying that the system was read-only.

Well now I've installed Ubuntu 9.10, same setup. It's been a couple of weeks now and I get this exact same problem.

Why?

TIA,
Fred

---

### Post by xtheunknown0 on 2010-10-29
Bump

---

### Post by dcstar on 2010-10-29
> **xtheunknown0 said:**
> Around a month ago I installed Ubuntu 10.04 as a virtual machine on VBox and I was really happy. But then after a while I would try to run a graphical program, launching it from a command in the CLI and I would get errors saying that the system was read-only.

Well now I've installed Ubuntu 9.10, same setup. It's been a couple of weeks now and I get this exact same problem.

Why?


Systems that are not shutdown correctly end up with "dirty" root filesystems that are mounted as read-only on the next boot.

They need to have fsck run on them to resolve the problem.

---

### Post by xtheunknown0 on 2010-10-30
> **dcstar said:**
> Systems that are not shutdown correctly end up with "dirty" root filesystems that are mounted as read-only on the next boot.

They need to have fsck run on them to resolve the problem.

Is data safe if fsck needs to be run again and again?

So shutting down a VM is much more preferable to saving the machine state?

TIA,
xtheunknown0

---

### Post by matt_symes on 2010-10-30
Hi 

Yes. Shutdown the VM. Saving state is for taking a snap shot of the OS. Run fsck on your VM drive but make sure the drive is not mounted when you run it. That should fix the problem.

Kind regards

---

### Post by xtheunknown0 on 2010-10-30
> **matt_symes said:**
> Yes. Shutdown the VM. Saving state is for taking a snap shot of the OS. Run fsck on your VM drive but make sure the drive is not mounted when you run it. That should fix the problem.

Thank you for your help and advice.

---

