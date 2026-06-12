---
title: "gpg: Couldn't Connect To Host"
date: 2010-05-01
forum: General Help
---

### Post by besweeet on 2010-05-01
I'm trying to add the Mactel sources via Terminal:
```
brian@brian-lucid:~$ sudo add-apt-repository ppa:mactel-support
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 7A6BC20C4FE04DADD10837608DB7F87A2B97B7B8
gpg: requesting key 2B97B7B8 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```Any ideas?

---

### Post by P4man on 2010-05-01
I think its the keyserver thats overloaded/down. I have the same. But that doesnt mean you cant use that ppa now, you;ll just get prompted that its from an untrusted source.

---

### Post by besweeet on 2010-05-01
Really? How would I go about using it? (I ran **sudo add-apt-repository ppa:mactel-support**).

Nevermind. It magically just started to work.

---

### Post by P4man on 2010-05-01
It should be added now. Feel free to check in 

system > administration > software sources > other software

 Not sure what you want to achieve, but you can now install software from that ppa, just like you could from ubuntu, only you will be warned its not a trusted source.

---

### Post by SilverWave on 2010-05-01
> **besweeet said:**
> Really? How would I go about using it? (I ran **sudo add-apt-repository ppa:mactel-support**).

Nevermind. It magically just started to work.


Well still having issues here...

have to go old skool and down load the key?

nope obviously the "Signing key:" link must do a lookup of the key sever...
[http://keyserver.ubuntu.com:11371/pks/lookup?search=0x4E0614F88874AF754D66E9C1EBD6062C6DE6117C&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0x4E0614F88874AF754D66E9C1EBD6062C6DE6117C&op=index)

If you retry yo can get the PGP key page up and copy and paste.

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xEBD6062C6DE6117C](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xEBD6062C6DE6117C)

\o/

---

