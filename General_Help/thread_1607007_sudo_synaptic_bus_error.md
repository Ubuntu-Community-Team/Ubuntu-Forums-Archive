---
title: "sudo synaptic bus error"
date: 2010-10-27
forum: General Help
---

### Post by SagnaB on 2010-10-27
Tied starting Synaptic via GUI, but it temporarily freezes then crashes and exits.
terminal> sudo synaptic returns
bus error

What's this about? Something wrong with my comp. bus? HDD?

---

### Post by linux-hack on 2010-10-27
what exactly do you want to install ?

why not install it from the terminal ? if you have problems with synaptic try reinstalling it. 

But try a : ```
sudo apt-get -f install
```
and try agen opening synaptic

if no luck : 
```
sudo aptitude reinstall synaptic
```

---

### Post by SagnaB on 2010-10-28
```
sudo apt-get -f install
```
And
```
sudo aptitude reinstall synaptic
```
Returns
```

Reading package lists... Done
Bus errordependency tree... 0%

```

I actually get this same error when I try to install *anything* from terminal. I have no idea why this is. The last thing I installed was Cairo -Dock via synaptic

---

### Post by SagnaB on 2010-10-28
So i Googled synaptic+bus+error again and mysteriously found a result I swear wasn't there before, the third one, a link to these forums in fact ( [http://ubuntuforums.org/showthread.php?p=2070840](http://ubuntuforums.org/showthread.php?p=2070840) ).
The fourth Google result is this page amazingly.

Anyway

```

cd /var/cache/apt
sudo mkdir .bkp
sudo mv *.bin .bkp
cd .bkp
sudo rm *.bin
cd ..
sudo rmdir .bkp

```ALL FIXED!

Also: [https://launchpad.net/bugs/192567](https://launchpad.net/bugs/192567)

---

