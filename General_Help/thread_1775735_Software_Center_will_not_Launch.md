---
title: "Software Center will not Launch"
date: 2011-06-05
forum: General Help
---

### Post by Iono12345 on 2011-06-05
Hi,
  When I click on the software centre and Synaptic package manager will not launch and gives me the below error message or the dial spins and then nothing happens.

E: Type 'src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by celticbhoy on 2011-06-05
> **Iono12345 said:**
> Hi,
  When I click on the software centre and Synaptic package manager will not launch and gives me the below error message or the dial spins and then nothing happens.

E: Type 'src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

A little more info will help, what version of Ubuntu are you using, and do you use Ubuntu-Tweak?

A quick workaround would be to remove the wine-ppa list file, but it could just be an incompatible version.

---

### Post by Iono12345 on 2011-06-10
> **celticbhoy said:**
> A little more info will help, what version of Ubuntu are you using, and do you use Ubuntu-Tweak?

A quick workaround would be to remove the wine-ppa list file, but it could just be an incompatible version.

Hey Celticbhoy,
  I'm using version 10.10, how do I remove the wine-ppa list file?  I've actually been trying to uninstall wine or any wine program and it hangs any suggestions?
Thanks

---

### Post by linuxinstalledfromhdd on 2011-06-10
One of the easiest way would be to install Ubuntu-Tweak and use the source center to remove them. 

The PPA to install Ubuntu-Tweak is about 1/3 the way down the list.

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by nitstorm on 2011-06-10
```
rm /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```

That will remove the Wine PPA for Maverick.

---

### Post by bahubindu on 2011-06-10
> **Iono12345 said:**
> Hi,
  When I click on the software centre and Synaptic package manager will not launch and gives me the below error message or the dial spins and then nothing happens.

E: Type 'src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Bro, I know the problem.

OPEN the file(/etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list) in "root" mode. and then see the file, you will see a single line with "src" written... remove the line and everything will be working fine... I had the same problem with SYNAPTIC.

It is caused because you added a new PPA of wine and that made that.

The extra line is on the "last" line of the file.

---

### Post by Iono12345 on 2011-06-10
> **bahubindu said:**
> Bro, I know the problem.

OPEN the file(/etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list) in "root" mode. and then see the file, you will see a single line with "src" written... remove the line and everything will be working fine... I had the same problem with SYNAPTIC.

It is caused because you added a new PPA of wine and that made that.

The extra line is on the "last" line of the file.

Ok I hate to ask and really I've typed all kinds of commands and even did a search for root commands and whatnot.

How do I change to my root directory?  I've done the CD and various directories

When I type in the command it asik me if I want to proceed I type "Y" and it says permission denied obviously I'm not in the root directory.
Thanks in advance

On that note is there a cheat sheet for directory commands?

---

### Post by Iono12345 on 2011-06-11
ok got into my root by typing sudo su then entered the information provided and got this

"bash: /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list: Permission denied
root@KentUbuntu:/home/kent#"

---

### Post by Iono12345 on 2011-06-11
Ok got it thanks to all this did the trick rm/etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list...once again thanks for all the help

If there is a cheat sheet guide for commands and you can point me in the right direction it would be most appreciated.

---

