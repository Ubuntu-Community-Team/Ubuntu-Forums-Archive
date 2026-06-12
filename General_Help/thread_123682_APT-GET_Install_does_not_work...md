---
title: "APT-GET Install does not work.."
date: 2006-01-30
forum: General Help
---

### Post by daditlefsen on 2006-01-30
Hi. 

I am trying to install a FTP-program. I have opened the console and typed:
```
root@snuppa:~# apt-get install DPSFTP
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig
E: Klarte ikke å finne pakken DPSFTP

```

In English:
```
root@snuppa:~# apt-get install DPSFTP
Reading package list... Done
Creating content of something... Done 
E: Coud not fint the package DPSFTP

```

In Windows E: is the cdroom. But it did not help to put in the Ubuntu-cd. What sould I do to install a FTP client?


BTW, Sorry for the bad english ;)

---

### Post by kaamos on 2006-01-30
Hello!

First you should probably enable the extra repositories: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Then you can use synaptic to install packages: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

If you wish to use the commandline to install instead of synaptic, you must know the package name. So first search for it:
```
apt-cache search ftp
```
And when you find a package you want
```
sudo apt-get install gftp
```
(Gftp is one ftp-client.)

Hope this helps!

BTW: is that danish? ;)

---

### Post by daditlefsen on 2006-01-30
Thanks kaamos. Got GFTP up and running now:)

It's norwegian, looks like danish.

---

