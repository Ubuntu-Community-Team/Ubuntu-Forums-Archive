---
title: "Sporadic GRUB issues: &quot;Error : Out of Disk&quot;"
date: 2010-06-21
forum: General Help
---

### Post by powerpleb on 2010-06-21
I just replaced the HD in my computer with a larger one (1tb) and installed Ubuntu Lucid 64bit onto two partitions (100gb for / and the rest for /home).

I rebooted and it loaded up fine. Did some stuff, had to restart (NVidia drivers) and it stopped at a GRUB rescue prompt, reporting the error "Error : Out of Disk".

So I rebooted again and it worked no problem.
But since then, every second bootup or so delivers this error, while other times it loads Ubuntu fine.

I've tried running update-grub a few times and this always seems to work. But ultimately, the problem never goes away.

I also had a look at this:[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

But it seems the advice given to change the 10_linux file must be only for an earlier version of GRUB2 as the file on my machine is very different.

:confused:

EDIT: I've attached the output of a Boot Info Script that I got here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by oldfred on 2010-06-21
If you manually edit out the recordfail line in your boot stanza does it boot?

It looks like they moved the logic from 10_linux to 00_header, but it is supposed to be resolved, so it still may be something else.

---

### Post by powerpleb on 2010-06-21
> **oldfred said:**
> If you manually edit out the recordfail line in your boot stanza does it boot?

It looks like they moved the logic from 10_linux to 00_header, but it is supposed to be resolved, so it still may be something else.

OK, tried your advice and edited the line out of 00_header but starting up still produced the error. 

Something else I've noticed: It only seems to occur when booting from complete shut down, when CTRL+ALT+DEL are pressed from grub prompt, computer reboots and loads Ubuntu without error.

I'm going to try a BIOS update.

---

### Post by oldfred on 2010-06-21
I think I have seen the reboot vs cold start issue several times. Only speculation but they have sped up the boot so much that maybe the hard drive has not fully spun up before grub tries to read it.

---

### Post by powerpleb on 2010-06-21
> **oldfred said:**
> I think I have seen the reboot vs cold start issue several times. Only speculation but they have sped up the boot so much that maybe the hard drive has not fully spun up before grub tries to read it.

BIOS update didn't change anything. 
I'm going to be changing to a SATA SSD which I ordered a few days ago anyway. If you are right, I suppose that shouldn't suffer from the problem.

---

