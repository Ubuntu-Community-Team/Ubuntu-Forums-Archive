---
title: "Creating User Account via PHP"
date: 2009-08-05
forum: General Help
---

### Post by Tralin on 2009-08-05
-Edit- Solved

Hey everyone.

Okay, so I just set up MySQL, Apache and PHP, and I have a custom script to create accounts on Ubuntu over the internet.

The set up right now let's a user choose a username and password, then PHP executes the appropriate command to create the account (The username that executes the command is "www-data" and is on the sudoers list for "useradd")

The problem is that in order to have the account activate (for some reason), I need to use "sudo passwd <accountname>" to get it to work, but if I add www-data to the sudoers list for passwd, I open up my computer to a giant security hole, so I need a way for it to either activate the account automatically, or for it to run a server side script (no idea how to do this) to have it activate it on another account name that does have access.

Thanks!
Tralin

---

### Post by marshalium on 2009-08-09
If you take a look at the useradd help:
```
useradd --help
```
You will see that it accepts a password parameter '-p' and that the argument to '-p' should be the already encrypted password. So the command will look something like this:
```
useradd test -p 12CsGd8FRcMSM
```

To encrypt the password you can use something like PHP's crypt() function.
[http://us3.php.net/manual/en/function.crypt.php](http://us3.php.net/manual/en/function.crypt.php)

On my Ubuntu system the passwords appear to be DES encrypted. So your call to the crypt() function will probably need to include a two character salt. The salt needs to be generated somehow. I'm not a cryptology expert so I won't give you advice on how to do that, but there are some examples on the PHP crypt() manual page.

I hope that helps point you in the right direction.

---

### Post by marshalium on 2009-08-09
> **Tralin said:**
> -Edit- Solved

And.......you'd already found a solution three days ago.
I'm so embarrassed :oops:

---

