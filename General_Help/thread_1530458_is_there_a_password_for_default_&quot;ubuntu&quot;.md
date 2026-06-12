---
title: "is there a password for default &quot;ubuntu&quot; user?"
date: 2010-07-13
forum: General Help
---

### Post by Chromisdesigns on 2010-07-13
And, if so, how do I find out what it is?

In trying to fix my SSH issues, I've been switching back and forth between the default user "ubuntu" and another user I created with the same attributes.  I can switch from "ubuntu" to the new user just fine.  However, I am unable to log back in as "ubuntu", because although there is apparently a password, I have no idea what it might be.

The install does not allow you to select a password for the "ubuntu" user, and of course, to change the password, you need to know the old one first.

When I try to log back in as "ubuntu" from another user account, I get the password screen and then the display goes black.  I assume that's what you get when you are not logged in at all?

In any case, to get back to "ubuntu" again, I have to reboot.

This is probably answered already somewhere, but searching didn't find it.

Regards,

Bob

---

### Post by sisco311 on 2010-07-13
It's blank, just hit Enter.

---

### Post by potat on 2010-07-13
what happens if you just hit Enter (i.e. the password is the empty string)?

---

### Post by endotherm on 2010-07-13
I'm a bit confused. at install, you are prompted to create a user and set a password for them. beyond that, and root, there are not default users, certainly none named 'Ubuntu', unless you are running off a live CD, in which case password is blank. 

what is the output of:
```
cat /etc/passwd | cut -d: -f1
```

(btw, /etc/passwd does NOT contain passwords, just user account info. )

---

### Post by Jan Dahl on 2010-07-13
> **Chromisdesigns said:**
> And, if so, how do I find out what it is?
 I am unable to log back in as "ubuntu", because although there is apparently a password, I have no idea what it might be.

When I try to log back in as "ubuntu" from another user account, I get the password screen and then the display goes black.  I assume that's what you get when you are not logged in at all?
I've experienced similar behaviour; I created a passwordless user, and after the first login, it was disabled. I couldn't even unlock from the screen saver. I had to log in using an administrative account and re-enable the account in Administration.
> **Chromisdesigns said:**
> 
In any case, to get back to "ubuntu" again, I have to reboot.


If you're in as that user, try firing up a terminal and typing
```
sudo passwd
```

If that doesn't help and the other account you have is administrative, you can just change it via System -> Administation -> Users or in a terminal, 
```
sudo passwd ubuntu
```

HTH :)

---

### Post by Chromisdesigns on 2010-07-13
Replying to all above:

I installed on a memory stick using the Pendrive installer (persistent install).  It definitely DID NOT prompt for a starting user name, and it DOES create a user called "ubuntu" with admin priv's.

I did this twice, because I thought also maybe I had missed it the first time.  Nope.  Only password requested during setup is for keyring to use wireless connection.  BTW, tried that one as the "ubuntu" user password, and it's not.

After install it boots right into Ubuntu, user = "ubuntu".  After any reboot, the same thing happens.

As for password being blank, that's not it, either.  When I try to change the "ubuntu" user password, it won't accept empty string as old password.

If I try to log in as "ubuntu", and just hit return for password, screen goes black and I have to reboot to get back in.

However, here is an interesting thing:  I have VNC running, and can connect just fine from a remote VNC client on my LAN, using ONLY the VNC password I created when I set up VNC.  It works fine logged in as the "ubuntu" user.  I assume VNC just takes over the machine and doesn't worry about user authorisaton unless you try to change users?

Regards,

Bob

---

### Post by Chromisdesigns on 2010-07-13
> **endotherm said:**
> I'm a bit confused. at install, you are prompted to create a user and set a password for them. beyond that, and root, there are not default users, certainly none named 'Ubuntu', unless you are running off a live CD, in which case password is blank. 

what is the output of:
```
cat /etc/passwd | cut -d: -f1
```(btw, /etc/passwd does NOT contain passwords, just user account info. )

Nope, didn't prompt, did create "ubuntu" all on it's own.  Password is not blank, either.

/etc/passwd contains a bunch of accounts, among them "ubuntu" and the other admin user I created.  Looks normal.

---

### Post by Chromisdesigns on 2010-07-13
> **potat said:**
> what happens if you just hit Enter (i.e. the password is the empty string)?

refuses the logon.  Password is not empty.

---

### Post by endotherm on 2010-07-13
ok, it soulds like the pendrive install is persistent but shares the default config of a live CD,

