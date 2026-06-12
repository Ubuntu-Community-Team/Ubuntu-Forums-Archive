---
title: "&quot;make install&quot; command problems"
date: 2011-06-05
forum: General Help
---

### Post by pottsiex5 on 2011-06-05
Hi,
Im trying to install something but with the "make install" command i get some directory problems:

pottsie@joel-potts:/usr/local/src/hydra-6.3-src$ sudo make install
[sudo] password for pottsie: 
strip hydra pw-inspector
echo OK > /dev/null && test -x xhydra && strip xhydra || echo OK > /dev/null
cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
echo OK > /dev/null && test -x xhydra && cp xhydra  /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra  || echo OK > /dev/null
cp -f hydra.1 xhydra.1 pw-inspector.1 /usr/local/man/man1
cp: target `/usr/local/man/man1' is not a directory
make: *** [install] Error 1

is there anything i can do to fix this?
thanks

---

### Post by 3xp10r3r|X13 on 2011-06-05
did you type "make", before going for the "make install"?

---

### Post by pottsiex5 on 2011-06-05
Yup, ive done all the steps following this guide: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by matt_symes on 2011-06-05
Hi

Where did you get the source from ?

The directory /usr/local/man/ is empty (on my laptop) and the install script is not creating the directory man1.

```
matthew@matthew-laptop:~$ ls /usr/local/man/
matthew@matthew-laptop:~$ 
```The man pages are usually stored under /usr/share/man in Ubuntu so it's trying to put the manual page in a different location than usual.

You could try creating the directory

```
sudo mkdir /usr/local/man/man1
```and the ```


sudo make install
```Kind regards

---

### Post by pottsiex5 on 2011-06-05
OK, i think it worked, this time i got:

pottsie@joel-potts:~$ sudo mkdir /usr/local/man/man1

pottsie@joel-potts:~$ cd /usr/local/src/hydra-6.3-src

pottsie@joel-potts:/usr/local/src/hydra-6.3-src$ sudo make install
strip hydra pw-inspector
echo OK > /dev/null && test -x xhydra && strip xhydra || echo OK > /dev/null
cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
echo OK > /dev/null && test -x xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra || echo OK > /dev/null
cp -f hydra.1 xhydra.1 pw-inspector.1 /usr/local/man/man1

but how would i open the program now?

---

### Post by SeijiSensei on 2011-06-05
It should be /usr/local/bin/hydra, which means you should be able to run it from the command prompt by just typing "hydra".  If you want to run it from the menus, you'll need to create a custom entry.

---

### Post by matt_symes on 2011-06-05
Hi

It's not a program i have ever used but it is stored in /usr/loca/bin so..

Lets make sure of the name. In a terminal type

```
ll /usr/local/bin
```That is 2 small L's

Post the results back here.

> cp hydra pw-inspector 

This suggests it may be two files.

Kind regards

---

### Post by pottsiex5 on 2011-06-05
Thankyou for the help. Its working :)

---

