---
title: "Dual Boot Partitions"
date: 2011-08-24
forum: General Help
---

### Post by tmaxwell8383 on 2011-08-24
Installed 11.04 today (first time Ubuntu user) and I'm having some teething problems which hopefully you fine people will be able to help me with. One of which is that when I tried to copy all of my music and films over I got a message telling me that I've only got 3gb of space left! I installed the disk usage analyser which tells me that I've actually got 517gb left, so what is going on?

I installed GParted and found that I've got 3 partitions (which I expected):

25gb recovery
550gb
100mb unallocated

So why on earth am I being told that I've only got 3gb left!?!?!

---

### Post by MG&amp;TL on 2011-08-24
Not really a fix, but you could try doing it anyway, and seeing if it still says that you only have 3gb left. You can always remove them later.

Alternatively, you could be copying them to the wrong drive. I did this recently, was trying to format a floppy, clicked the wrong icon and BANG! goes my USB. With files on. Oops. ;)

What does the 'recovery' partition do? I don't have one of these, and with respect, if you're a first-time user, you won't have set it up manually. 25GB! Check what it does.

Edit: and which bit's 'SWAP'? I'm assuming this a 'pure' ubuntu install, without any dual-boots or anything like that?

---

### Post by tmaxwell8383 on 2011-08-24
Turns out that I am an actual idiot.

New question:

When you first install the OS you are presented with a slider which allocates different amounts of memory to each OS. I didn't allocated enough. So is there an easy way to edit the amount of memory dedicated to Ubuntu without having to create or edit partitions? Can I get back to the point in the installation where it offers me the chance to edit the allocations?

---

### Post by MG&amp;TL on 2011-08-24
Nope, it's OK, we've all been here, done that.

One way to do it, as Windows does not play nicely with other OSs changing it's parition size, is to boot to windows, and use disk utility as explained here:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")

to shrink the windows partition, and grow the Ubuntu one. Be CAREFUL, though, as it's all too easy to delete something, and you don't know about it until next restart. And backup important files. And have a recovery/install windows cd ready. Or the easier way would be to choose 'something else' from live cd, then manually partition and reinstall, as descried here:

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide]("http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide")

Hope this helps. And please be careful. Booting to 'grub rescue>' is not a pleasant experience. And I would definitely choose the second option. ;)

---

### Post by tmaxwell8383 on 2011-08-24
> **MG&TL said:**
> Not really a fix, but you could try doing it anyway, and seeing if it still says that you only have 3gb left. You can always remove them later.

Alternatively, you could be copying them to the wrong drive. I did this recently, was trying to format a floppy, clicked the wrong icon and BANG! goes my USB. With files on. Oops. ;)

What does the 'recovery' partition do? I don't have one of these, and with respect, if you're a first-time user, you won't have set it up manually. 25GB! Check what it does.

Edit: and which bit's 'SWAP'? I'm assuming this a 'pure' ubuntu install, without any dual-boots or anything like that?

Definitely copied to the right place, and I've just realised that after each programme installation you get a message telling you how much memory you've got left which tells me the same thing.

It's originally a Windows 7 machine so the 25gb recovery partition is where the OS is stored in case a system recovery is needed. If things go wrong and you need to do a factory reset or something then instead of booting from a DVD you install from that partition.

I'm on a dual boot. I'm done with Windows, I've had 1 too many blue screen experiences related to Microsoft update messing with my drivers and causing untold amounts of pain and suffering. That said, I'm keeping it there for now until I get used to this. When the time comes that I have become one with Ubuntu then Win7 will be cast off to the fiery depths of hell where it belongs.

---

### Post by MG&amp;TL on 2011-08-24
Lucky whatsit. Sorry, I didn't read the thread title. My windows came with a 1GB recovery partition that " may assist in recovery should a minor error occur." Grrr....if it came with an install key for windows, is it worth thinking about running Windows inside Ubuntu for your progs and that as a VM?

---

### Post by tmaxwell8383 on 2011-08-24
Did you get a recovery DVD? I think the point of that partition which has an entire recovery utility inside is to replace the need for including recovery DVDs. It could probably be smaller because I think Win7 is only 8gb installed.

What's a VM?

To be honest I just want to get rid of Windows because I'm sick to death of it. I've also got a friend who has been trying to persuade me for a long time that Ubuntu is the future, and to be honest even though I've had it for less than a day I quite like it already.

I'll go back into Windows and see if that disk management trick works.

---

### Post by MG&amp;TL on 2011-08-24
Careful! Please. :D

Nope, S0ny's just ummm...GREAT at customer support.

If it does boot to something known as "grub rescue", my trick is to  reinstall Ubuntu over Ubuntu, or in the free space, and then it works. <shrugs>

Me too, but I gotta keep my windows. Fun to hack, I guess. A Vm is a virtual machine, made with a program like VirtualBox or VMWare. You can run a little computer inside a 'real' one.

---

### Post by tmaxwell8383 on 2011-08-24
Ok, it worked but now I'm stuck with not knowing how to tell Ubuntu to use the extra GBs I've just freed up for it. I've given the partition a drive letter but how do I tell Ubuntu to use it?......

Forget it. Fresh install. Just googled methods to uninstall Ubuntu and it all looks very complicated. If I were to boot from my USB and install again would the original installation be removed?

---

### Post by Megaptera on 2011-08-25
Just a suggestion.
It might help if you posted a screenshot of your current partition set up. That way it would make it easier to see what's where and how much there is of it ...

Cliche follows ..... A picture paints a thousand words.

---

### Post by donaldsmith on 2011-08-25
Your Windows machine is already installed and you install Linux as an operating system, and

Want to leave the Windows boot loader (NTLDR) is the MBR (Master Boot Record). This allows you to continue starting Windows without problems. I heard that Windows 2000, Windows XP, or anti-virus software may complain if the MBR contains the boot loader of Windows

---

### Post by tmaxwell8383 on 2011-08-25
I just did a fresh install and allocated the disk space properly this time. Everything is ok now.

---

### Post by Megaptera on 2011-08-26
Glad to read you solved it!!

---