in that case, definitely try this to set a password on the account and activate the account:
```
sudo passwd ubuntu
```

hopefully that will do it

---

### Post by sisco311 on 2010-07-13
> **Chromisdesigns said:**
> Nope, didn't prompt, did create "ubuntu" all on it's own.  Password is not blank, either.

/etc/passwd contains a bunch of accounts, among them "ubuntu" and the other admin user I created.  Looks normal.

Oh, yep, if memory serves, in Lucid, the password is locked and users in the admin group (ubuntu is in the admin group) are allowed to use sudo and policykit without a password.

Try to set up a password as root:
```
sudo passwd ubuntu
```

---

### Post by CharlesA on 2010-07-13
You are booting a persistent livecd then?

---

### Post by Chromisdesigns on 2010-07-13
> **Jan Dahl said:**
> I've experienced similar behaviour; I created a passwordless user, and after the first login, it was disabled. I couldn't even unlock from the screen saver. I had to log in using an administrative account and re-enable the account in Administration.


If you're in as that user, try firing up a terminal and typing
```
sudo passwd
```If that doesn't help and the other account you have is administrative, you can just change it via System -> Administation -> Users or in a terminal, 
```
sudo passwd ubuntu
```HTH :)


Thanks, that worked just fine. Apparently, that install creates the user "ubuntu" and sets both it's password and the UNIX password to something internal, other than blank.

sudo passwd and sudo passwd ubuntu both change the UNIX password on this install.

Thanks, again.

Bob

---

### Post by sisco311 on 2010-07-13
> **Chromisdesigns said:**
> Thanks, that worked just fine. Apparently, that install creates the user "ubuntu" and sets both it's password and the UNIX password to something internal, other than blank.

sudo passwd and sudo passwd ubuntu both change the UNIX password on this install.

Thanks, again.

Bob

Please note that *sudo passwd* sets the root password, while *sudo password ubuntu* changes ubuntu's password.

[uhelp]community/RootSudo[/uhelp]

---

### Post by Chromisdesigns on 2010-07-13
> **sisco311 said:**
> Please note that *sudo passwd* sets the root password, while *sudo password ubuntu* changes ubuntu's password.

[uhelp]community/RootSudo[/uhelp]


I dunno -- either one of them responds with "Enter new UNIX password"...

Sounds like they are one and the same.  I did both just for grins, but I think in this case, they are the same thing.

---

### Post by Chromisdesigns on 2010-07-13
> **CharlesA said:**
> You are booting a persistent livecd then?

No, a persistent install on a memory stick.  The idea, once I get SSH running, is to leave Linux booted on my regular PC when I go away on a trip, with a secure entry using VNC over SSH for one userid so I can remote in and do stuff I wouldn't do on a public pc, using a client on my wife's iPad.

We are trying to avoid dragging her laptop along on trips, now that she has the iPad.

Unfortunately, as you may know, Apple crippled some of the built-in features in the iPad, like file system access and dowloads, for example.  I need to download financial data, and there are no apps that will do it, as yet.  So figured I'd set up a basic Linux install and boot my machine with it before we leave.

Still having problems getting SSH to work, though.  That's another thread I already started.

Bob

---

### Post by sisco311 on 2010-07-13
> **Chromisdesigns said:**
> I dunno -- either one of them responds with "Enter new UNIX password"...

Sounds like they are one and the same.  I did both just for grins, but I think in this case, they are the same thing.

Nope, passwd changes the password for a user account. If it's invoked without a username then it changes the passwd of the user who runs the command. 

sudo allows you to execute a command as another user or (by default) root.

So once again, if run *sudo passwd* you change root user password.

Until you learn the differences between root, *admin* and non-privileged users, I would strongly suggest you to lock the root account password:
```
sudo usermod -p '!' root
```

---

### Post by Chromisdesigns on 2010-07-13
> **sisco311 said:**
> Nope, passwd changes the password for a user account. If it's invoked without a username then it changes the passwd of the user who runs the command. 
 
sudo allows you to execute a command as another user or (by default) root.
 
So once again, if run *sudo passwd* you change root user password.
 
Until you learn the differences between root, *admin* and non-privileged users, I would strongly suggest you to lock the root account password:
```
sudo usermod -p '!' root
```
 
Sorry, you are right, of course.  Blame it on a brain fart by an old guy.  I did some Unix a bunch of years ago in school, but it WAS a bunch of years ago.  Just got confused by the "Unix password" verbiage.

Things are set correctly now.

Regards,

Bob

---

