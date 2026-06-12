---
title: "Installing Microsoft Windows inside Ubuntu"
date: 2009-10-29
forum: General Help
---

### Post by conradin on 2009-10-29
Hello, I want to take a hard drive put it in my computer and create a boot able copy of windows XP. I have the media and the licenses. The goal is then to take out the hard drive and plug it into a computer (generic, nondescript, random hard ware) and have it function.  Is there a tutorial out there for this?

---

### Post by albandy on 2009-10-29
you can't do this with windows XP.
for example, if you load a Windows Xp HD from a PIV in an AMD it will crash.
The only way it's creating hardware profiles for each machine, and this is very expensive in time and in hard disk resources.

---

### Post by Giblet5 on 2009-10-29
> **conradin said:**
> Hello, I want to take a hard drive put it in my computer and create a boot able copy of windows XP. I have the media and the licenses. The goal is then to take out the hard drive and plug it into a computer (generic, nondescript, random hard ware) and have it function.  Is there a tutorial out there for this?

That is certainly possible, but not from Ubuntu.

The way to do this is to *replace* your Ubuntu drive with the new one, boot from the Windows media, install in the usual way, do NOT activate Windows, then swap the drives again.

Now you can take the Windows drive and drop it in another PC, boot Windows, install the various drivers for that PC's hardware, and activate the copy.

Then you're ready to begin the endless task of updating. ;)


It'd be easier to just install Windows on the target PC, but you know what you're doing...

---

### Post by scottuss on 2009-10-29
You can install XP inside a Virtual Machine running on an Ubuntu machine. The other computer doesn't matter, as the XP install will always think its running on the same machine (the virtual one)

You can't install XP on a hard disk on it's own (as the main OS) and then plug it into any computer. It will most likely blue screen, and where it does work, it will likely mess around with WGA.

---

### Post by Giblet5 on 2009-10-29
> **albandy said:**
> you can't do this with windows XP.
for example, if you load a Windows Xp HD from a PIV in an AMD it will crash.
The only way it's creating hardware profiles for each machine, and this is very expensive in time and in hard disk resources.

I thought the amd.sys bug was gone in XP...

If not, forget what I said.

---

### Post by albandy on 2009-10-29
surely you're right. I migrated from Windows to Linux in 2004, so I don't know if this was patched or not.

---

### Post by Giblet5 on 2009-10-29
> **albandy said:**
> surely you're right. I migrated from Windows to Linux in 2004, so I don't know if this was patched or not.

I'll bet it depends on the install disk.

If it's a "Windows XP Pro/Home/Fapper Edition w/ SP2" disk, then I'll wager that the amd.sys bug is corrected.

I still have scars.

---

