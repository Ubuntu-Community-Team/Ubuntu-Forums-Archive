---
title: "I/O error on shutdown"
date: 2009-11-05
forum: General Help
---

### Post by MoscowModder on 2009-11-05
When Ubuntu shuts down, it goes smoothly until after the white logo fades away and it gives some text output, and then says:
```
Buffer I/O error on device loop0 logical block #####
```

I can't read the block number because my photo is blurry... sorry.

It's 9.10 with Wubi, and has UNR installed.

---

### Post by Giblet5 on 2009-11-05
Did you have a USB pen drive or SD card plugged in at the time?

That is the most common cause of this that I've seen. Something is trying to flush the SD card driver's buffers *after* the card was already unmounted. (ON MY SYSTEM.)

Try to capture the device name and then figure out what device that really is (SD card, / filesystem!!!, etc)

---

### Post by P4man on 2009-11-05
Can you check /var/log/messages to retrieve the exact message?

---

### Post by Giblet5 on 2009-11-05
> **P4man said:**
> Can you check /var/log/messages to retrieve the exact message?

That would work for startup messages.

Previous shutdown messages would be in /var/log/syslog.1.gz, recoverable via ```
zcat /var/log/syslog.1.gz | less
```

---

### Post by MoscowModder on 2009-11-06
> **Giblet5 said:**
> That would work for startup messages.

Previous shutdown messages would be in /var/log/syslog.1.gz, recoverable via ```
zcat /var/log/syslog.1.gz | less
```

That command gives me nothing, and I don't think I leave USB drives in.

Edit: I found that the faulty device is called loop0.  Also, last time I booted up it did a filesystem check of it, but I didn't see the result.

---

### Post by MoscowModder on 2009-11-07
Even more horror: Windows gets stuck on the Windows loading screen (or maybe it's checking the filesystem), and won't boot all the way!  Help, please?

Edit: Scratch that.  Windows is working now.

---

### Post by P4man on 2009-11-07
sounds like you got a problem with your harddrive.
Make sure SMART is enabled for your harddrive in the bios, boot the 9.10 live cd and run disk utility from system > administation


If its not a hardware problem killing your drive it could of course be a windows virus or filesystem corruption problem. That one of the reasons why wubi sucks, if windows goes down there is a good chance it takes ubuntu along as it sits on the same windows filesystem.

So also try booting windows recovery or something to test the windows filesystem (sorry no windows expert so not sure how exactly).

---

### Post by MoscowModder on 2009-11-09
Well, its a good thing I have a live USB because my netbook doesn't have an optical drive.  I'll try that, then.

---

### Post by MoscowModder on 2009-11-11
[s]Well, Windows works fine, but the original problem persists.  The device loop0 causes an error every time it tries to shut down from Wubi, but not when booted from a live USB drive.[/s]

For some reason, the problem has gone away.  How mysterious.

---

