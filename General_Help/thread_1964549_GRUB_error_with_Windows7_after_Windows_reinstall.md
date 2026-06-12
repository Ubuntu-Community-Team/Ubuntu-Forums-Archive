---
title: "GRUB error with Windows7 after Windows reinstall"
date: 2012-04-24
forum: General Help
---

### Post by h1078276 on 2012-04-24
I have Ubuntu/Windows 7 dualboot. I had to reinstall Windows 7, by using a recovery disc which formats the partition and reinstalls it.
After it did it work and PC restarted, GRUB can't run Windows7 when I click the same option as before.
It complains about disk and something and says "Press enter to continue".
 
When browsing the Windows partition from Ubuntu all files seem to be there.
 
Whats going on?

---

### Post by coffeecat on 2012-04-24
Welcome to the forum!

> **h1078276 said:**
> 
Whats going on?

If your Windows recovery disc reformatted the Windows partition, it would have changed the UUID of the partition. Grub searches for partitions by UUID, and if you haven't reconfigured grub, it will still be searching for the old UUID.

Just to be sure that I've understood you - you still see the grub menu and you can boot into Ubuntu? If so, boot into Ubuntu, open a terminal, and run this command:

```
sudo update-grub
```

Then reboot and see if you can boot into Windows.

---

### Post by h1078276 on 2012-04-24
> If your Windows recovery disc reformatted the Windows partition, it would have changed the UUID of the partition. Grub searches for partitions by UUID, and if you haven't reconfigured grub, it will still be searching for the old UUID.I don't know what UUID is, but I'm guessing its something like file enty blocks in archives which give info about the files in it, like offset, size and name. Do I have a decent idea?
 
> Just to be sure that I've understood you - you still see the grub menu and you can boot into Ubuntu? 
Yes, luckily, otherwise I wouldn't be able to post this.
 
> 
If so, boot into Ubuntu, open a terminal, and run this command:
 
```
sudo update-grub
```Then reboot and see if you can boot into Windows.I'll try now, thanks!
 
**EDIT:** OK, it worked! Posting this from Windows.

---

### Post by coffeecat on 2012-04-24
> **h1078276 said:**
> I don't know what UUID is

[UUID]("http://en.wikipedia.org/wiki/UUID").

UUIDs are used to uniquely identify partitions formatted with Linux filesystems. Strictly speaking the "UUID" of a NTFS partition (which is what your Windows partiiton will be) is not a UUID, but offhand I can't remember what it is meant to be called. However, it is usually loosely referred to as a UUID, and that is how it is referenced in the main grub configuration file (and in your /etc/fstab file if that is used to mount NTFS partitions).

> **h1078276 said:**
> EDIT: OK, it worked! Posting this from Windows.

Excellent!

And, a tip for posting when you need help.

> **h1078276 said:**
> 
It complains about disk and something

If you see an error message, it's always best to post the complete error if you can. The error message often tells its own story and can be needed to know what is wrong and what is needed to fix the problem. This time, I was able to deduce the likely problem, but that is not always the case.

Good luck!

---

