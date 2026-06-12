---
title: "encryption"
date: 2010-01-28
forum: General Help
---

### Post by phoenixfire900 on 2010-01-28
what is the easiest way to encrypt an entire linux OS as well as the file system? which program has the eaisest GUI and steps for it?  I tried TrueCrypt but it seemed too confusing.  Any help would be great thanks.

---

### Post by blueshiftoverwatch on 2010-01-28
> **phoenixfire900 said:**
> what is the easiest way to encrypt an entire linux OS as well as the file system?
You can't encrypt the entire filesystem. At the very least /boot must remain unencrypted. Although, based on an article I read I think even this method isn't completely secure because someone could tamper with the files in /boot and have it load up something to compromise your security. Some people get around this problem by putting /boot on a flash drive and carrying it around with them.
> **phoenixfire900 said:**
> 
which program has the eaisest GUI and steps for it?  I tried TrueCrypt but it seemed too confusing.  Any help would be great thanks.
Fedora and OpenSUSE allow you to encrypt directories other than /home right from the installation. Although I've only tried OpenSUSE's out once. [Here's]("http://en.opensuse.org/Encrypted_Root_File_System") an article on the subject that I read through awhile ago. Even though it's a OpenSUSE howto I'm sure most of the things there would apply to other distros as well with minimal modifications.

---

### Post by HPD2 on 2010-01-28
True crypt is about the best thing i know of.  However even with full drive encryption it is still possible to break into the system using a [cold boot attack]("http://en.wikipedia.org/wiki/Cold_boot_attack") should the attacker have access to the computer.

---

