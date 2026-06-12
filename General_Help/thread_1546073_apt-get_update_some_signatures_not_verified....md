---
title: "apt-get update: some signatures not verified..."
date: 2010-08-04
forum: General Help
---

### Post by icd* on 2010-08-04
when running "sudo apt-get update" at the end of downloading the list it produces the error:
"Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0"

(obviously) running lucid lynx x64, not sure what else you need to know...

cheers.

BTW: i didn't find anything searching on the forums but maybe i suck at it, i don't know O_o

---

### Post by chopinhauer on 2010-08-04
```
gpg --recv-key 5A9A06AEF9CB8DB0 && gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -
```

It is easier if you add the PPAs the way described on PPA Launchpad page.

---

