---
title: "Startup Apps: Keyring"
date: 2011-06-25
forum: General Help
---

### Post by Jeff Root on 2011-06-25
Three default entries in the list of Startup Applications are
"Certificate and Key Storage", "Secret Storage Service", and
"SSH Key Agent".  Under what conditions would I want or need
these three apps?  Can I turn them off and leave them off
without losing any functionality that I actually use?
 
   -- Jeff, in Minneapolis

---

### Post by kerry_s on 2011-06-25
anything that uses a password, wifi, mail, im, etc...

---

### Post by Jeff Root on 2011-06-26
I use passwords to get my e-mail and access some websites
such as this one, but those passwords which are stored are
in cookies.  As far as I know, I've never used the Keyring
apps at all.  And if I did ever need them, wouldn't they
be started when they are needed?  I don't understand why
they are started at boot.
 
   -- Jeff, in Minneapolis

---

### Post by doas777 on 2011-06-26
when Kerry says email, he means evolution. the keyring only holds keys for services and clients on your local PC. it does not include web remembered passwords. each browser uses its own means to do that.

anytime you ask ubuntu to rember a password, it stores it in the keyring. 

the most common passwords I've seen are for wifi connections at boot or login, and for samba (file/print sharing) shares on your local network. for instance i have passwords for shares on several of my PCs.

the keyring (seahorse) allows you to encrypt any keys you store, so that other users (even admin users) cannot get to your passwords.

---

### Post by kerry_s on 2011-06-26
just disable them, if you have problems the error will tell you whats missing, then just start that back up.

---

### Post by Jeff Root on 2011-06-26
doas, kerry,
 
Thanks.  Some part of my brain is telling me that's all
it needed to know about that.
 
   -- Jeff, in Minneapolis

---

### Post by Habitual on 2011-06-26
seen this before using auto-login to the DE.

Just a thought...

---

