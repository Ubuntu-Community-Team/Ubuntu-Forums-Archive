---
title: "can't open my synaptic package manager"
date: 2010-01-09
forum: General Help
---

### Post by honeybert223 on 2010-01-09
need assistance: this appears everytime i open my synaptic


E: Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.listE: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by SecretCode on 2010-01-09
Post (using the code tags) the contents of file */etc/apt/sources.list.d/medibuntu.list*

- Also the output of ```
ls -l /etc/apt/sources.list.d/
```

---

### Post by ajgreeny on 2010-01-09
Run this command again in terminal to reset the sources.list file.  If you have done a ubuntu upgrade it will have caused the problem, but whatever, this should fix it.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

