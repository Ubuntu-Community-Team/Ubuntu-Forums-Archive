---
title: "turning off computer not from the main power button"
date: 2009-10-07
forum: General Help
---

### Post by invitingdopeman on 2009-10-07
someone has proally posted sumthing like this but i was just wondering if there is anything i can doo to turn my system completely off so i dont have to push the main power button like is there and thing i can do to shut it down wile my pc is on thanks so very much invitingdopeman

---

### Post by roger_1960 on 2009-10-07
Hi

Click on the square red icon at top right and then on "shut down".........Is this what you mean?

---

### Post by razorboy5 on 2009-10-07
yes i didn't completely understand either

as far as i understand it u just press the "Shutdown" button under the top right corner

Sometimes when i press this button it goes to a black screen for a while before completely shutting down. So dont worry if it doesn't shutdown instantly

---

### Post by yknivag on 2009-10-07
Not sure I understand the question, the shutdown is (as others have posted) on the top right corner of the screen.

However, if you're meaning shutting down a machine remotely or shutting down a headless server, then the command is:

```
sudo shutdown -h now
```

---

### Post by Carl Hamlin on 2009-10-07
> **invitingdopeman said:**
> someone has proally posted sumthing like this but i was just wondering if there is anything i can doo to turn my system completely off so i dont have to push the main power button like is there and thing i can do to shut it down wile my pc is on thanks so very much invitingdopeman

Heya.

So far as I'm aware, the shutdown feature in Ubuntu relies on the motherboard supporting ACPI. This is a relatively safe assumption today, but certainly wasn't even five years ago, so if you're trying to run Ubuntu on older hardware, that might be your problem.

---

### Post by LowSky on 2009-10-07
> **Carl Hamlin said:**
> Heya.

So far as I'm aware, the shutdown feature in Ubuntu relies on the motherboard supporting ACPI. This is a relatively safe assumption today, but certainly wasn't even five years ago, so if you're trying to run Ubuntu on older hardware, that might be your problem.

My guess is the Same as Carl's. if the Shutdown icon dowes not completely shutdown your machine, it because your hardware does not support that feature or its turned off (some older PCs had the option under BIOS to enable or disable)

---

### Post by invitingdopeman on 2009-10-07
thanks so much yea i have an older pc i new about the shutdown from the drop down menu in the right of the screen when ever i do that it logs out everythang then it says system halted sorry i should have been more specific is there anyway i can shut it down all the way thanks so much i love this **** INVITINGDOPEMAN

---

### Post by yknivag on 2009-10-07
If the machine doesn't shutdown at that point then, apart from upgrading your motherboard, it won't be possible.

---

