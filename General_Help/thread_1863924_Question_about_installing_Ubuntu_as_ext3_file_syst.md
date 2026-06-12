---
title: "Question about installing Ubuntu as ext3 file system"
date: 2011-10-18
forum: General Help
---

### Post by ComradeNF on 2011-10-18
I want to run Ubuntu in a Virtual Machine as an ext3 file system for something specific which I will be doing. Right now I did an install of Ubuntu with VirtualBox but I have no idea what file system it is.

I have 2 questions:

1. How can I check what file system is currently being used?

2. If it isn't running ext3, how can I install Ubuntu as an ext3 file system through a VM?

---

### Post by ubu_dynamite on 2011-10-18
If you did a standard install off ubuntu lucid or newer you are using ext4.
You could check in "system monitor-> file systems"
To change this you will have to choose manual partitioning when installing.

---

### Post by matt_symes on 2011-10-18
Hi

> **ComradeNF said:**
> I want to run Ubuntu in a Virtual Machine as an ext3 file system for something specific which I will be doing. Right now I did an install of Ubuntu with VirtualBox but I have no idea what file system it is.

I have 2 questions:

1. How can I check what file system is currently being used?

Open a terminal and type 

```
sudo blkid -c /dev/null
```Enter your password. It will not be echoed to the screen. That will tell you various information including the file system type. This will be ext4.

> 2. If it isn't running ext3, how can I install Ubuntu as an ext3 file system through a VM?Is there not an option to select the type to format your partitions to anymore  when you install ? It has been a while since i installed and have just upgraded. I'm sure you could just select the filing system you wanted on your partitions if you select the manual partition option.

Kind regards

---

### Post by ComradeNF on 2011-10-18
> **matt_symes said:**
> Hi



Open a terminal and type 

```
sudo blkid -c /dev/null
```Enter your password. It will not be echoed to the screen. That will tell you various information including the file system type. This will be ext4.

Is there not an option to select the type to format your partitions to anymore  when you install ? It has been a while since i installed and have just upgraded. I'm sure you could just select the filing system you wanted on your partitions if you select the manual partition option.

Kind regards

Is it possible to format a VirtualBox partition? I'm not too sure I can do that. The only reason I am even installing via VirtualBox is because I need to use Windows alongside Ubuntu.

But in order to install as ext3 I would need to reinstall right?

---

### Post by 2F4U on 2011-10-18
> But in order to install as ext3 I would need to reinstall right?

Your assumption is right, there is now way to downgrade from ext4 to ext3 (at least that is what I know).

---

