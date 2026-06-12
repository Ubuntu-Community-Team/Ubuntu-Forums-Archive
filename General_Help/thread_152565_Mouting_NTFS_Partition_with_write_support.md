---
title: "Mouting NTFS Partition with write support"
date: 2006-03-30
forum: General Help
---

### Post by Quantum3k on 2006-03-30
In the process of beta-testing a new program (in Windows), it got caught in a loop and wrote a load of files on my windows partition filling it, without my knowledge. On rebooting, I found that there was not enough space to boot to Windows.
I can mount my NTFS partition into Kubuntu but not with write support so i can delete the files. I've tried everything I can think of.
Any ideas?

Thanks in advance.

---

### Post by Darkriser on 2006-03-30
ntfs r/w partition mounting is supported in ubuntu, it's only an `experimental` feature - which means this shouldn't be used if you like your data [-( 

[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by Quantum3k on 2006-03-30
Well tried that... and only got -r-xr-xr-x permissions. Is there a switch or something else that I need to put in the mount command?

---

### Post by frodon on 2006-03-30
This guide will help you to get the experimental NTFS write support : [http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs+write](http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs+write)

---

### Post by Princey on 2006-03-30
[QUOTE=Quantum3k]In the process of beta-testing a new program (in Windows), it got caught in a loop and wrote a load of files on my windows partition filling it, without my knowledge. On rebooting, I found that there was not enough space to boot to Windows.
I can mount my NTFS partition into Kubuntu but not with write support so i can delete the files. I've tried everything I can think of.
Any ideas?

Thanks in advance.[/QUOTE]

Seeing write support is experimental and you're constantly warned of you risking losing your data, have you looked into the posibility of using BartPE instead? I know you can't boot into your Windows Partition right now, but if you have a friend with a CDR/W drive you can have one up and running in under an hour. BartPE allows you to build a "Live CD" of Windows XP with Full READ/WRITE permissions allowing you to do system cleanup among other things. Personally,that's what I use in my workshop to delete pesky viruses caught up in System Restore when Windows does it's best to keep virus scanners off there or some stubborn file that refuses to get deleted. I'd give it a try. Here's the link: [http://www.nu2.nu/pebuilder/download/]("http://www.nu2.nu/pebuilder/download/")

Oh, did I mention that the software is free?

---

