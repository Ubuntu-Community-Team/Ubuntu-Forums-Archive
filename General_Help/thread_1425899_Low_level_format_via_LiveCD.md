---
title: "Low level format via LiveCD"
date: 2010-03-09
forum: General Help
---

### Post by Saidear on 2010-03-09
I have an old office PC that I need to shred the drive on. Problem is, I have no monitor for it. I do have the 9.10 LiveCD however. 

Can anyone walk me through how to do a format without actually seeing it? And to have it shutdown after?

---

### Post by ibuclaw on 2010-03-09
Find a LiveCD with an ssh server enabled, and ensure the workstation is connected to a hub/switch/router when it boots, then you can connect to it remotely via ssh. :)

---

### Post by Saidear on 2010-03-09
Unfortunatly, the machine in question is a standalone tower with no NIC, it was our onsite secruity camera controller. My area manager has decided to give it away as we upgraded to a better system. But he has requested the hard drive be shredded to avoid any potential privacy concerns.

---

### Post by ibuclaw on 2010-03-09
> **Saidear said:**
> Unfortunatly, the machine in question is a standalone tower with no NIC, it was our onsite secruity camera controller. My area manager has decided to give it away as we upgraded to a better system. But he has requested the hard drive be shredded to avoid any potential privacy concerns.

Do you intend to use the Hard Drive again (after the disk shred)?

---

### Post by pricetech on 2010-03-09
Physical destruction is the best way, but if you want the drive to stay intact you're best to use something like dban to overwrite it.

If your working "blind", just wait until the ODD stops spinning and type "autonuke" to overwrite the drive to DOD standards.

By the way, that's not a low level format.

---

### Post by ibuclaw on 2010-03-09
> **pricetech said:**
> Physical destruction is the best way.

For physical destruction, unscrewing the lid of the hard drive is the best way.

Once that air tight seal is broken, renders the disk practically unusable.

---

### Post by efflandt on 2010-03-09
Don't you have another computer you could plug the drive into temporarily as a slave drive.

Then just **dd if=/dev/zero of=/dev/sdb** or whatever it is.  Make absolutely certain that you are doing that to the correct drive.

Or the following is a modified version of an example from **man dd** if you want to be able to check its status occasionally:

```
Sending a USR1 signal to a running `dd' process makes it print I/O statistics to standard error and then resume copying.

              $ dd if=/dev/zero of=/dev/sdb& pid=$!
              $ kill -USR1 $pid; sleep 1; kill $pid

              18335302+0 records in 18335302+0 records out 9387674624 bytes (9.4 GB) copied, 34.6279 seconds, 271 MB/s
```

---

### Post by dcstar on 2010-03-09
> **Saidear said:**
> Unfortunatly, the machine in question is a standalone tower with no NIC, it was our onsite secruity camera controller. My area manager has decided to give it away as we upgraded to a better system. But he has requested the hard drive be shredded to avoid any potential privacy concerns.

Then spend 10 minutes to find a spare monitor for it so you can erase the drive properly.

It is unbelievable that you want to muck around trying to do it without a monitor, is the thing located on the moon?

---

### Post by Saidear on 2010-03-11
> **pricetech said:**
> Physical destruction is the best way, but if you want the drive to stay intact you're best to use something like dban to overwrite it.

If your working "blind", just wait until the ODD stops spinning and type "autonuke" to overwrite the drive to DOD standards.

By the way, that's not a low level format.
Sounds like a plan.  The computer, sans the camera hook-ups, is to be given away to one of our employee's kids as something to browse the internet on at home.  Otherwise, I would take the drive and physically destroy it. In this case, he has asked I merely make the drive's data "difficult/impossible to recover".   I've understood that to be a low level format but if my terminology is off, I'm sorry.  I'll give the autonuke a command when I go in tomorrow.

> Then spend 10 minutes to find a spare monitor for it so you can erase the drive properly.

It is unbelievable that you want to muck around trying to do it without a monitor, is the thing located on the moon?
The tower is left in a locked office and cannot leave the premises until my area manager is assured that any data on it is sufficiently destroyed.  There is only 1 monitor onsite right now, and it is securely attached to our KVM switch running our internal computer and POS system (which are also securely attached).  If it was a simple as that, I would. And I don't really want to snag my old CRT monitor, carry it into work via bus, and then carry it home. I do have my laptop which I take with me but since I don't think that will work as a monitor I am kind of hooped.  Besides, learning to do it once makes it easy to do it again.

---

### Post by pricetech on 2010-03-11
> **ibuclaw said:**
> For physical destruction, unscrewing the lid of the hard drive is the best way.

Once that air tight seal is broken, renders the disk practically unusable.

Not true.  Rust takes time to accumulate, though it would certainly help.  My son came in handy when he was a kid for destroying old hard drives.  He and his best friend both enjoyed beating things to death with a sledge hammer.

---

