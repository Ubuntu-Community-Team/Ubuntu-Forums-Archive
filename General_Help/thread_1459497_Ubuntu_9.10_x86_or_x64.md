---
title: "Ubuntu 9.10 x86 or x64?"
date: 2010-04-21
forum: General Help
---

### Post by manco on 2010-04-21
I apologize in advance to the mods if I posted this in the wrong place.

I just learned today that there are 32-bit and 64-bit versions of Ubuntu.

My laptop is currently running Ubuntu 9.10 that I installed off the [Live CD]("http://2.bp.blogspot.com/_oPmvXB6su08/SwKETa1ISYI/AAAAAAAABL0/Vz1p0Kt-rb4/s400/ubuntuCD.png") Ubuntu sent me (I think it's 32-bit).

My laptop is running an Intel Core 2 Duo 2.0 GHz, which I'm about 99.99% sure can utilize the 64-bit architecture.

I'm downloading the 64-bit Ubuntu 9.10 right now; are there any problems I might run into by upgrading from 32-bit to 64-bit?

Also, after installing 64-bit Ubuntu, can I install 64-bit OS' in VirtualBox?

Thanks

EDIT: I should add that my laptop has 3GB of RAM

---

### Post by The Real Dave on 2010-04-21
I dunno about VB, but I'd advise you to use 64bit Ubuntu. I run an older machine (signature) on 64bit, and the speed difference is amazing. Your system is almost definitely compatible, and there's very little difference software side between the two :)

---

### Post by srs5694 on 2010-04-21
Depending on what you mean by "upgrade," you might run into an issue: AFAIK, it's not possible to upgrade a 32-bit installation to a 64-bit installation, in the sense of replacing the system software without changing the configuration files, user accounts, and so on. This may not be a big deal if you've got a separate /home partition, since you can just blow away the root (/) partition, re-install everything from scratch, and keep your user data (in /home). Ubuntu defaults to creating one big root (/) partition with no separate /home partition, though, which means that converting from 32-bit to 64-bit results in loss of data in /home unless you back it up first and then restore it after the fact. If you find that you're in this boat, you may want to take the re-installation as an opportunity to create a custom partitioning arrangement with a separate /home so that you won't find yourself in this situation again in the future.

---

### Post by undecim on 2010-04-21
> **manco said:**
> I'm downloading the 64-bit Ubuntu 9.10 right now; are there any problems I might run into by upgrading from 32-bit to 64-bit?
Possibly. Sometimes hardware drivers and flash have issues, but most of those kinks are worked out nowadays. The only way to know is to try. If it doesn't work, you can always go back to 32-bit
> **manco said:**
> Also, after installing 64-bit Ubuntu, can I install 64-bit OS' in VirtualBox?

You should be able to. I don't know if it requires hardware virtualization or not, but it works fine on mine. If you can't use it, check your BIOS and make sure that virtualization is enabled.

---

### Post by manco on 2010-04-21
> **The Real Dave said:**
> I dunno about VB, but I'd advise you to use 64bit Ubuntu. I run an older machine (signature) on 64bit, and the speed difference is amazing. Your system is almost definitely compatible, and there's very little difference software side between the two :)
Thanks for the info.

I think I'll try it out next week!

---

### Post by Jive Turkey on 2010-04-21
I don't have any problem running 64-bit guest os on 64-bit ubuntu host with VBox.

---

