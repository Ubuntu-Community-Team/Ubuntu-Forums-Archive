---
title: "Stuck at grub menu, can't make any selections."
date: 2011-01-03
forum: General Help
---

### Post by MountainX on 2011-01-03
I'm running Ubuntu 10.10 64bit. After I see "Loading Operating System..." I get the grub menu listing the kernels. At this screen, the system doesn't recognize any input. I cannot move up or down the list. The enter key doesn't work, neither do 'e' or 'c'. 

It is not a keyboard problem. I tried 3 keyboards. Also, the keyboard works at the bios screens. The problem is that the grub menu screen will not accept any input.

The problem occurred when grub set environment variable recordfail.

EDIT: here's the command to unset recordfail:
```
grub-editenv /mnt/MY_UUID/boot/grub/grubenv unset recordfail
```
where /mnt/MY_UUID/ is the volume that won't boot and is mounted under the LiveCD

You can check it first with ```
grub-editenv /mnt/MY_UUID/boot/grub/grubenv list
```
if recordfail is set, the command will show:
recordfail =1
else it won't show anything

After unsetting recordfail, I was able to boot again. However, I have not solved the original problem.  Why won't the grub menu accept any input??? Any ideas?

---

### Post by oldfred on 2011-01-03
When I put a new motherboard in a couple of years ago I had this problem. i found mouse & keyboard worked if I changed to ps/2 ports but both XP & Ubuntu worked with either.

Grub actually follows BIOS setting where both windows & Ubuntu ignore it. Check your BIOS and enable USB mouse & keyboard.

---

### Post by MountainX on 2011-01-03
> **oldfred said:**
> 
Grub actually follows BIOS setting where both windows & Ubuntu ignore it.

Thank you. That's good info. I'll try that.

---

