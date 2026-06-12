---
title: "[SOLVED] How to prevent Truecrypt from prompting for administrative privileges???"
date: 2009-07-31
forum: General Help
---

### Post by ghostparty13 on 2009-07-31
Hello all, I've recently installed the Ubuntu Netbook Remix Edition onto a Lenovo S10. All works wonderfully :D
However, I triple boot this netbook and I share my school documents and important serials and stuff through an encrypted truecrypt file.
It mounts just fine so my problem is more of a nuisance but what happens is when I go to mount the file it prompts me for the password to access the file itself which is obviously correct, but then it immediately after prompts me to enter the Ubuntu system admin password.
Is there a way to just automatically give admin privileges to this application so I only have to enter one password to access this file?
Sorry if this is a relatively easy question but I'm still somewhat of a newb when it comes to editing config files or whatever.
Thanks in advance!

---

### Post by ghostparty13 on 2009-08-01
Anyone? I'm sure this is a quick fix..

---

### Post by michy99 on 2009-08-01
You should be able to do this in the sudoers file. To learn how it works:```
man sudoers
```

---

### Post by michy99 on 2009-08-01
I decided to try this myself, so here it is. You have to edit sudoers with visudo:```
sudo visudo
```Add this line at the end of the file:```
%admin ALL=NOPASSWD: /usr/bin/truecrypt
```This will allow anyone in the admin group to run truecrypt without having to enter the administrative password. You still have to enter the truecrypt password. You can replace %admin with your username (without the %) to only give yourself this privilege. A reboot is necessary for it to take effect.

---

### Post by aysiu on 2009-08-01
I think making *mount* work without a password will be the solution, not making *truecrypt* work without a password.

The password prompt you get is from TrueCrypt trying to mount something, and mounting generally requires root privileges.

---

### Post by michy99 on 2009-08-01
> **aysiu said:**
> I think making *mount* work without a password will be the solution, not making *truecrypt* work without a password.

The password prompt you get is from TrueCrypt trying to mount something, and mounting generally requires root privileges.

Maybe so, but I can confirm that the solution I gave in the post above works, and without disabling the password for other instances of 'mount'.

---

### Post by aysiu on 2009-08-01
> **michy99 said:**
> Maybe so, but I can confirm that the solution I gave in the post above works, and without disabling the password for other instances of 'mount'.
Do you then have to launch TrueCrypt as root then?

---

### Post by michy99 on 2009-08-01
> **aysiu said:**
> Do you then have to launch TrueCrypt as root then?

Nope.

---

### Post by ghostparty13 on 2009-08-01
@michy99

I just tried out your solution with editing visudo, works perfectly!

Thanks for the help you guys rock! :cool:

---

### Post by Soul-Sing on 2009-08-02
> **aysiu said:**
> Do you then have to launch TrueCrypt as root then?

Indeed not. Only the "pass" for starting the program.

---

