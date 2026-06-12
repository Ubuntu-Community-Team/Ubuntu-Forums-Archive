---
title: "Configure PAM to not use fingerprint reader on login"
date: 2012-06-18
forum: General Help
---

### Post by Mr.Kappa on 2012-06-18
Hi everybody! I'm trying to configure PAM in a way that it doesn't give me the fingerprint option on login, that is actually useless (and insecure) since it doesn't decrypt the home partion nor unlock the keyring.
Right now (I configured fprint) lightdm asks me first my fingerprint and I have to scan a couple of times the wrong finger before it gives me the password option. 
I have already figured out that it's impossibile (by design) to load multiple PAM modules at the same time, hence the need to timeout the fingerprint module.

Any suggestion??

---

