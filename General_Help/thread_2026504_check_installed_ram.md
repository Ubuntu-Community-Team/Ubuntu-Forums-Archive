---
title: "check installed ram"
date: 2012-07-15
forum: General Help
---

### Post by jackobi on 2012-07-15
Can anyone please give me advice.
I have been given a refurbished computer by my sister but she can't remember how much ram it has.It has Xubuntu installed on the whole hard drive. She thinks that it is 512mb ram.
I have Linux Xubuntu 12.04 installed on this computer. Can anyone tell me how to check my ram and also if they could advice me how much swap to allow.
I am new to Linux and grateful for any info given.
Thanks for your help

---

### Post by Laiquendi on 2012-07-15
Type in command line "free -m"
OR
if you're not accustomed with terminal, run - System monitor -> System, and there is the Hardware frame.

---

### Post by chocklet on 2012-07-15
sudo dmidecode --type memory

The output will show what is actually installed.  On my PC, top & system monitor will show different numbers, which represent the amount of memory to which the OS has access.

---

### Post by chocklet on 2012-07-15
swap - if you have 512mb RAM & plenty of storage space, probably 1 GB

[https://help.ubuntu.com/community/SwapFaq/](https://help.ubuntu.com/community/SwapFaq/)

---

