---
title: "irexec, irxevent, irw, mode2 for lirc not working since upgrade to 11.10"
date: 2011-10-17
forum: General Help
---

### Post by SNIFFER_dog on 2011-10-17
Hello Ubuntu Community,

I upgraded to Ubuntu 11.10 Oneiric Ocelot yesterday and today when trying to test a script for use with lirc, I found that irexec, irxevent, irw, mode2 have stopped working.

This is the error I get in the terminal when I type one of these commands, e.g.
```
$ irxevent
irxevent: could not connect to socket
irxevent: No such file or directory

```As mentioned, I get the same error message for irexec, irw & mode2. Nothing else broken has been discovered yet.

Before the upgrade in 11.04 my usb mce receiver and Hauppauge_350 remote worked perfectly.

I'm still new to Linux and Ubuntu and this is my first experience of a major update so understand there will be things to fix after an update.

I will continue to search for a solution but in the meantime if anyone has any ideas on what might be the problem, I would be grateful for the info.


Kind regards

SNIFFY.

---

### Post by thaelim on 2011-10-17
Yup, this is definitely a bug - I found the exact same thing. I fixed it by downloading the lirc Debian package for Natty from packages.ubuntu.com and installing that instead. I'm planning to log a bug against this later today as it's clearly a regression.

---

### Post by SNIFFER_dog on 2011-10-18
Thanks thaelim for your reply.

If you have time, could you talk though the steps I should take to install it from natty as I've not seen that before. I'm also not sure how you go about reporting bugs so I must look into that too.

Regards,

SNIFFY

---

### Post by SNIFFER_dog on 2011-10-18
Ok I solved it.

In Natty I had to blacklist the module 'mceusb' which was from the kernal, this one did not work with my receiver. I could then use the module 'lirc_mceusb' from the lirc_modules_source.

It seems that in Oneiric the kernal module has been fixed for my receiver, and so removing the blacklist then allowed my receiver to work.

This also means now that when I run irexec, irw, irxevent, mode2 the system works as before the Upgrade.

This worked for me at least.

Regards

SNIFFY

---

