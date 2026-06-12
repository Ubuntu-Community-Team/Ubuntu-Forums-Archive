---
title: "apt-get fails to complete the &quot;apt-get update&quot;"
date: 2010-03-11
forum: General Help
---

### Post by dcanti on 2010-03-11
Hello guys,

 I'm  having a problem with the apt-get update, the apt-get print an error while it is reading the packages, i already try to comment all the non official repositorys in my sources.list but don't work.

Here is the problem, (is in portugueses, but is a general error easy to understand)

Lendo listas de pacotes... Erro!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_debichem_ubuntu_dists_jaunty_main_binary-amd64_Packages
E: As listas de pacotes ou os arquivos de estado não puderam ser analisados ou abertos.

reading the package list ... Error!
(already in english)
(already in english)
E: The listis of packages or the state data cannot be analysed or open

Anyone knows how to fiz it? this error start after a simple apt-get update.

---

### Post by J_Stanton on 2010-03-11
do- sudo cat /etc/apt/sources.list and post it here.

---

### Post by philinux on 2010-03-11
And

```
ls /etc/apt/sources.list.d
```

---

