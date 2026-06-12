---
title: "Acroread and LaTex Q's - newbie"
date: 2006-05-10
forum: General Help
---

### Post by psixpsi on 2006-05-10
Hi all!
Just installed 5.10 Breezy. I have a moderate exp. with Linux. I need TeX and Acroread, but neither Synaptic nor apt-get does not see them, which is sort of a shock :eek: to me (esp. that the online documentation lists both). Am I a complete idiot   ](*,)  ? Please help how to install the stuff.

Best,
psixpsi

PS I installed Ubuntu through the ISO image CD.

---

### Post by kabus on 2006-05-10
For TeX you'll need to install the tetex-base package, I think.
Since acroread isn't free software you'll find it in the multiverse repository, which you have to enable first. Just follow the wiki instructions :

[https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu)

---

### Post by Ced22 on 2006-05-10
I would recommend installing tetex-base and tetex-extra. The extra package provides a lot of useful LaTeX packages, if you're into LaTeX word processing.

---

### Post by psixpsi on 2006-05-10
Thanks guys! It works now. Yes, I LateX A LOT (that's my basic activity), so will go for the extras too.

Best,
psixpsi

---

### Post by harisund on 2006-05-10
Just in case you aren't already aware, you can install a package named "kile". It's an awesome latex front end. (Don't worry that it's a KDE package. Just use Synaptic to install kile and it will install all the appropriate packages. And it's not that huge either) 

You LaTeX a lot? Awesome.. are you a student/professor ? (I am a student and am really addicted to LaTeX !)

---

### Post by Alexander Kirillov on 2006-05-11
[QUOTE=psixpsi]Thanks guys! It works now. Yes, I LateX A LOT (that's my basic activity), so will go for the extras too.

Best,
psixpsi[/QUOTE]
I strongly suggest using Kile as editing environment (to make it usable, you will also need kviewshell, kate and kdvi).

---

