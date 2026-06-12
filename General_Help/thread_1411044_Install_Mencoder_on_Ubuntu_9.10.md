---
title: "Install Mencoder on Ubuntu 9.10?"
date: 2010-02-19
forum: General Help
---

### Post by jahgamer189x on 2010-02-19
I tried to install Mecncoder on Ubuntu 9.10 using:
```
sudo apt-get install mencoder 
```
But it returned with this error which I don't understand:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  bsd-mailx: Depends: postfix but it is not going to be installed or
                      mail-transport-agent
  lsb-core: Depends: postfix but it is not going to be installed or
                     mail-transport-agent
  mencoder: Depends: mplayer-nogui but it is not going to be installed
            Depends: liblzo2-2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

How do I install Mencoder? Please help!

---

### Post by MinimalBin on 2010-02-19
Did you followed the advice and tried the* forced mode* ?

```
sudo apt-get -f install
```

---

### Post by jahgamer189x on 2010-02-19
Yes and it just installed a few updates. (Like going to the Update Manager). It didn't install mencoder.

---

