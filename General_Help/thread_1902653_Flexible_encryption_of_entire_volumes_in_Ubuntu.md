---
title: "Flexible encryption of entire volumes in Ubuntu"
date: 2011-12-31
forum: General Help
---

### Post by S. Cornelissen on 2011-12-31
Dear all,

I have a laptop (Ubuntu 11.10) with sensitive personal and business data on two partitions on the same hard drive. Therefore I would like to encrypt my data. The ideal system would look like this:

[LIST=1]
[*]My entire hard drive is encrypted (e.g. I do not want to be forced to choose to put certain folders in the encrypted part and others not)
[*]Upon successful login (of a certain user) the volumes on the drive are auto-mounted decrypted (e.g. the login password of that user is identical to the decryption key)
[*]I do not suffer too much performance loss
[*]The encryption of the drive can take place with the data on it (e.g. no formatting during encryption)
[/LIST]

I am not sure whether this is at all possible. Suggestions for systems that come close are also welcome.

I have looked into using TrueCrypt, but have not found an auto-mounting procedure on login (point 2). Also it seems to require formatting of the drive (point 4).

Thanks in advance for any tips!

---

### Post by Paqman on 2011-12-31
You can set Ubuntu up with full-disk encryption that unlocks at boot, but you need to specify this at install time.

---

### Post by 2F4U on 2011-12-31
You have basically two options:
1. Only the home folder is encrypted. That option can be selected during installation from the liveCD. Upon login when you enter your password, the home folder will be mounted and decrypted. Almost transparent for the user.
2. Complete encryption of the hard disk, except the /boot partition. Less transparent since you have to enter the pass phrase during the system start. This option is only available through the alternate CD.

---

### Post by S. Cornelissen on 2012-01-02
Hi Pacman and 2F4U, thanks for the tips. Pacmans solution and 2F4U's second solution sounds like the full encryption I am looking for. I understand I should specify this at Ubuntu install.

Three additional questions:
[LIST=1]
[*]What is the "alternate CD"?
[*]Can I achieve this by simply re-installing Ubuntu on my existing system, or will the process require formatting the hard drive and starting with a completely fresh drive/install?
[*]In what step of the installation can I choose these encryption options?
[/LIST]

Thanks a lot!

---

