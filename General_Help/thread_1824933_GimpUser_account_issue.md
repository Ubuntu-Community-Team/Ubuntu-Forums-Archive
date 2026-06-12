---
title: "Gimp/User account issue"
date: 2011-08-14
forum: General Help
---

### Post by bravo sierra echo on 2011-08-14
Kubuntu Natty Narwhal, modern hardware, bit of a Frankenbox.

Two user accounts on this machine.  I've had it for a while, and I've recently added an account for my girlfriend to use.

No problems to report on my account.

On my girlfriend's account, The GIMP flatly refuses to run.  The cursor bounces with the logo, then it just disappears - no excuses, no error messages, no nothing.

It works perfectly well under my account.

As far as I can see, everything else works perfectly well under my girlfriend's account.

Any ideas?

---

### Post by ofnuts on 2011-08-14
> **bravo sierra echo said:**
> Kubuntu Natty Narwhal, modern hardware, bit of a Frankenbox.

Two user accounts on this machine.  I've had it for a while, and I've recently added an account for my girlfriend to use.

No problems to report on my account.

On my girlfriend's account, The GIMP flatly refuses to run.  The cursor bounces with the logo, then it just disappears - no excuses, no error messages, no nothing.

It works perfectly well under my account.

As far as I can see, everything else works perfectly well under my girlfriend's account.

Any ideas?Start gimp from a terminal using --verbose:
```
gimp --verbose
```What version of Gimp are you running? Have you installed any plugins?

---

### Post by AlphaLexman on 2011-08-14
Quickfix, login as girlfriend, and ...
```
cp -r /home/boyfriend_username/.gimp-2.6 /home/girlfriend_username
```

---

### Post by bravo sierra echo on 2011-08-14
Gimp 2.6, as supplied with Kubuntu.  I've never used it, Girlfriend just wants to use it to add watermarks to photos that she puts on her blog.

Thanks AlphaLexman, that worked.  It gives an error message on startup saying that she doesn't have permission to the folder /girlfriend/.gimp-2.6 but it all seems to work OK.  I imagine she won't be able to save preferences or install plugins but that's unlikely to be an issue.

Thanks very much!

---

### Post by ofnuts on 2011-08-14
> **bravo sierra echo said:**
> Gimp 2.6, as supplied with Kubuntu.  I've never used it, Girlfriend just wants to use it to add watermarks to photos that she puts on her blog.

Thanks AlphaLexman, that worked.  It gives an error message on startup saying that she doesn't have permission to the folder /girlfriend/.gimp-2.6 but it all seems to work OK.  I imagine she won't be able to save preferences or install plugins but that's unlikely to be an issue.

Thanks very much!Make sure she has write access to her gimp profile. Plenty of things saved there.

---

### Post by WyleECoyote on 2011-08-14
> **bravo sierra echo said:**
> Gimp 2.6, as supplied with Kubuntu.  I've never used it, Girlfriend just wants to use it to add watermarks to photos that she puts on her blog.

Thanks AlphaLexman, that worked.  It gives an error message on startup saying that she doesn't have permission to the folder /girlfriend/.gimp-2.6 but it all seems to work OK.  I imagine she won't be able to save preferences or install plugins but that's unlikely to be an issue.

Thanks very much!

just change ownership with with this

$ chown -R girlfriend:girlfriend /girlfriend/.gimp-2.6

---

### Post by AlphaLexman on 2011-08-14
> **bravo sierra echo said:**
> It gives an error message on startup saying that she doesn't have permission to the folder /girlfriend/.gimp-2.6
We can fix that with your help! Post the output of...
```
ls -ld /home/girlfriend/.gimp-2.6
```
**EDIT:** Beaten

---

### Post by AlphaLexman on 2011-08-14
> **WyleECoyote said:**
> chown -R girlfriend:girlfriend /girlfriend/.gimp-2.6
Actually should be...
```
chown -R girlfriend:girlfriend [COLOR="Red"]/home[/COLOR]/girlfriend/.gimp-2.6
```
probably just a typo/oversight, if you still have trouble we would like to see the permissions from my code.

Good Luck!

---

### Post by WyleECoyote on 2011-08-14
hehe thanks AlphaLexman I just copy/pasted his path above :)

---

