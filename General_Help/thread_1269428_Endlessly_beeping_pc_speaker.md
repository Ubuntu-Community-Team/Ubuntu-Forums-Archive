---
title: "Endlessly beeping pc speaker"
date: 2009-09-18
forum: General Help
---

### Post by 01000111 on 2009-09-18
Greetings all,
I recently upgraded my video card to a Nvidia GeForce 8400 GS in a PCI-E 16x slot.  I'm very happy with the results both on the VGA and DVI ports.  Everything is working beautifully, except...

Since the upgrade, every now and then when I boot, the PC speaker starts beeping very rapidly.  By the time the gui is displayed, the beeping has become a single, steady, endless tone.

The cure so far has to reboot, and the problem is solved, but I'd rather have an actual solution.

I'm running Xubuntu Jaunty on a dual-core AMD64 X2 5000 with 2GB ram.

Attached are a DMESG dump from when the beeping was happening, and another about 60 seconds later when it wasn't.  No changes between the two, other than rebooting.

Thanks in advance for the assistance.

G

---

### Post by TheStroj on 2009-09-18
By saying PC speaker, you mean BIOS speaker? There is an easy solution for that so please answer.

---

### Post by 01000111 on 2009-09-18
> **TheStroj said:**
> By saying PC speaker, you mean BIOS speaker? There is an easy solution for that so please answer.

Yes.  The speaker that typically gives a single beep at the beginning of a boot cycle, typically built onto the motherboard.

I am aware of the "modprobe -r pcspkr" method for killing the speaker, but that is treating a symptom.  I'd rather know why its happening and remove the cause.

Besides, why should rebooting fix it?  Shouldn't one boot be identical to the next?

---

### Post by TheStroj on 2009-09-18
> **01000111 said:**
> Yes.  The speaker that typically gives a single beep at the beginning of a boot cycle, typically built onto the motherboard.

I am aware of the "modprobe -r pcspkr" method for killing the speaker, but that is treating a symptom.  I'd rather know why its happening and remove the cause.

Besides, why should rebooting fix it?  Shouldn't one boot be identical to the next?
Don't know why it happens, but I wanted to recommend using that command, but you already know about it xD.

---

### Post by 01000111 on 2009-09-18
> **TheStroj said:**
> Don't know why it happens, but I wanted to recommend using that command, but you already know about it xD.

Thanks.  I appreciate the suggestion.  My concern is that there is something wrong somewhere that needs actual fixing.

---

### Post by TheStroj on 2009-09-18
> **01000111 said:**
> Thanks.  I appreciate the suggestion.  My concern is that there is something wrong somewhere that needs actual fixing.
No problem =).
But if you open the files you attached you can see that the message keeps showing ```
ACPI: PCI Interrupt Link
``` all the time, which probably means that the cause of the beep was your new PCI device.

---

### Post by 01000111 on 2009-09-18
> **TheStroj said:**
> No problem =).
But if you open the files you attached you can see that the message keeps showing ```
ACPI: PCI Interrupt Link
``` all the time, which probably means that the cause of the beep was your new PCI device.

Ok, but what do I do about it?  The "PCI Interrupt Link" items appear in the non-beeping boot log as well.

---

### Post by TheStroj on 2009-09-18
> **01000111 said:**
> Ok, but what do I do about it?  The "PCI Interrupt Link" items appear in the non-beeping boot log as well.
Don't know the answer, I just noticed it while looking through the files you posted. 
Just wait for some real Ubuntu geek to show up and he will probably know what do.

---

### Post by 01000111 on 2009-09-22
> **01000111 said:**
> Greetings all,
I recently upgraded my video card to a Nvidia GeForce 8400 GS in a PCI-E 16x slot.  I'm very happy with the results both on the VGA and DVI ports.  Everything is working beautifully, except...

Since the upgrade, every now and then when I boot, the PC speaker starts beeping very rapidly.  By the time the gui is displayed, the beeping has become a single, steady, endless tone.

The cure so far has to reboot, and the problem is solved, but I'd rather have an actual solution.

I'm running Xubuntu Jaunty on a dual-core AMD64 X2 5000 with 2GB ram.

Attached are a DMESG dump from when the beeping was happening, and another about 60 seconds later when it wasn't.  No changes between the two, other than rebooting.

Thanks in advance for the assistance.

G

bump!

---

