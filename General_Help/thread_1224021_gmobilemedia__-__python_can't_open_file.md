---
title: "gmobilemedia  -  python: can't open file"
date: 2009-07-26
forum: General Help
---

### Post by held7over on 2009-07-26
Running Ubuntu 9.04 32bit. 

I need to download pictures from my wife's Nokia 6085 cell phone utilizing its USB cable. It appears that gmobilemedia will do this. However, when I click on it in the menu, it does not appear to launch. 

I went to the command line to find out what is happening and got:

lucky@ispy:~$ gmobilemedia
python: can't open file '/usr/lib/python2.6/site-packages/gmobilemedia/main.py': [Errno 2] No such file or directory
lucky@ispy:~$ 

What do I need to do, to fix this?

Thanks!  :D

---

### Post by credobyte on 2009-07-26
Try:
```
sudo mkdir /usr/lib/python2.6/site-packages/gmobilemedia && sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* /usr/lib/python2.6/site-packages/gmobilemedia/
```

---

### Post by held7over on 2009-07-26
Thanks credobyte!

Here is what happened:

lucky@ispy:~$ sudo mkdir /usr/lib/python2.6/site-packages/gmobilemedia && sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* /usr/lib/python2.6/site-packages/gmobilemedia/

[sudo] password for lucky: 

mkdir: cannot create directory `/usr/lib/python2.6/site-packages/gmobilemedia': No such file or directory
lucky@ispy:~$

---

### Post by credobyte on 2009-07-26
```
cd /usr/lib/python2.6/site-packages
``````
sudo mkdir gmobilemedia
``````
cd gmobilemedia
``````
sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* ./
```Execute all these commands separately & let us know, which one fails !


If it fails, post the output of:
```
cd /usr/lib/python2.6 && ls -l
```

Another question could be .. Python version ( python -V ) ?

---

### Post by held7over on 2009-07-26
Ha!  We didn't get far...

lucky@ispy:~$ cd /usr/lib/python2.6/site-packages
bash: cd: /usr/lib/python2.6/site-packages: No such file or directory
lucky@ispy:~$

---

### Post by credobyte on 2009-07-26
> **held7over said:**
> Ha!  We didn't get far...

lucky@ispy:~$ cd /usr/lib/python2.6/site-packages
bash: cd: /usr/lib/python2.6/site-packages: No such file or directory
lucky@ispy:~$

In that case, this shouldn't return any errors:
```
sudo mkdir /usr/python2.6/site-packages && sudo mkdir /usr/python2.6/site-packages/gmobilemedia && sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* /usr/lib/python2.6/site-packages/gmobilemedia/
```

---

### Post by held7over on 2009-07-26
Well, we have it on the run...


lucky@ispy:~$ sudo mkdir /usr/python2.6/site-packages && sudo mkdir /usr/python2.6/site-packages/gmobilemedia && sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* /usr/lib/python2.6/site-packages/gmobilemedia/

[sudo] password for lucky: 

mkdir: cannot create directory `/usr/python2.6/site-packages': No such file or directory
lucky@ispy:~$

---

### Post by credobyte on 2009-07-26
> **held7over said:**
> Well, we have it on the run...


lucky@ispy:~$ sudo mkdir /usr/python2.6/site-packages && sudo mkdir /usr/python2.6/site-packages/gmobilemedia && sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* /usr/lib/python2.6/site-packages/gmobilemedia/

[sudo] password for lucky: 

mkdir: cannot create directory `/usr/python2.6/site-packages': No such file or directory
lucky@ispy:~$

Ahh, my mistake ( forgot to add lib :p ):
```
sudo mkdir /usr/lib/python2.6/site-packages && sudo mkdir /usr/lib/python2.6/site-packages/gmobilemedia && sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* /usr/lib/python2.6/site-packages/gmobilemedia/
```

Anyway, what you need to do is to copy gmobilemedia folder from dist-packages to site-packages ( which doesn't exist - you need to create it ).

---

### Post by held7over on 2009-07-26
YES! YES! YES!

lucky@ispy:~$ sudo mkdir /usr/lib/python2.6/site-packages && sudo mkdir /usr/lib/python2.6/site-packages/gmobilemedia && sudo cp -r /usr/lib/python2.6/dist-packages/gmobilemedia/* /usr/lib/python2.6/site-packages/gmobilemedia/
lucky@ispy:~$

It worked, and it launches! Thanks!

So, if it isn't too much trouble, how did you figure out what we needed was in /usr/lib/python2.6/dist-packages/ ?

---

