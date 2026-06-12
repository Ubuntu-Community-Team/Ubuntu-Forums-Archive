---
title: "Mount of file system failed"
date: 2010-01-28
forum: General Help
---

### Post by PaulM1985 on 2010-01-28
Hi

I have noticed another post on here that has been posted recently but since it is very basic at the moment, I didn't want to piggy back it with my issue.

On booting my computer I get the following error:

```

Mount of file system failed.
A maintenance shell will now be started CONTROL-D will terminate this shell and re-try.

[18.149638] phy0->rt2500usb_init_eeprom: Error - invalid RT chipset detected.

[18.149689] phy0->rt2x00lib_probe_dev: Error - failed to allocate device.
```

After getting this I have run fsck which prompts:

```

Super block last mount time (Thu Jan 28 18:41:35 2010,
now = Tue Jan 19 19:55:42 2010) is in the future.
```

After fsck completes I am able to restart my computer and Ubuntu runs and updates the clock in the top corner from Jan 19 to current time.

When I turn my computer off and start again, the problem above occurs.  I am assuming this problem has something to do with the internal clock going funny but I don't know how to fix it.

Any info would me really appreciated.

Paul

EDIT - I am running Ubuntu 9.10 (main OS) and Windows 7

---

### Post by perrti-y02 on 2010-01-28
This might be far too basic, but how old is the battery on the motherboard? If that has died then the system clock won't keep going until you turn it on. I might be misunderstanding the issue or how the clock works, but it can't hurt to suggest it.

---

### Post by PaulM1985 on 2010-01-28
I assume the battery is going to be as old as the computer so I guess maybe 3 years old.

Would it be likely to have gone in such as short period of time? Also, are they cheap to buy and easy to replace?

I have also noticed that the clock has been slightly out on the Windows side so this may have been the case.

Paul

---

