---
title: "Problems with passwords"
date: 2009-08-14
forum: General Help
---

### Post by tedius on 2009-08-14
I use seahorse (I'm assuming that is the name of the GNOME application that keeps track of my passwords) for a few applications including UbuntuOne.  Lately I change my Ubuntu login in password and now seahorse is popping up and asking me for my old password.

In the past seahorse was automaticly unlocked when I logged in, but since changing my login password it now asks me for it.  

Does anyone know how I can fix this so that it unlocks automaticly again?

---

### Post by P4man on 2009-08-14
as I understand it, the keyring is opened automatically if your login pw = seahorse (keyring) pw. You changed one, but not the other. Not quite how to solve that, but its probably in applications / accessoires / pw and encryption keys

---

### Post by donato roque on 2009-08-16
Go to Applications>Accessories>Password and Encrytion Keys
right click the default folder in your Password Tab and choose change password.  You should give the new password, the one you give during log in so that when you log in with your password, it also unlocks the password keyring.

Good luck.

---

### Post by tedius on 2009-08-16
Thanks guys. 

That solved my problem.  I was looking in System->Preferences so no wonder I couldn't find anything.

---

