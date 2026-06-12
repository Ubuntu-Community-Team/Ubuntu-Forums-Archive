---
title: "APT-CACHE reuse"
date: 2011-09-17
forum: General Help
---

### Post by sptutusukanta on 2011-09-17
I've installed ubuntu in one system and installed many software using [FONT="Courier New"]apt-get[/FONT] command. I know all the downloaded packages will be found at [FONT="Courier New"]/var/cache/apt/archives[/FONT]

Now, I've installed ubuntu on another system and need to updrage all those packages once again.

If I copy the downloaded packages from the previous system to the new one at the same place, means [FONT="Courier New"]/var/cache/apt/archives[/FONT] and I run command [FONT="Courier New"]apt-get install <some package>[/FONT] then will it require to download again or it will search inside the cache & only unavailable packages will be dowloaded?

If it is not possible to do like that, then what should I have to do for not downloading again & again?

---

### Post by plucky on 2011-09-17
> If I copy the downloaded packages from the previous system to the new one at the same place, means /var/cache/apt/archives and I run command apt-get install <some package> then will it require to download again or it will search inside the cache & only unavailable packages will be downloaded?


If the correct version of the package is in the archive,it will use **it** instead of downloading it again.This is determined when it updates the package lists.

Good Luck

---

### Post by sptutusukanta on 2011-09-17
ok... thanks plucky!!
:)

---

