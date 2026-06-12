---
title: "Ubuntu Maverick with 2.6.35 doesn't see my drives?"
date: 2010-10-26
forum: General Help
---

### Post by depesz on 2010-10-26
I have machine, which has 7 hard drives. 5 connected to normal controller, and 2 connected to (still on-board) marvell controller.

Till 3 days ago, it was running on jaunty (server kernel, 2.6.28-19-server).

Then I upgraded the machine to Maverick, and this is when the problem started.

When I boot from Maverick kernel (2.6.35-22-server) it doesn't see my drives attached to marvell controller.

Which is problematic, as I have /home and /usr on raid devices that are build on those drives.

I do not know why it happens, so I'd appreciate suggestion what to do/check/fix to make it work.

I did gather some evidence, though:

[LIST]
[*][Output of dmesg on 2.6.28-19]("http://depesz.com/various/blob/dmesg.on.2.6.28-19")
[*][Output of dmesg on 2.6.35-22]("http://depesz.com/various/blob/dmesg.on.2.6.35-22")
[*][Output on lshw (on 2.6.28, as I can't run it on 2.6.35)]("http://depesz.com/various/blob/lshw.output")
[*][Output of lspci -v]("http://depesz.com/various/blob/lspci-v.txt")
[*][Output of lsmod on 2.6.28]("http://depesz.com/various/blob/modules.on.2.6.28-19")
[*][Output of lsmod on 2.6.35]("http://depesz.com/various/blob/modules.on.2.6.35-22")
[/LIST]

If there is anything else that I should provide, please let me know

---

### Post by ronparent on 2010-10-26
I have just posted to another thread with a similar problem advising them to submit a bug report.

Both problems involve Marvell SATA hook up's on a MB. His hookup and his drives are SATA III. Also his drive are configured fakeraid and are fully operational in Win 7. 

I don't know how similar the situation is to yours but at least two bug reports are needed on the same problem to secure the developers attention. It would be timely if your problem was submitted now also.

---

### Post by depesz on 2010-10-26
Can you provide link to bug report?

---

### Post by ronparent on 2010-10-26
They haven't said they are filing a bug report yet. This is the link to their post: [http://ubuntuforums.org/showthread.php?t=1605770](http://ubuntuforums.org/showthread.php?t=1605770)

---

### Post by depesz on 2010-10-27
For future reference - commented in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666144](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666144) as it seems related bug.

---

### Post by ronparent on 2010-10-27
You will note a similarity in dmesg as compared to your 'Output on lshw (on 2.6.28, as I can't run it on 2.6.35)'. Both show repeated attempt and failure to address an ATA device.

---

### Post by depesz on 2010-10-27
Thanks. Well - I can't really make much out of it - I'm DB guy, not really low-level Linux guy. Hopefully someone will fix the problem.

---

