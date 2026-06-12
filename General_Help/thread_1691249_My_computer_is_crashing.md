---
title: "My computer is crashing"
date: 2011-02-19
forum: General Help
---

### Post by TimmyK. on 2011-02-19
My laptop, running Ubuntu 10.10, keeps on crashing. For a Windows user, this would be normal, but isn't it rare for Unix-based OSs to crash? Could there have been some corruption in the disk I installed it with?

---

### Post by sikander3786 on 2011-02-19
We need some more details. When does it crash? Do you remember any specific applications running at that time e.g, flash player or a browser or mucis player? Is the crash periodic or just random?

Which hardware is there? CPU, RAM and graphics card? Did you enable compiz?

---

### Post by TimmyK. on 2011-02-19
There is no program that it usually crashes on. Sometimes it crashes while showing the desktop, sometimes when running Chess or Celestia. 

It's a Dell D620, so 2 GB DDR2 SDRAM, a dual core 1.66 GHz intel core duo processor, and a video and sound card built into the motherboard. 

One thing I have noticed though, is that it almost always crashes when it is running on battery power. Anything significant in this?

---

### Post by tudor117 on 2011-02-19
Your ram might be corrupted.
Might wanna do a memcheck

---

### Post by TimmyK. on 2011-02-19
How do I do a memcheck? Could it also be that the disk I installed Ubuntu from was corrupted?

---

### Post by tudor117 on 2011-02-19
It could be anything. Memcheck checks the ram.
It's one of the first options when you boot, in the grub. It's called **memtest86**.
If you still have the install disk, you can also check it for defects. It's one of the options when you insert it, though I doubt it would be that.

---

### Post by tgalati4 on 2011-02-19
It could be a loose battery, or dirty battery contacts.  It could also be a worn-out or defective battery.  When power drops suddenly, that can cause your computer to freeze.

Try this:

Remove the battery.  Plug in and boot.  Run the computer on a desk with adequate airflow (small fan or something) and open a terminal:

sudo apt-get install cpuburn
sudo burnP6

Let it run for 1 hour then Control-C to quit.  If it doesn't lock up for this test, then the CPU is OK.  Memtest should be run for 30 complete cycles.  This will take all night.  Memtest can be found on the LiveCD or in /boot/memtest86+.bin.  You need to run it from grub.  Your grub entry (hit escape during boot) should show "Memory Test".  Run that for 30 cycles.  If no error, then your RAM is OK.

How old is the battery?

---

### Post by sikander3786 on 2011-02-20
+1 to everything said by *tgalati4*.

> **tgalati4 said:**
>   You need to run it from grub.  Your grub entry [COLOR="Red"](hit escape during boot)[/COLOR] should show "Memory Test".  Run that for 30 cycles.  If no error, then your RAM is OK.

As the OP is running 10.10, most probably it is Grub2. In that case, you need to press and _hold_ down <Shift> key from your Bios screen until the Grub menu pops up.

---

