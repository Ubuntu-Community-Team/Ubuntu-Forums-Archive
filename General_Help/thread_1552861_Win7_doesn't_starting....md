---
title: "Win7 doesn't starting..."
date: 2010-08-14
forum: General Help
---

### Post by turbora on 2010-08-14
Hello everyone.

Last night, I formatted my laptop(Asus w5f). And I installed win7 Home Premium.
Then I installed Ubuntu 10.04.

After installation, I restarted the computer. When I choised win7 at grub, comp. restarted itself. But When I choised Ubuntu, started properly. Now, grub is not starting win7.

At ubuntu, I can see windows disk and files. But win7 doesn't start.

Do you have any idea to fix it?

---

### Post by Mark Phelps on 2010-08-14
When you installed Ubuntu, did you let the installer do it by choosing side-by-side? If so, the installer shrunk the Win7 OS partition and most probably, corrupted it in the process.

You will not be able to boot into Win7 again until you repair the boot loader.

Since you already had Win7, did you bother to use the Backup feature to create and burn a Win7 Repair CD?  Or did you just charge blindly ahead -- hoping for the best?

I'm betting the latter.  So if you want to repair Win7, you will have to go to the link below, download and burn a Win7 Repair CD, boot from that, and run Startup Repair three times.  It takes three passes to make all the needed repairs:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

And next time, you would do better coming to the forums and asking about what to do, instead of just charging ahead ...

---

### Post by elliotn on 2010-08-14
Fix win7 bootloader then restore grub

---

