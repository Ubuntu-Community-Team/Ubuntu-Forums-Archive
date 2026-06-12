---
title: "Rebooting = Frozen bios splash screen"
date: 2010-03-22
forum: General Help
---

### Post by sr_guy on 2010-03-22
Hi All,

Running Jaunty 9.04. I have an odd situation that started up recently. If I go to CLI and run sudo reboot the PC reboots but freezes on the bios splash screen. If I shutoff the PC and turn it back on it reboots normally. What's likely to cause this? Power supply issue, Bios Power Management settings, or something else? I did reset my bios back to factory default settings by shorting the pin on the motherboard, but still having the same issues. Any ideas?

---

### Post by srs5694 on 2010-03-22
I had some problems like that on a system with a GUID Partition Table (GPT) disk, and I found that making a trivial change to the partition table (renaming one partition) fixed the problem. My hypothesis is that the BIOS was looking inside the first MBR partition it found, which in the case of a GPT disk is a "protective partition" that begins with the GPT data structures, and the BIOS therefore became confused. This is only a hypothesis, though.

So, if on the off chance you're using GPT, try making a trivial change to the partition table (alter the names of the first couple of partitions, say). If you're not using GPT, some other change to your partition table or the first sector of one or more partitions may do the trick, but I don't recommend you start making such changes randomly. Many of these details are critical for normal system operation, so changing them if you don't know what you're doing can cause the system to become completely unbootable.

---

### Post by pricetech on 2010-03-22
Try removing the battery.  I know you said you jumped the pins, but pull the battery anyway.

Does your BIOS feature any kind of logging ??  If so you should be able to find at least some information there.

You don't mention any errors, so I'm guessing you don't get any, such as angry beeps or stop codes.  Watch the screen closely in case come kind of message "flashes by".

When you power off and back on, do you wait any time or is the power off and on immediate ??

---

### Post by srs5694 on 2010-03-22
I forgot to make explicit in my earlier reply: To try changing the partition table, you've got to pull the drive and put it in another computer. In the process, you can test to see if the system with the problem can boot any other medium. If it can, then the BIOS is probably flaking out over something it's seeing on your hard disk. If not, then chances are it's a CMOS issue (which can be reset in ways such as pricetech suggests) or a hardware problem.

---

### Post by sr_guy on 2010-03-22
No beep codes unfortunately, and no errors on the screen. Now I imaged my other mythtv multimedia machine (2nd computer with higher end RAM/CPU) using remastersys, and used that same image on the machine that is having the issues. So the partition table issue could be the problem.

On the other hand, remastersys uses ubuntu's generic installation setup, so it goes through and setups up your partitions like a normal ubuntu distro cd would.

---

### Post by pricetech on 2010-03-23
I don't recommend you monkey with partitions at all.

Your symptoms sound like a hardware issue of some sort, though pinning it down will take some doing.  The fact that it only happens at reboot and not when you power cycle is kind of weird.

My brain is still working on that.

I am intrigued I must say.

Got any substitute RAM, or can you run it on one stick at a time ??

---

