---
title: "Installing hebrew on ubuntu"
date: 2011-10-23
forum: General Help
---

### Post by seoisfree on 2011-10-23
Hi guys, i tried to follow the steps of installing hebrew on my ubuntu [https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto)

and i got this error - 
```
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/x/xfonts-efont-unicode/xfonts-efont-unicode_0.4.2-3_all.deb  Connection failed
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/x/xfonts-efont-unicode/xfonts-efont-unicode-ib_0.4.2-3_all.deb  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

So i tried to do apt-get update, and then i got - 
```
W: Failed to fetch http://source.repository.backtrack-linux.org/dists/revolution/Release.gpg  Something wicked happened resolving 'source.repository.backtrack-linux.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

So i tried applying the second tip the code said and wrote,  "--fix-missing" (with and without question mark) but the command not found

Any idea guys?

Thanls

---

### Post by oldtimer7777 on 2011-10-23
They have dropped support for some languages in Ubuntu lately. That could be what they were talking about in the last update discussion on ubuntu dev boards.

> **seoisfree said:**
> Hi guys, i tried to follow the steps of installing hebrew on my ubuntu [https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto)

and i got this error - 
```
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/x/xfonts-efont-unicode/xfonts-efont-unicode_0.4.2-3_all.deb  Connection failed
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/x/xfonts-efont-unicode/xfonts-efont-unicode-ib_0.4.2-3_all.deb  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```So i tried to do apt-get update, and then i got - 
```
W: Failed to fetch http://source.repository.backtrack-linux.org/dists/revolution/Release.gpg  Something wicked happened resolving 'source.repository.backtrack-linux.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```So i tried applying the second tip the code said and wrote,  "--fix-missing" (with and without question mark) but the command not found

Any idea guys?

Thanls

---

### Post by seoisfree on 2011-10-23
That Sucks..

Thanks Friend for the info

---

### Post by oldtimer7777 on 2011-10-23
> **seoisfree said:**
> That Sucks..

Thanks Friend for the info

Debian will continue to support Hebrew indefinitely because they are used for servers. I would try Debian Squeeze.

---

### Post by seoisfree on 2011-10-23
> **oldtimer7777 said:**
> Debian will continue to support Hebrew indefinitely because they are used for servers. I would try Debian Squeeze.

Unfortunately (or not :D) Back-Track is Ubuntu based OS

---

### Post by oldtimer7777 on 2011-10-23
> **seoisfree said:**
> Unfortunately (or not :D) Back-Track is Ubuntu based OS

That just means it is going to be Pure Debian based soon like Crunchbang.

Smell ya later

---

