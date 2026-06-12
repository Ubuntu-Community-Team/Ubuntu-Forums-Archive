---
title: "How do I encrypt swap?"
date: 2012-05-29
forum: General Help
---

### Post by ToshibaLaptoplinux on 2012-05-29
I selected encryption when installing. This encrypted my HOME folder and was pleasantly surprised to find that it also encrypted swap. However, during some re-partitioning stuff I was forced to re-format my swap, as swap.

Is there a way to re-encrypt swap without doing a clean install?

---

### Post by codemaniac on 2012-05-29
> **ToshibaLaptoplinux said:**
> I selected encryption when installing. This encrypted my HOME folder and was pleasantly surprised to find that it also encrypted swap. However, during some re-partitioning stuff I was forced to re-format my swap, as swap.

Is there a way to re-encrypt swap without doing a clean install?

Although you can configure particular applications such as vi not to write to swap space, you can not configure the kernel to do so. When memory is low, the kernel will swap the contents of the page to the swap space. The contents of this page can include such sensitive contents as your bank PIN, your passwords or GPG passphrase. This information is in cleartext which means an attacker can read the contents at their leisure. Encrypting your swap space protects its contents against unauthorized reading and various forensic attacks should your machine be removed from your possession and/or compromised.

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by ToshibaLaptoplinux on 2012-05-29
> **codemaniac said:**
> Although you can configure particular applications such as vi not to write to swap space, you can not configure the kernel to do so. When memory is low, the kernel will swap the contents of the page to the swap space. The contents of this page can include such sensitive contents as your bank PIN, your passwords or GPG passphrase. This information is in cleartext which means an attacker can read the contents at their leisure. Encrypting your swap space protects its contents against unauthorized reading and various forensic attacks should your machine be removed from your possession and/or compromised.

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

Thanks. Thus my question, how can I re-encrypt swap? The initial install did so there must be a way.

---

### Post by Dave_L on 2012-05-29
```
sudo ecryptfs-setup-swap
```

Back up these files first: /etc/crypttab, /etc/fstab

---

### Post by codemaniac on 2012-05-30
yes as suggested above ,You might need the ecryptfs-utils package.

---

### Post by ToshibaLaptoplinux on 2012-06-14
Thanks for the replies. I tried to use the command provided and this error was thrown back;

> WARNING: [/dev/dm-0] already appears to be encrypted, skipping.
WARNING: There were no usable swap devices to be encrypted.  Exiting.


Which leads me to believe swap is still encrypted. However if I look in any disk management tool (GParted, Win7 Disk Management, etc.) it still shows up as not being encrypted.

Any other suggestions?

---

### Post by HermanAB on 2012-06-14
The best way, I would say the only way, is to use 'whole disk' encryption.  Since swap is on there, it will also be encrypted when the system is at rest.

---

