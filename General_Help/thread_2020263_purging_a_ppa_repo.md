---
title: "purging a ppa repo"
date: 2012-07-08
forum: General Help
---

### Post by proggy on 2012-07-08
Could someone give me the command to purge this repo -repository ppa:adilson/experimental?
tThe update manager is giving me an error message because of it
thank you.!

---

### Post by yiannis66 on 2012-07-08
have alook at this post [http://ubuntuforums.org/showthread.php?t=1592540]("http://ubuntuforums.org/showthread.php?t=1592540")
u will find the solution

---

### Post by ubudog on 2012-07-08
To **remove** the PPA, do: 
```
sudo add-apt-repository --remove ppa:adilson/experimental
```

To **purge** the PPA, do:
```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge ppa:adilson/experimental
```

Be sure you [know the differences]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html").

Best,
ubudog

---

### Post by oldos2er on 2012-07-08
> **proggy said:**
> Could someone give me the command to purge this repo -repository ppa:adilson/experimental?
tThe update manager is giving me an error message because of it
thank you.!

```
sudo add-apt-repository -r ppa:adilson/experimental
```

---

### Post by proggy on 2012-07-08
wWhen




When i open Synaptic i stil gewt thiis error "E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/adilson-experimental-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
edit. can't open Synaptic at all and Ubuntu Software Centrer crashes.

---

### Post by oldos2er on 2012-07-08
```
sudo rm /etc/apt/sources.list.d/adilson-experimental-precise.list* && sudo apt-get update
```

---

### Post by proggy on 2012-07-08
Thank you oldos2er that did it! Thanks to all that helped!

---

