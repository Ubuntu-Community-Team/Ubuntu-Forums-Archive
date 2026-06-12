---
title: "password free installation?"
date: 2011-05-29
forum: General Help
---

### Post by jquillian on 2011-05-29
Is there a way to configure Ubuntu so as to not require passwords?
 
Thanks
 
James

---

### Post by Markmental on 2011-05-29
yes, during installation when ubuntu asks for a password don't enter one.

---

### Post by linuxinstalledfromhdd on 2011-05-29
Mark, is that true? No passwords.. How about root?

---

### Post by 3rdalbum on 2011-05-29
> **jquillian said:**
> Is there a way to configure Ubuntu so as to not require passwords?
 
Thanks
 
James

No, not really. You could enable the root account and log in as root permanently, but this is terrible security practice and some programs won't work with you logged in as root. You'd still need to type your root password to log in as root anyway, and anything that uses Policykit (Software Center and Update Manager come to mind) would still require a password.

All major operating systems now (Linux/Unix, Mac OS X, Windows Vista/7) have security systems that require confirmation from the user before performing any administrator-only access. Really, you should just get used to typing your password whenever prompted.

It's also been pointed out that new users hit the password prompts more frequently because they're still finding what software they want to use, applying tweaks and trying different settings. When you've been using Ubuntu for a while you'll probably only get password prompts when using Update Manager and Software Center, and when logging in - and this will be rare enough.

EDIT: No, Markmental and linuxinstalledfromhdd; Ubuntu's installer doesn't let you have no password. This isn't Windows XP ;-)

---

### Post by linuxinstalledfromhdd on 2011-05-29
Awwww..  ha ha

---

### Post by jquillian on 2011-05-29
I couldn't disagree more. For some people, security is not an issue.
 
> **3rdalbum said:**
> No, not really. You could enable the root account and 
log in as root permanently, but this is terrible security practice and some programs won't work with you logged in as root. You'd still need to type your root password to log in as root anyway, and anything that uses Policykit (Software Center and Update Manager come to mind) would still require a password.
 
All major operating systems now (Linux/Unix, Mac OS X, Windows Vista/7) have security systems that require confirmation from the user before performing any administrator-only access. Really, you should just get used to typing your password whenever prompted.
 
It's also been pointed out that new users hit the password prompts more frequently because they're still finding what software they want to use, applying tweaks and trying different settings. When you've been using Ubuntu for a while you'll probably only get password prompts when using Update Manager and Software Center, and when logging in - and this will be rare enough.
 
EDIT: No, Markmental and linuxinstalledfromhdd; Ubuntu's installer doesn't let you have no password. This isn't Windows XP ;-)

---

### Post by linuxinstalledfromhdd on 2011-05-29
A long long long time ago I built a linux system with no root passwords and no user passwords.  I blocked all the ports I didn't want.  Except for outgoing.  It didn't last very long.  But it was kinda fun. Kinda not. ;)

---

### Post by egalvan on 2011-05-29
> **jquillian said:**
> I couldn't disagree more. **For some people, security is not an issue**.

This is OK, as long as the machine is ONLY booted in a sterile environment, which is not connected IN ANY WAY to ANY OTHER MACHINE.

Once you connect IN ANY WAY to another machine, then security is not just your concern. It affects others.

---

