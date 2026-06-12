---
title: "Gpg Key problem"
date: 2006-01-29
forum: General Help
---

### Post by barisurum on 2006-01-29
[COLOR="Blue"][FONT="Georgia"]Hi all!

   I try to update repository archives but Synapto gives this error:
 W: GPG error: [-( [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [My ID]

   How do I fix this problem easily? :-k 

   [COLOR="DarkOrchid"]Thanks and Karibu!! Wellcome!! :D [/FONT][/COLOR][/COLOR]

---

### Post by o_fortuna on 2006-01-29
[QUOTE=barisurum][COLOR="Blue"][FONT="Georgia"]Hi all!

   I try to update repository archives but Synapto gives this error:
 W: GPG error: [-( [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [My ID]

   How do I fix this problem easily? :-k 

   [COLOR="DarkOrchid"]Thanks and Karibu!! Wellcome!! :D [/FONT][/COLOR][/COLOR][/QUOTE]
Try this in the terminal (Applications-->Accessories-->Terminal for Gnome, look for Konsole in KDE):
```
 wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
```
I think that may be the key you are looking for. That will add the key, which will let the packages be "verified" (the verification is to make sure synaptic is installing trusted packages, instead of potential viruses).

---

### Post by barisurum on 2006-01-29
OK! It fixed the problem. Thanks a lot for your help. \\:D/

---

