---
title: "error message when trying to download sofwares"
date: 2011-01-13
forum: General Help
---

### Post by g777 on 2011-01-13
:)i get this error message when trying to download softwares from softwares center....please help me!!!
[B]
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
[/B]

---

### Post by 3Miro on 2011-01-13
Go to System -> Admin -> Synaptic Package Manager and try to manually install ttf-mscorefonts-installer. See if this works.

---

### Post by g777 on 2011-01-13
pls some1 help me!!!

---

### Post by Quackers on 2011-01-13
Did you see post #2, by 3Miro? You seem to have posted together - almost :-)

---

### Post by g777 on 2011-01-13
i cant open synaptic  manager....i get thz error!!1

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

---

### Post by 3Miro on 2011-01-13
Close the Software Center and Update Manager. If this doesn't work, try in the terminal:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by g777 on 2011-01-13
> **Quackers said:**
> Did you see post #2, by 3Miro? You seem to have posted together - almost :-)

yeh,i can't open synaptic manager!!!!

---

### Post by g777 on 2011-01-13
when i enter a command in terminal,i get this error message!

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by sikander3786 on 2011-01-13
> **g777 said:**
> when i enter a command in terminal,i get this error message!

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Please close any package managers e.g, Software Center, Synaptic or Update Manager and run and post the output of these commands. If you get an error even after closing them, log out and back in and try these.

Applications > Accessories > Terminal:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by matt_symes on 2011-01-13
Hi

Reboot your PC and try again. If that does not work the lock can be deleted manually.

You need to try to install the fonts.

BTW: Calm down a bit ;) I sure this can be fixed. :)

Kind regards

---

### Post by g777 on 2011-01-13
> **3Miro said:**
> Close the Software Center and Update Manager. If this doesn't work, try in the terminal:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

npt working dude!!!

---

### Post by g777 on 2011-01-13
thanks everyone,i got it solved...

what i did was,i gave a restart for the pc and then ran this command in terminal. sudo dpkg --configure -a
then i got into synaptic manager which i couldnt access last time/and updated this""ttf-mscorefonts-installer"".now,it works fine......

---

### Post by Quackers on 2011-01-13
Nice one :-)
A restart has solved the odd problem for me too, but on occasions it can also cause them  :-)  depending on the circumstances.

---

