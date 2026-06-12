---
title: "HDD raw data viewer (disk utilities)"
date: 2010-08-02
forum: General Help
---

### Post by dohzer on 2010-08-02
Is there (free) software for Ubuntu that will allow me to view and search the raw data sectors on my hard drive?
I had to reinstall/format after my OS became corrupted, and I want to try recovering some important data (just a simple text file) if it has not been overwritten.

I've forgotten the name of this type of software. Data/file recovery? Hex editor?
I had a decent free/OS program for Windows when I was working on an embedded FAT32 SD Card project a few years ago, but I don't know where to start looking for Ubuntu.

---

### Post by dcstar on 2010-08-02
> **dohzer said:**
> Is there (free) software for Ubuntu that will allow me to view and search the raw data sectors on my hard drive?
I had to reinstall/format after my OS became corrupted, and I want to try recovering some important data (just a simple text file) if it has not been overwritten.

I've forgotten the name of this type of software. Data/file recovery? Hex editor?
I had a decent free/OS program for Windows when I was working on an embedded FAT32 SD Card project a few years ago, but I don't know where to start looking for Ubuntu.

There are many Hex viewers/editors available, use the Search function in Synaptic to find them.

Disk partitions can be examined directly by /dev/sd**x** designations.

---

### Post by dohzer on 2010-08-02
I have GNOME Hexadecimal Editor installed, but I can't seem to open "/dev/sda7" for instance.
Is there a way to do that?

---

