---
title: "Home directory encryption"
date: 2010-11-18
forum: General Help
---

### Post by Drenriza on 2010-11-18
Well, under the installation of Ubuntu i selected that it should encrypt my home directory. But how strong is this encryption? what kind of encryption is it?.

If a person, gets around my logon password. Under the boot process, would my home directory then be decrypted? or would the person still need the password that i made for this.

Thanks on advance,
kind regards.

---

### Post by Mark Phelps on 2010-11-18
Sorry to "burst your bubble" regarding info security, but if someone gets physical access to your PC, encryption is only going to be a temporary hinderence, not an assurance.

Given the size of USB drives these days, it would only take minutes for them to download your hard drive onto it -- and then leisurely decrypt it offline.

---

### Post by stefangr1 on 2010-11-18
> **Mark Phelps said:**
> Sorry to "burst your bubble" regarding info security, but if someone gets physical access to your PC, encryption is only going to be a temporary hinderence, not an assurance.

Given the size of USB drives these days, it would only take minutes for them to download your hard drive onto it -- and then leisurely decrypt it offline.

This is not true. I'm not sure what algorithm is used to calculate the 128 bits EAS keys used to decrypt the home directory from passwords in Ubuntu (edit: the hash algorithm used is SHA-512, but the speed of brute forcing critically depends on the number of rounds). However, with a strong password it would take many years to decrypt. If you use a really strong password, they're lucke if they're finished before the end of our solar system.

An especially good "password" is a sentence with a few additonal numbers and characters. This makes brute forcing password more or less impossible...

---

### Post by Drenriza on 2010-11-19
> **stefangr1 said:**
> This is not true. I'm not sure what algorithm is used to calculate the 128 bits EAS keys used to decrypt the home directory from passwords in Ubuntu (edit: the hash algorithm used is SHA-512, but the speed of brute forcing critically depends on the number of rounds). However, with a strong password it would take many years to decrypt. If you use a really strong password, they're lucke if they're finished before the end of our solar system.

An especially good "password" is a sentence with a few additonal numbers and characters. This makes brute forcing password more or less impossible...

But just to clerify. The only way they could get access to my home folder (encrypted) is to brute force it, if they dont know the pass?

In ubuntu you can get around the login password, but booting the pc and selecting the apprioate boot. To remove the password. Would this also remove the password use to encrypt the home folder? Or is it the encryption phrase that is in charge of that?

My own encryption phrase is 17+ characters.

---

### Post by stefangr1 on 2010-11-19
> **Drenriza said:**
> But just to clerify. The only way they could get access to my home folder (encrypted) is to brute force it, if they dont know the pass?

Yes and no. When you are logged in with the right password, your home folder is encrypted and decrypted "on the fly". Without the key, your files are really secure. The problem is that your password is also stored in /etc/password. I don't know a lot about how vulnerable this file is to brute forcing. I assume, though, that the Linux people have made sure it's secure.

> In ubuntu you can get around the login password, but booting the pc and selecting the apprioate boot. To remove the password. Would this also remove the password use to encrypt the home folder? Or is it the encryption phrase that is in charge of that?

My own encryption phrase is 17+ characters.

The SHA hashing algorithm is used to calculate the AES encryption key from your password. This calcuation process is very CPU intensive when brute forcing, that's why brute forcing only works forpasswords with at most 6 or 7 characters.

---

### Post by Drenriza on 2010-11-19
A okey.

Well the passwords are encrypted and stored in a shadow file.

```
/etc/shadow
```You can see if a password is encrypted or not by 
user:x:1000:1000:/user:/user:/path  The x means that this user password is encrypted and stored in /etc/shadow and /etc/gshadow for groups.

The number 1000 and 1000 is a generated number you get when making a user/group.
0:0 = root
1xxx:1xxx normal users/groups.

But thanks for the info guys.

---

