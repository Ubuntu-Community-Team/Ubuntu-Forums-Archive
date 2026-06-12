---
title: "Ubuntu laggy and strange log messages..."
date: 2010-07-23
forum: General Help
---

### Post by cpury on 2010-07-23
Hi everyone!

Recently my Ubuntu becomes a bit laggy after running for a while. i.e. it stops every other second for maybe half a second. Today I looked into the syslog to see that it's getting spammed with strange messages, they seem to be the cause of the lag:

```
Jul 23 21:10:32 Ingeborg kernel: [42278.560101] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:32 Ingeborg kernel: [42278.560186] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:32 Ingeborg kernel: [42279.060052] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:32 Ingeborg kernel: [42279.060064] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:32 Ingeborg kernel: [42279.060091] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:32 Ingeborg kernel: [42279.060179] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:33 Ingeborg kernel: [42279.562550] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:33 Ingeborg kernel: [42279.562564] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:33 Ingeborg kernel: [42279.562591] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node ffff8800b7e3e400), AE_TIME
Jul 23 21:10:33 Ingeborg kernel: [42280.060053] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:33 Ingeborg kernel: [42280.060066] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:33 Ingeborg kernel: [42280.060091] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:33 Ingeborg kernel: [42280.060179] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:34 Ingeborg kernel: [42280.560083] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:34 Ingeborg kernel: [42280.560097] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:34 Ingeborg kernel: [42280.560121] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:34 Ingeborg kernel: [42280.560209] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:34 Ingeborg kernel: [42281.512562] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:34 Ingeborg kernel: [42281.512575] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:34 Ingeborg kernel: [42281.512599] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node ffff8800b7e3e400), AE_TIME
Jul 23 21:10:36 Ingeborg kernel: [42283.050048] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:36 Ingeborg kernel: [42283.050062] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:36 Ingeborg kernel: [42283.050092] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:36 Ingeborg kernel: [42283.050178] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:37 Ingeborg kernel: [42283.552566] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:37 Ingeborg kernel: [42283.552578] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:37 Ingeborg kernel: [42283.552605] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node ffff8800b7e3e400), AE_TIME
Jul 23 21:10:37 Ingeborg kernel: [42284.050043] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:37 Ingeborg kernel: [42284.050056] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:37 Ingeborg kernel: [42284.050081] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:37 Ingeborg kernel: [42284.050167] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:38 Ingeborg kernel: [42284.550048] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:38 Ingeborg kernel: [42284.550061] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:38 Ingeborg kernel: [42284.550085] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:38 Ingeborg kernel: [42284.550168] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:38 Ingeborg kernel: [42285.052570] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:38 Ingeborg kernel: [42285.052583] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:38 Ingeborg kernel: [42285.052608] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:38 Ingeborg kernel: [42285.052694] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
Jul 23 21:10:39 Ingeborg kernel: [42285.552562] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:39 Ingeborg kernel: [42285.552574] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:39 Ingeborg kernel: [42285.552601] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node ffff8800b7e3e400), AE_TIME
Jul 23 21:10:39 Ingeborg kernel: [42286.050047] ACPI: EC: input buffer is not empty, aborting transaction
Jul 23 21:10:39 Ingeborg kernel: [42286.050059] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Jul 23 21:10:39 Ingeborg kernel: [42286.050083] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node ffff8800b7e3d9c0), AE_TIME
Jul 23 21:10:39 Ingeborg kernel: [42286.050165] ACPI Exception: AE_TIME, Evaluating _BST (20090903/battery-393)
```

You can imagine how long the logfile is with this happening every second :)

I'm relatively new to Ubuntu so if you need any further info, please tell me (and how to obtain it). I run Ubuntu 10.04 (64 Bit).

Thanks!

---

### Post by Altay_H on 2010-10-04
I'm having the same issue, except I'm only getting one message each second:
```

Oct  4 17:56:16 acer-laptop kernel: [757490.489074] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Oct  4 17:56:16 acer-laptop kernel: [757490.489098] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Oct  4 17:56:18 acer-laptop kernel: [757492.489085] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Oct  4 17:56:18 acer-laptop kernel: [757492.489111] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Oct  4 17:56:20 acer-laptop kernel: [757494.489055] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Oct  4 17:56:20 acer-laptop kernel: [757494.489080] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME
Oct  4 17:56:22 acer-laptop kernel: [757496.489076] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
Oct  4 17:56:22 acer-laptop kernel: [757496.489099] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f70178d0), AE_TIME

```

Any ideas? [This thread]("http://ubuntuforums.org/showthread.php?t=1257067") looked like the same problem, but it says it was fixed in Karmic Koala (9.10).

---

### Post by Stephen Morgan on 2010-10-09
I've had this same problem, also running 64 bit on an Acer laptop, having only just updated from Intrepid. 

Upon restarting the computer it failed to boot, couldn't even get into the BIOS setup. It would only boot up again after being disconnected from the mains and removing the battery. Seems to be fine now, even with the battery back in.

---

### Post by Altay_H on 2010-10-09
> **Stephen Morgan said:**
> Upon restarting the computer it failed to boot, couldn't even get into the BIOS setup. It would only boot up again after being disconnected from the mains and removing the battery. Seems to be fine now, even with the battery back in.
This happens to me consistently on my Acer Aspire 5735Z. I just remove the battery every time I reboot as a workaround.

The logging problem went away for me after a kernel update and reboot.

---

### Post by maykelmoya on 2010-11-02
Please see bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578506](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578506)

---

