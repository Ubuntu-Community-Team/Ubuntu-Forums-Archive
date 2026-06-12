---
title: "xp user private files accessible in Ubuntu !"
date: 2010-03-28
forum: General Help
---

### Post by bud55 on 2010-03-28
i am dual booting xp pro sp2 with Ubuntu 9.10

the problem is that an xp user's private files are accessible in Ubuntu.

one xp user chose to keep his documents private and were not even  accessible to other xp users. But can be accessed freely from ubuntu.  This is creating a problem
any way to fix this? or some solution

Or am i supposed to post this Q in a xp user forum?

---

### Post by Directive 4 on 2010-03-28
physical access equals root access, 

if he doesn't want his files to show he should encrypt them (pgp)

of course you could always install a key logger or scan for likely keys.

but that would be evil..  .. .  ..  mahahahaha..

---

### Post by new_tolinux on 2010-03-28
I guess Ubuntu uses the number of the default Administrator group within XP to access the drive.
I noticed before that everything is accessible.

---

### Post by coffeecat on 2010-03-28
Permissions in Windows are quite different from permissions in Linux. As Directive 4 has pointed out, if there is physical access to a machine, there is **no** security. You don't even have to install Ubuntu. You can boot up an Ubuntu live CD (or most Linux live CDs) and have read-write access to the whole of a Windows C:\ partition.

> **bud55 said:**
> Or am i supposed to post this Q in a xp user forum?

Unless you found a Windows forum with members experienced in Linux, you would probably get some very uninformed and misleading comments.

---

### Post by snowpine on 2010-03-28
Create an unprivileged user without "sudo" rights. This user will not be able to mount the Windows partition and see the sensitive data.

Of course, if this user is clever, he could use a Live CD as described above.

Don't let anyone use your computer if you don't trust them, and *especially* don't give them sudo rights. :)

---

### Post by MCVenom on 2010-03-28
> **coffeecat said:**
> Permissions in Windows are quite different from permissions in Linux. As Directive 4 has pointed out, if there is physical access to a machine, there is **no** security. You don't even have to install Ubuntu. You can boot up an Ubuntu live CD (or most Linux live CDs) and have read-write access to the whole of a Windows C:\ partition.



Unless you found a Windows forum with members experienced in Linux, you would probably get some very uninformed and misleading comments.
I agree; furthermore the files ought to be encrypted then. Unless it's hidden by Linux's own rules/permissions, Linux will not 'respect them', and all privacy is lost.

Inform the user that his/her files should be encrypted to ensure optimal security/privacy [B]across operating systems.

[/B]P.S: To coffeecat, I once had the shock of going to a Win 7 support forum and finding that many of the mods/admins there were quite knowledgeable on Linux, no kidding. So you never really know :p

---

### Post by coffeecat on 2010-03-28
> **snowpine said:**
> Create an unprivileged user without "sudo" rights. This user will not be able to mount the Windows partition and see the sensitive data.

Unless you give them your password! :p

If you create an unprivileged user and they try to mount a partition listed in the Places menu, the system prompts them for the first (administrative) user's password.

---

### Post by coffeecat on 2010-03-28
> **BlackOtaku said:**
> P.S: To coffeecat, I once had the shock of going to a Win 7 support forum and finding that many of the mods/admins there were quite knowledgeable on Linux, no kidding. So you never really know :p

I'm glad to see the - ahem - delights of Windows driving experienced people our way! :wink:

Seriously, though, it's good to see experienced users of any OS broad-minded enough to try and use other OSs. I was thinking of the fanboy mentality (which infests any forum unfortunately) getting in the way of good advice.

---

### Post by bud55 on 2010-03-29
> **BlackOtaku said:**
> I agree; furthermore the files ought to be encrypted then. Unless it's hidden by Linux's own rules/permissions, Linux will not 'respect them', and all privacy is lost.

Inform the user that his/her files should be encrypted to ensure optimal security/privacy [B]across operating systems.

[/B]P.S: To coffeecat, I once had the shock of going to a Win 7 support forum and finding that many of the mods/admins there were quite knowledgeable on Linux, no kidding. So you never really know :p

Another support forum has suggested the inbuilt exnryption in windows. right click folder, properties, advanced and encryption check box.
I did that and the files are cannot be opened now from ubuntu. But they are still visible, listed. 
Looking for a solution where the private files in xp arenot even visible in ubuntu

---

### Post by HPD2 on 2010-03-29
If you don't want them visible to ubuntu then u need to use the Linux style of hiding files ".filename" otherwise because of the diffrences in the way windows hides files you will see them. Encryption is your best bet or restricting mount access of the drive.

---

### Post by QIII on 2010-03-29
Physical access is the mother of all security problems.

---

