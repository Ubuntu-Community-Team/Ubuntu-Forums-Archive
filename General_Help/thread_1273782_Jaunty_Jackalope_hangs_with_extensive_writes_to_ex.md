---
title: "Jaunty Jackalope hangs with extensive writes to ext4"
date: 2009-09-23
forum: General Help
---

### Post by jkounis on 2009-09-23
I recently created a 5.5TB raid array as a large backup volume and formatted it with ext4. The idea was that it would be a central place where several machines on the network could write their backups.

During writing to the ext4 volume, every so often, the process doing the writing will hang. I have seen this both on the main machine where the raid array physically exists and on nfs client machines.

When this occurs, I first notice that rsync stops working. Any other command I use to access the file system also hangs (ls, df, du, etc.). It is then impossible to kill any process that has attempted to access the hung ext4 file system. Even kill -9 has no effect.

During this time, uptime shows a load average of about 5; however, top shows almost no processes above 0.1% cpu, and the cpu actually seems rather idle.

Also, shutdown -r now is ineffective. The only way to reboot the machine is to type Alt-PrtScn and then type R-S-E-U-I-B, or "echo b > /proc/sysrq-trigger".

The problem is intermittent and usually only occurs after a terabyte or two have been copied. It seems to occur more frequently if multiple processes are simultaneously accessing the file system. 

I should mention that the server also has about 5TB worth of ext3 file systems. When the ext4 file system has hung, there is no problem continuing to access the ext3 file systems. The only reason to force a reboot is if I want to start using the ext4 file system again.

I have seen the problem on both the 2.6.28-15 kernel and the 2.6.31 kernel that I downloaded for testing purposes from kernel.ubuntu.com. (I'm on 64-bit architecture (x86_64), so I downloaded a kernel using the procedures recommended at [http://ubuntuforums.org/showpost.php?p=7382178&postcount=29]("http://ubuntuforums.org/showpost.php?p=7382178&postcount=29")

Is this a known problem, or should I file a bug report? 

Does anyone know of any workarounds?

I'm tempted to just re-format the file system as ext3 until the bugs get worked out of ext4. Maybe Karmic will bring some improvements.

---

