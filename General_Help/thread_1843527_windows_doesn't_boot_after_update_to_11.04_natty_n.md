---
title: "windows doesn't boot after update to 11.04 natty narwhal"
date: 2011-09-13
forum: General Help
---

### Post by karma coma on 2011-09-13
I had this phenomen after updating ubuntu 9.10 to 10.10 and finally 11.04 on a dual boot system.

After that, the windows option in the dual boot menue was no longer there.

After messing around with grub (tried different things which ended that also ubuntu didnt boot), i finally repaired the mbr and grub with a live cd and boot-repair.

Now both options (ubuntu 11.04 and windows xp) are availible in the boot menue, but the windows boot process gets stuck after choosing between "safe mode" or every other option.

I googled and read alot, most advices ended up in using the recovery console of the windows setup disk. The problem ist that this disk also stucks while telling me it is loading windows.

I can rule out following things:

cpu-problem: i think also the ubuntu live cd and the normal boot of ubuntu wouldn't work if it is broken
cd-problem: i also tried another windows cd - with the same results
usb-problem: i disconnected every usb-cable from the pc - same results

I can see the content of the windows partition in ubuntu, it is "still there".
Besides the same problem occurred when updating 9.10 to 11.04 on my laptop.

Is there a solution to repair my windows system or get the setup disk to boot?

**Edit:** I finally got windows setup disk to boot! I disabled usb- and lan-controllers in bios. Now the disk boots and i can solve the other issues.

---

