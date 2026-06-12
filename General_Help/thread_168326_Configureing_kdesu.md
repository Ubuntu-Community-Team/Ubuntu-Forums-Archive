---
title: "Configureing kdesu"
date: 2006-04-30
forum: General Help
---

### Post by xinix on 2006-04-30
Is it possible to configure kdesu to not ask for a password every single time it's used?  What I'd like is for it to work like sudo.  only asking for the password after a certain period of time.thanks,
-r

---

### Post by Caligula on 2006-04-30
can you not use sudo?
anyway, I thought kdesu was to launch programs? you only need it once...

---

### Post by gingermark on 2006-04-30
No, what the OP wants is once the password is entered in kdesu (such as when opening Adept) to not have to enter it again for a time if they then run another app (such as Guarddog, or indeed, any other app they need root priviledges for),

A little research has revealed that kdesu normally has a "Keep Password" checkbox. Normally using "kdesu -n" would be used to disable this, but evidently the Kubuntu developers have beaten us to it.

So, I guess it probably is possible, but I couldn't find any operator to re-enable this option.

---

### Post by xinix on 2006-04-30
Gingermark, that is exactly why I was asking about this. I like to use the command line panel applet and sudo doesn't work with it.  It seems that the kubuntu devs don't want the user to even have the choice to enable this for themselves. Or don't make it easy to find out how.  In help:/kdesu/sec-password-keeping.html (konqueror) they explain that this is to prevent hackers from getting your password if they gain access to your account.  If they gain access to your account haven't they already guessed your password?  I can see how this could be used to get your password (and admin rights) if someone is sitting at the computer that was left logged in. Are there ways of hacking into someones account without guessing their password?

It's not that that entering a password it that much more work, but when you need to run several admin apps in a brief period it would be nice to just launch them without the repetitive typing.

---

### Post by xenblend on 2006-06-08
hackers know plenty of ways to get into your computer without your password, from keyloggers to trojans.  all they need is a tiny smtp server program to mass mail everyone and their mother. :(

lj

---

