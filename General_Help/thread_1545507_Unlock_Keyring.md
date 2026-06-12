---
title: "Unlock Keyring"
date: 2010-08-04
forum: General Help
---

### Post by polardude1983 on 2010-08-04
So whenever i start my pc I get a Unlock Keyring. An app wants the keyring

Why am I having to enter this in everytime? and How do i find out what app is asking for it?

---

### Post by chopinhauer on 2010-08-04
> **polardude1983 said:**
> 
Why am I having to enter this in everytime? and How do i find out what app is asking for it?


Your keyring is encrypted using your login password as the encryption key. Since the Ubuntu system doesn't know your password (but is able to verify that it is correct cf. hash functions) you have to enter it every time to decrypt your keyring.

As to who is asking for access to the keyring, my money would be on Ubuntu One or Gwibber. Or Evolution if you start it with the session.

---

### Post by mcduck on 2010-08-04
You only need to give the keyring password to unlock the keyring in two cases: Either you have different keyring password and login password, or you are using automatic login.

In the first case you should just set both passwords to the same. That way the keyring will be unlocked automatically when you log in, without asking you for the keyring password.

In the second case you'd probably want to just set the keyring password to empty one, that wold store your passwords and encryption keys in unencrypted format but would never ask you for the keyring password again. Less security, but that's not likely to be a problem to anybody using automatic login anyway... 

To change/remove the keyring password go to Applications/Accessories/Passwords and Encryption Keys. Right-click the "Passwords:login" -keyring and select "Change Password".

---

### Post by al108 on 2010-08-07
Thanks mcduck! Applications/Accessories is a wrong place for a keyring password manager, and you have to right click... I would never figure it out :), of course it wasn't a problem till I signed up with UbuntuOne

---

### Post by bilkay on 2010-08-08
> **mcduck said:**
> You only need to give the keyring password to unlock the keyring in two cases: Either you have different keyring password and login password, or you are using automatic login.

In the first case you should just set both passwords to the same. That way the keyring will be unlocked automatically when you log in, without asking you for the keyring password.

In the second case you'd probably want to just set the keyring password to empty one, that wold store your passwords and encryption keys in unencrypted format but would never ask you for the keyring password again. Less security, but that's not likely to be a problem to anybody using automatic login anyway... 

To change/remove the keyring password go to Applications/Accessories/Passwords and Encryption Keys. Right-click the "Passwords:login" -keyring and select "Change Password".

I'm having a problem with a non-admin user. To connect to the router, it needs the router's password, then it prompts for a "Default" keyring password. Whether I set it to the login password or the router password, it still prompts for it on every login. The only way I found to stop it was to enter an empty password. I tried deleting the "Default" password, then logging out and back in, but the problem persists.

One thing I noticed different between my (admin) login and the non-admin login is what's in Applications->Accessories->Passwords and Encryption Keys. Mine shows one login password with a bunch of others (including the router) as sub-entries. The non-admin user (if I enter a "Default" password) shows the login Password and Default password as separate entities.

---

### Post by chopinhauer on 2010-08-08
> **bilkay said:**
> 
One thing I noticed different between my (admin) login and the non-admin login is what's in Applications->Accessories->Passwords and Encryption Keys. Mine shows one login password with a bunch of others (including the router) as sub-entries. The non-admin user (if I enter a "Default" password) shows the login Password and Default password as separate entities.

These are not “passwords”, but rather the “Keyring for passwords 'login'” and the “Keyring for passwords 'default'”. I think the interface uses a misleading choice of words.

The 'login' Keyring is normally unlocked whenever the user logs in (unless the login is automatic), the other not. However if you click on “Details” whenever the system asks to unlock the 'default' keyring, you can tell him to always unlock it together with the 'login' keyring.

---

### Post by bilkay on 2010-08-09
> **chopinhauer said:**
> These are not “passwords”, but rather the “Keyring for passwords 'login'” and the “Keyring for passwords 'default'”. I think the interface uses a misleading choice of words.

The 'login' Keyring is normally unlocked whenever the user logs in (unless the login is automatic), the other not. However if you click on “Details” whenever the system asks to unlock the 'default' keyring, you can tell him to always unlock it together with the 'login' keyring.
Thanks!

---

### Post by ronwin on 2010-08-20
I've got a problem like this thread - that is, when I try to sign on to my secure network (router), it asks for a 'default keyring' password.

This didn't happen until I updated to the latest version of Ubuntu.

Problem is:  1. I have no idea what that password is.  I have never assigned a password to anything.  My admin password is 'password', but that doesn't work here.

How can I clear the password and reset both the admin and the default keyring passwords so that I know what they are?

Thanks for your help with a newbie . . .

---

