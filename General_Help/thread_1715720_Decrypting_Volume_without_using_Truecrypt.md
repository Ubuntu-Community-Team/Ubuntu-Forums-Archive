---
title: "Decrypting Volume without using Truecrypt"
date: 2011-03-27
forum: General Help
---

### Post by phr33k-dc on 2011-03-27
Hi,

I have recently just encrypted an external HDD using TrueCrypt.
To decrypt it, one must launch Truecrypt and then enter the passphrase.
Is it possible to be prompted for the passphrase without having to launch TrueCrypt everytime, e.g when I plug my HDD into a friends computer, so he/she doesnt have to go and download and install TrueCrypt just to unencrypt it?

Thanks in advanced.

---

### Post by mendhak on 2011-03-27
Hi - part of the point of encrypting it is to prevent the scenario you're describing.  If you think about it, anyone could then pick up your volume and brute force it till it opens.  So yeah - you will need TrueCrypt on your friend's computer. 

If you're looking for something simpler, have a look at [mcrypt]("http://manpages.ubuntu.com/manpages/maverick/man1/mcrypt.1.html") or [encfs]("http://ubuntuforums.org/showthread.php?t=148600").

---

### Post by tgm4883 on 2011-03-27
> **phr33k-dc said:**
> Hi,

I have recently just encrypted an external HDD using TrueCrypt.
To decrypt it, one must launch Truecrypt and then enter the passphrase.
Is it possible to be prompted for the passphrase without having to launch TrueCrypt everytime, e.g when I plug my HDD into a friends computer, so he/she doesnt have to go and download and install TrueCrypt just to unencrypt it?

Thanks in advanced.

You could put truecrypt on an unencrypted partition of the drive. I've done that with my thumb drive.

---

### Post by phr33k-dc on 2011-03-29
Points taken, and yes it makes sense what both of you are saying.

Although a brute force attack would be quite hard with a AES-Twofish-Serpent encryption and a keyfile, and a 43 character random password?

@tgm4883: Do you mean put the actual truecrypt program on the unencrypted bit?

---

### Post by tgm4883 on 2011-03-29
> **phr33k-dc said:**
> Points taken, and yes it makes sense what both of you are saying.

Although a brute force attack would be quite hard with a AES-Twofish-Serpent encryption and a keyfile, and a 43 character random password?

@tgm4883: Do you mean put the actual truecrypt program on the unencrypted bit?

Yes, I have the binaries for Linux, Windows, and Mac on mine

---

