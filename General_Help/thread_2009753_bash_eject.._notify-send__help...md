---
title: "bash eject.. notify-send  help.."
date: 2012-06-24
forum: General Help
---

### Post by oklokl on 2012-06-24
This is a problem.  [COLOR=Red]notify-send 'usb Failure safe removal'[/COLOR]
I need success and failure.

notify-send the message problem.
Will eject normally if my HDD
I want to succeed.(succeed message) If I do not have another hard(normalcy) succeed
# A Point 

but .. If I do not have another hard ... unconditional to fail.
T^T [COLOR=Red]# B Point - notify-send 'usb Failure safe removal'[/COLOR]



udisks --detach... If the be not for Fatal error.. I want to succeed. # A Point- notify-send 'usb Success safe removal'

```
#!/bin/bash
sync
{
## umount
notify-send 'Please wait ... of doing eject'
umount -l /dev/sd[c-z][0-9]*             ## c~z all
udisks --unmount /dev/sd[c-z][0-9]*      ## c~z all To force
sync
sleep 7
} && {
udisks --detach /dev/sdc
udisks --detach /dev/sdd
udisks --detach /dev/sde
udisks --detach /dev/sdf

} && {
# A Point 

notify-send 'usb Success safe removal'
} || {

# B Point 
notify-send 'usb Failure safe removal'
}

```

---

