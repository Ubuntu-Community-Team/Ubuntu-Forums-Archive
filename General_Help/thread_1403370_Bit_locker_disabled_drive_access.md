---
title: "Bit locker disabled drive access"
date: 2010-02-10
forum: General Help
---

### Post by g160689 on 2010-02-10
**one of my drive(ntfs) is used to share files in windows 7 and ubuntu. But after enabling 'bit locker' feature in that drive from W7....the drive became encrypted and cannot be accessed from ubuntu.**
**Any hacks?**

---

### Post by g160689 on 2010-02-10
**has anyone faced this problem.anyone?**

---

### Post by Grenage on 2010-02-10
Seriously a bump after 10 minutes?  You're better off with a cross-platform encryption such as Truecrypt - you won't have much luck with Bitlocker.

---

### Post by g160689 on 2010-02-10
true crypt is new to me...i'll try it.thanks.
anyone else?

---

### Post by rohit.shady08 on 2010-03-17
I have an external hard drive which I encrypted with BitLocker. Ubuntu now does not read it.

---

### Post by Grenage on 2010-03-17
Bitlocker is a Windows encryption program, it's not going to work in Ubuntu.  If you want cross-platform encryption, you're going to need a cross-platform utility like Truecrypt.

---

### Post by DrWho7of9 on 2010-03-18
Does Truecrypt use the TPM?
I want the TPM to verify / measure my BIOS before I decrypt my hard drive.

---

### Post by Grenage on 2010-03-18
It does not:

> **Some encryption programs use TPM to prevent attacks. Will TrueCrypt use it too?**

No. Those programs use TPM to protect against attacks that require the attacker to have administrator privileges or physical access to the computer (and the attacker needs you to use the computer after such an access). However, if any of these conditions is met, it is actually impossible to secure the computer (see below) and, therefore, you must stop using it (instead of relying on TPM).

If the attacker has administrator privileges, he can, for example, reset the TPM, capture the content of RAM (containing master keys) or content of files stored on mounted TrueCrypt volumes (decrypted on the fly), which can then be sent to the attacker over the Internet or saved to an unencrypted local drive (from which the attacker might be able to read it later, when he gains physical access to the computer).

If the attacker can physically access the computer hardware (and you use it after such an access), he can, for example, attach a malicious component to it (such as a hardware keystroke logger) that will capture the password, the content of RAM (containing master keys) or content of files stored on mounted TrueCrypt volumes (decrypted on the fly), which can then be sent to the attacker over the Internet or saved to an unencrypted local drive (from which the attacker might be able to read it later, when he gains physical access to the computer again).

The only thing that TPM is almost guaranteed to provide is a false sense of security (even the name itself, "Trusted Platform Module", is misleading and creates a false sense of security). As for real security, TPM is actually redundant (and implementing redundant features is usually a way to create so-called bloatware). Features like this are sometimes referred to as security theater [6].

For more information, please see the sections Physical Security and Malware in the documentation.

---

### Post by wrose51106 on 2010-03-18
As of now there is no hack to break bitlocker. Someday perhaps, best thing I can recommend is like the others, TrueCrypt.

-Bill

---

