---
title: "60GB Hard Drive full even though home is 20GB"
date: 2009-07-17
forum: General Help
---

### Post by johncolescarr on 2009-07-17
Hi, 

My 60GB ubuntu partition is almost full even though my home folder is only 20GB.  I only have standard programs installed and have searched for what might be filling it up with no luck.  Any ideas?

---

### Post by hibliss on 2009-07-17
Have you checked your root trash?

---

### Post by drs305 on 2009-07-17
johncolescarr,

The three most common things that unexpectedly take away free disk space are undeleted trash, large log files, and files mistakenly copied to the system partition instead of another partition or external device (for instance a backup that was supposed to be copied onto /media/mybackupdrive, but mybackupdrive wasn't mounted at the time).

I wrote a guide that goes through the reasons free space is lost, how to find it and and how to fix it. This is the link to the wiki:
  	
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

If you have questions, you can ask them here.

Here are previews of two of the troubleshootig commands. The third one looks at your root trash folder. Refer to the guide on how to rid root trash:  ;-)
```

sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

```

---

### Post by DaithiF on 2009-07-17
Why not run Disk Space Analyzer.  Applications -> Accessories -> Disk Usage Analyser.

If you do not have this installed, then install the gnome-utils package from Synaptic.

---

### Post by dlmarti on 2009-07-17
> **DaithiF said:**
> Why not run Disk Space Analyzer.  Applications -> Accessories -> Disk Usage Analyser.

If you do not have this installed, then install the gnome-utils package from Synaptic.

Nice catch, I never used that before, just "du" with various options.  Nice tool.

---

### Post by drs305 on 2009-07-17
Since you haven't used DUA before, and since it is your system partition that is full, umount any other partitions to make the results of DUA more evident. 

If you don't, it will include the mounted partitions in the results and may also hide files on the system partition which would be hidden 'underneath' exteranl files mounted temporarily on a system folder.

---

