---
title: "64 bit applications"
date: 2011-03-30
forum: General Help
---

### Post by mainak_sen on 2011-03-30
I am running Lucid x64 in a multi-boot system (with Win XP Pro 32 and 64 bit, and Lucid 32bit as well).

Now my question is that when I am booted into my Lucid 64 system (which is my default) and am downloading software/packages from Synaptic or Ubuntu Software Center, am I, by default, getting the 64-bit version of those software/packages? For individual software/package/application how would I know if it is 32-bit or 64-bit?

Kindly let me know.

Thanks!!

---

### Post by tgm4883 on 2011-03-30
> **mainak_sen said:**
> I am running Lucid x64 in a multi-boot system (with Win XP Pro 32 and 64 bit, and Lucid 32bit as well).

Now my question is that when I am booted into my Lucid 64 system (which is my default) and am downloading software/packages from Synaptic or Ubuntu Software Center, am I, by default, getting the 64-bit version of those software/packages? For individual software/package/application how would I know if it is 32-bit or 64-bit?

Kindly let me know.

Thanks!!

You are getting the 64-bit version if the program is arch dependent. Various programs can run on 32-bit or 64-bit hardware with the same binary.

---

### Post by mainak_sen on 2011-03-31
Thanks for your quick response!

Need two clarifications, however:

1. What is "arch dependent"? Is "arch" short for "architecture"? How would I be able to tell if a program is or is not "arch dependent"?

2. In general, is there a way of finding out if the binary/package is for 32-bit or 64-bit?

I know little bit about computers but am not a geek by any stretch of imagination...so please pardon my ignorance if my questions are stupid. :)

Thanks again!

---

### Post by Joeb454 on 2011-03-31
If you are installing packages from the repositories, most of them will indeed be 64 bit. The way I spot them is whether the package has 'amd64' in the name, or perhaps 'x86_64'

---

### Post by tgm4883 on 2011-03-31
> **mainak_sen said:**
> Thanks for your quick response!

Need two clarifications, however:

1. What is "arch dependent"? Is "arch" short for "architecture"? How would I be able to tell if a program is or is not "arch dependent"?

2. In general, is there a way of finding out if the binary/package is for 32-bit or 64-bit?

I know little bit about computers but am not a geek by any stretch of imagination...so please pardon my ignorance if my questions are stupid. :)

Thanks again!

If you want to tell if the binary file (not deb) is 32-bit or 64-bit, you can use the 'file' command.

Example
```
file /bin/ls
```

---

