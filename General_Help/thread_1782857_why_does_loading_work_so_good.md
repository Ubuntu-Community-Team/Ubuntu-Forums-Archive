---
title: "why does loading work so good?"
date: 2011-06-15
forum: General Help
---

### Post by superpisto on 2011-06-15
this sounds rather like a dumb question, but I'm curious to know what makes program load so fast in Ubuntu. Is it due to some caching mechanism, maybe alike Windows ReadyBoost, or due to ext4 itself? Also, I noticed that the same program performs much better if compiled for 64 bits than 32 bits (namely, Cube 2: Sauerbraten during map load): is it related to the handling of files or it's just the 32 bit compiling that adds some overhead, being my OS 64 bit?

---

### Post by mcduck on 2011-06-15
Most programs are rather small, and make heavy use of shared libraries which are quite likely already loaded into RAM because other programs or the desktop also uses the same libraries. On Windows the use of shared libraries is harder because of the lack of version control for them, so all programs come with their own versions of libraries instead.

What comes to 64-bit applications working faster, that's just one of the benefits of 64-bit computing. Any task that requires high precision or makes heavy use of floating-point calculations benefits from the use of 64 bits, and 64-bit computing also gives you larger procesor registries.

---

### Post by inameiname on 2011-06-15
Thanks for the info, mcduck. Very concise and understandable. I was curious myself after the threader posted this.

---

### Post by Yellow Pasque on 2011-06-15
Technically, 64-bit programs are larger than 32-bit counterparts (because of the size of pointers and such), so that's more data to load from the disk.

---

### Post by 3rdalbum on 2011-06-15
> **Temüjin said:**
> Technically, 64-bit programs are larger than 32-bit counterparts (because of the size of pointers and such), so that's more data to load from the disk.

Not much bigger at all.

---

### Post by grahammechanical on 2011-06-15
The parts that go to make up a distribution such as Ubuntu are under constant development. The programmers are not employees who have no say in how the program is developed. They are part of the development team. One of the great things about open source program development is that it is not led by the desire to make more and more profit for a corporation but by a desire for a better operating system or program and that would include speed of operation as well as features and looks.

Regards.

---

