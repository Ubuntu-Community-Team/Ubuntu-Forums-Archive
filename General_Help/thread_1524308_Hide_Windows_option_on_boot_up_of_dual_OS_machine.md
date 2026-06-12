---
title: "Hide Windows option on boot up of dual O/S machine"
date: 2010-07-05
forum: General Help
---

### Post by keevill on 2010-07-05
I want to set up a dual Win/Ubuntu machine and I know that Windows goes on first and then Ubuntu second.
Grub produces the boot menu choice with the default os being Ubuntu.
What I want to do is to hide the Windows option from the user so that they are 'encouraged' to use Ubuntu.
However, if absolutely necessary then can ask me to boot into Windows.
How can I achieve that?
-keevill-

---

### Post by stderr on 2010-07-05
The boot options are specified in /boot/grub/menu.lst and can be edited with this command:

```
gksudo gedit /boot/grub/menu.lst
```

If you scroll to the very bottom you should see the Windows entry. You should be able to comment the lines out (there should be about 5 lines for it). Or you could change the title... you might be able to remove the title characters so the line just reads "title     " so it's a semi-invisible menu entry. Just be a little careful messing around with menu.lst - my advice is to a) take a backup of menu.lst, and b) burn a Live CD and keep it handy, just in case you really screw up menu.lst and can't boot.

edit: Actually, it might work well to change either the X or Y value in the "root (hdX,Y)" line. That way, it will fail to boot, but it's elementary to select the menu entry in the boot menu, hit e to edit, and change the number back to the correct one to boot it.

---

### Post by keevill on 2010-07-05
> **stderr said:**
> The boot options are specified in /boot/grub/menu.lst and can be edited with this command:

```
gksudo gedit /boot/grub/menu.lst
```

If you scroll to the very bottom you should see the Windows entry. You should be able to comment the lines out (there should be about 5 lines for it). Or you could change the title... you might be able to remove the title characters so the line just reads "title     " so it's a semi-invisible menu entry. Just be a little careful messing around with menu.lst - my advice is to a) take a backup of menu.lst, and b) burn a Live CD and keep it handy, just in case you really screw up menu.lst and can't boot.

edit: Actually, it might work well to change either the X or Y value in the "root (hdX,Y)" line. That way, it will fail to boot, but it's elementary to select the menu entry in the boot menu, hit e to edit, and change the number back to the correct one to boot it.

Fell at the first hurdle !
When gedit opens the menu.lst it is empty - no entries at all
-keevill-

---

### Post by mikewhatever on 2010-07-05
Hiding a grub menu entry is not possible, at least afaik, but you can hide the whole menu instead. To do that, edit **/etc/default/grub**. Here is an example of what the first three lines should look like:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=3
GRUB_HIDDEN_TIMEOUT_QUIET=true

```

_GRUB_DEFAULT=0_ - determines the default boot entry, usually the newest available kernel.
_GRUB_HIDDEN_TIMEOUT=3_ - timeout during which you can hit the Shift key to display the boot menu.
_GRUB_HIDDEN_TIMEOUT_QUIET=true_ - no counter during time out.

When done editing, run **sudo update-grub**

Edit: /boot/grub/menu.lst is from grub1, which has been deprecated since Ubuntu 9.10. Both Karmic and Lucid use grub2, which doesn't have the above mentioned file.

---

### Post by keevill on 2010-07-05
> **mikewhatever said:**
> Hiding a grub menu entry is not possible, at least afaik, but you can hide the whole menu instead. To do that, edit /etc/default/grub. Here is an example of what the first three lines should look like:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=3
GRUB_HIDDEN_TIMEOUT_QUIET=true

```

_GRUB_DEFAULT=0_ - determines the default boot entry, usually the newest available kernel.
_GRUB_HIDDEN_TIMEOUT=3_ - timeout during which you can hit the Shift key to display the boot menu.
_GRUB_HIDDEN_TIMEOUT_QUIET=true_ - no counter during time out.

Edit: /boot/grub/menu.lst is from grub1, which has been deprecated since Ubuntu 9.10. Both Karmic and Lucid use grub2, which doesn't have the above mentioned file.

I've found the entries in grub.cfg.
Can I safely go ahead and edit this file ?
Lots of warnings that it is not for editing unlike menu.lst
-keevill-

---

### Post by mikewhatever on 2010-07-05
> **keevill said:**
> I've found the entries in grub.cfg.
Can I safely go ahead and edit this file ?
Lots of warnings that it is not for editing unlike menu.lst
-keevill-

Excuse me? Who said anything about editing grub.cfg? As the warning tells you, you should not edit the file.

I forgot to mention that after editing **/etc/default/grub**, you have to update grub with **sudo update-grub** command. Added that above as well.

---

### Post by keevill on 2010-07-05
> **mikewhatever said:**
> Excuse me? Who said anything about editing grub.cfg? As the warning tells you, you should not edit the file.

I forgot to mention that after editing **/etc/default/grub**, you have to update grub with **sudo update-grub** command. Added that above as well.

Apologies, I was moving on with the first reply from stder which mentioned the menu.lst file.
I have opened the grub file in gedit as you say and can see the first three lines as described.
Do I comment them out or ??
Thx,
-keevill-

---

### Post by mikewhatever on 2010-07-05
No, don't comment them out, just make sure they look like in the example I posted.

---

