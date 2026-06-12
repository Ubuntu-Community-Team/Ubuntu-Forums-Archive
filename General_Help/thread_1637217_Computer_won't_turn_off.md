---
title: "Computer won't turn off"
date: 2010-12-04
forum: General Help
---

### Post by ocwo92 on 2010-12-04
I've installed Ubuntu 10.04 LTS on a Via EN12000EG. Everything works fine, except the computer doesn't turn off as desired. Instead, it ends at the final "System halted" message and stays on.

When I press the power button, the screen blanks for a few seconds then returns to normal.

According to biosdecode: "ACPI 1.0 present".

I've passed "acpi=force" as a grub boot option, but this doesn't seem to help.

There's no /proc/acpi directory.

What should I do to make the computer recognize the power button press and shut down completely?

---

### Post by TeoBigusGeekus on 2010-12-04
Any messages from
```
sudo shutdown -h now
```
?

---

### Post by ocwo92 on 2010-12-04
> **TeoBigusGeekus said:**
> Any messages from
```
sudo shutdown -h now
```
?

Well, nothing that indicates a problem. "shutdown -h now" performs the entire shutdown sequence (disabling services, unmounting drives, etc.) until the computer stops at the final "System halted" message. In the old days, this was the message that indicated that it was now safe to manually power off the computer.

---

### Post by TeoBigusGeekus on 2010-12-04
It should be ok to press the power button now and see if it shuts down.
Strange problem though...

---

### Post by ocwo92 on 2010-12-04
> **TeoBigusGeekus said:**
> It should be ok to press the power button now and see if it shuts down.
Strange problem though...
I know it's safe to turn off the computer after the "System halted" message.

The problem is that the computer is for an embedded system where there won't be access to the power button. It's necessary to make the computer perform a proper shutdown on its own without requiring someone to press the power button.

The computer doesn't even seem to detect the power button event.

---

### Post by ocwo92 on 2010-12-04
Problem solved: it turned out the BIOS had been corrupted.

---

