---
title: "Wipe a Partition Clean"
date: 2009-08-03
forum: General Help
---

### Post by nmaster on 2009-08-03
I want to clear a partition so that its data is completely unrecoverable.  Like DBAN but only for a single partition; I want to leave the recovery drive so that I can return the laptop to factory setting before I sell it.  

What is the best way to do this?  
I've seen this thread: [http://ubuntuforums.org/showthread.php?t=496856](http://ubuntuforums.org/showthread.php?t=496856)

Any comments or suggestions?

---

### Post by nmaster on 2009-08-03
and what if I did want to clear the entire drive?  is it possible to do this using a live usb? i figure it should work just as well as LiveCD, but just checking...

---

### Post by merlinus on 2009-08-03
Formatting, whether a partition or entire hdd, will still leave data that can be recovered.

Use dban or killdisk.

---

### Post by nmaster on 2009-08-03
> **merlinus said:**
> Formatting, whether a partition or entire hdd, will still leave data that can be recovered.

Use dban or killdisk.

yeah i think i'll just use dban and then trust the recovery discs to return the laptop to factory condition.  if anyone else has a comment, i'd be happy to hear it.

---

### Post by ajgreeny on 2009-08-03
Is your data really that needful of such intense security?  If it is just fairly ordinary personal data you can copy data to the partition several times with dd, if I remember correctly.  This will overwrite all the data on that partition, and without really clever forensic recovery tools such as used by security organisations it should be pretty well gone.  Just formatting is a complete waste of time for security purposes.
```
dd if=/dev/zero of=/dev/sdx
```Just make sure the of=/dev/sdx is correct, or you're in serious trouble.

Anyone else care to comment on dd that purpose.

---

### Post by rbc on 2009-08-03
> dd if=/dev/zero of=/dev/sdx

Just make sure the of=/dev/sdx is correct, or you're in serious trouble.

Anyone else care to comment on dd that purpose.

It does indeed work. I use that frequently. To clarify though, for anyone unfamiliar, it needs to be prefaced with sudo, and that particular command will zero out the whole drive, not just a partition. Additionally, to make sure the whole drive is zeros:
xxd -a /dev/sdx
I cannot remember if that one needs sudo
Coincidentally, I used the partmagic LiveCD today, to wipe a drive. It uses dc3dd to zero a drive, and it included a progress bar, which the dd terminal command lacks.

---

### Post by nmaster on 2009-08-03
> **ajgreeny said:**
> Is your data really that needful of such intense security? 

Yes.  Thanks for the info about dd.  However, I think I'm going to use dban.  Thanks everyone!

---

