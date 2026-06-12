---
title: "Evolution wants old, unused password"
date: 2010-05-03
forum: General Help
---

### Post by Vined Adobo on 2010-05-03
Hi all,
This morning when I opened Evolution, It asked me
for a password.  It didn't like my login pass.  It
wanted an old password I used to use.

When I click on Evolution I get
    Enter password to unlock your login keyring
    The password you use to log in to your computer 
    no longer matches that of your login keyring.

When I click on System > Preferences > Encryption 
and Keyrings, I get
    Could not launch 'Encryption and Keyrings'
    Failed to execute child process "seahorse-
    preferences" (No such file or directory)

When I click on System > Preferences > Passwords and 
Encryption Keys, I get two lines about desktop couch 
user authentication, but I can't change anything there.

I can go to System > Preferences > About me and change
my login password, but it no longer syncs to my other 
applications which require authentication.  Even when I
restore my old password for login, Evolution does not 
recognize it.

I upgraded to 10.04 on Thursday.  Everything was fine
until today.  I did a backup, but don't know what to 
restore.

Does anyone know how to handle this?

Thanks,

Dave

---

### Post by dcstar on 2010-05-03
> **Vined Adobo said:**
> 
........
When I click on System > Preferences > Encryption 
and Keyrings, I get
    Could not launch 'Encryption and Keyrings'
    Failed to execute child process "seahorse-
    preferences" (No such file or directory)
........
Does anyone know how to handle this?


Reinstall the seahorse packages and it should open up again.

Also look in Applications-Accessories-Passwords and Encryption Keys.

---

### Post by Vined Adobo on 2010-05-03
> **dcstar said:**
> Reinstall the seahorse packages and it should open up again.

Also look in Applications-Accessories-Passwords and Encryption Keys.


After reinstalling seahorse packages, I can reset my loginto my old password and Evolution will open up without asking for a password, but If I change the login password to a new one, Evolution opens and asks for the old password.  I changed my login password Thursday, but ever since Sunday morning, Evolution asks for a password.

---

### Post by Vined Adobo on 2010-05-04
> **Vined Adobo said:**
> After reinstalling seahorse packages, I can reset my loginto my old password and Evolution will open up without asking for a password, but If I change the login password to a new one, Evolution opens and asks for the old password.  I changed my login password Thursday, but ever since Sunday morning, Evolution asks for a password.


AHA!  I finally found this link: [http://gnome-evolution-general.1774414.n4.nabble.com/Evolution-and-Seahorse-Encryption-Key-Manager-td1787291.html#a1787291](http://gnome-evolution-general.1774414.n4.nabble.com/Evolution-and-Seahorse-Encryption-Key-Manager-td1787291.html#a1787291)

This is what fixed my problem:      Go to Applications > Accessories > Password 
and Encryption Keys. The first tab,  Passwords should be open.  Click on it if not. Now right-click on the **"Passwords**: Login entry."
select "change passsword" at the bottom, and make it identical to the      password you use to log into Ubuntu.

When I've changed system passwords before, evolution updated through seahorse.  For some reason some bits got twisted.  anyway, now I can use my new password and Evolution doesn't bother me for a password anymore.

Thank you all
dave

---

### Post by donloveslinux on 2010-05-23
Thanks very much!  I didn't see how to fix this in Evolution manual, but your clear explanation worked perfect.

---

