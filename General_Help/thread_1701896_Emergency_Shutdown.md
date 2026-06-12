---
title: "Emergency Shutdown?"
date: 2011-03-07
forum: General Help
---

### Post by MisterGatorade on 2011-03-07
I use Ubuntu 10.10 (name and surname: Maverick Meerkat)
I know the key combination "ALT + SYSRQ + R E I S U B". That is an "Emergency Reboot" if a program freezes.
What's the key combo for the shutdown?

---

### Post by howefield on 2011-03-07
Ctrl+Alt+Del usually brings up a shutdown dialogue.

---

### Post by matt_symes on 2011-03-07
Hi

ALT + SYSRQ + R E I S U **O**

Kind regards

---

### Post by veggen on 2011-03-07
This looks useful.
Could someone please elaborate what ALT + SYSRQ + R E I S U O actually means?

---

### Post by matt_symes on 2011-03-07
hI

> Could someone please elaborate what ALT + SYSRQ + R E I S U O actually means?

It's a safe shutdown of the PC. Try it.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

[http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html)

Kind regards

---

### Post by mcduck on 2011-03-07
> **veggen said:**
> This looks useful.
Could someone please elaborate what ALT + SYSRQ + R E I S U O actually means?

"R" changes the keyboard to raw mode

"E" tells all running programs to stop what they are doing and close. Same as if you selected "Close" from a programs menu.

"I" interrupts whatever programs didn't close in the previous step, and closes them.

"S" syncs the discs, writing whatever data might be in the buffers into the discs.

"U" remounts hard drives in read-only mode. We just made sure that discs are synced in previous step, so we don't want to make any more changes to them.

"O" shuts down (or "B" reboots)

Remember to give the system a bit of time between each command to allow it to actually complete.

So, in short, the whole thing tells all programs to close, kills whatever programs didn't close on their own, then makes sure all data that should be written to drives really gets there, and finally restarts or shuts down the system.

---

### Post by veggen on 2011-03-09
Thanks guys. I had no clue this existed.

---

### Post by Dutch70 on 2011-03-09
> **veggen said:**
> Thanks guys. I had no clue this existed.

There is a phrase to help you remember the keys. 

Raising
Skinny 
Elephants
Is
Utterly 
Boring

or...

Reboot
System
Even
If
Utterly 
Broken :D

You can use the keys in this order as well.

---

### Post by Grenage on 2011-03-09
While I've only used this once, I assume you can use the commands in any sequence, or in isolation?

For example, to write cached data, could one simply press alt-sysrq-s?

---

### Post by matt_symes on 2011-03-09
Hi

> **Dutch70 said:**
> There is a phrase to help you remember the keys. 

Raising
Skinny 
Elephants
Is
Utterly 
Boring

or...

Reboot
System
Even
If
Utterly 
Broken :D

You can use the keys in this order as well.

Or BUSIER backwards :D

Kind regards

---

### Post by matt_symes on 2011-03-09
Hi

> **Grenage said:**
> While I've only used this once, I assume you can use the commands in any sequence, or in isolation?

Yes you can but this combination is the closest to a normal shutdown.

> For example, to write cached data, could one simply press alt-sysrq-s?

Yes you can but in normal OS operation you should not need to.

The Wikipedia link i posted above has a list of them.

Kind regards

---

### Post by Grenage on 2011-03-09
> **matt_symes said:**
> Hi



Yes you can but this combination is the closest to a normal shutdown.



Yes you can but in normal OS operation you should not need to.

The Wikipedia link i posted above has a list of them.

Kind regards

Excellent, thank you.

---

### Post by grahammechanical on 2011-03-09
The keyboard I am using has a key with a Print Screen label. I have two older keyboards where this key is called Prt Sc Sys Rq. I think I can assume that the print screen key is also the system request key even if it is not labeled that way.

Regards.

---

### Post by matt_symes on 2011-03-09
Hi

> The keyboard I am using has a key with a Print Screen label. I have two older keyboards where this key is called Prt Sc Sys Rq. I think I can assume that the print screen key is also the system request key even if it is not labeled that way.

Maybe not. Some keyboards do not have it. Your best bet is to try it as long as it's not on a production machine.

You cannot remap it using xmodmap either (as far as i am aware). It is compiled into the kernel and requires the CONFIG_MAGIC_SYSRQ (last time i checked) macro to be enabled.

You can check if it's compilied in and enabled if the command below returns one and the file exists.

```
cat /proc/sys/kernel/sysrq
```

```
matthew@matthew-laptop:~$ cat /proc/sys/kernel/sysrq 
1
matthew@matthew-laptop:~$
```

On Ubuntu it seems to be enabled by default on desktops. Will check my server and other distros at some point.

Not a good idea to have it enabled on a production machine. It can be disabled with...

```
sudo sh -c "echo 0 > /proc/sys/kernel/sysrq"
```

Obviously this (echo 0 > /proc/sys/kernel/sysrq) can be added to a configuration file at startup.

..or one can recompile the kernel.

Kind regards

---

