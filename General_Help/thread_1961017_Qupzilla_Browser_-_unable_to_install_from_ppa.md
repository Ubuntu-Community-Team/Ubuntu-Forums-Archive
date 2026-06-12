---
title: "Qupzilla Browser - unable to install from ppa"
date: 2012-04-18
forum: General Help
---

### Post by maureenc on 2012-04-18
Hi,

I've been trying to install the Qupzilla Browser from the ppa as per standard method:

#sudo add-apt-repository ppa:nowrep/qupzilla

#sudo apt-get update

#sudo apt-get install qupzilla

but I keep getting the message:
"unable to locate package qupzilla!

I've tried several sites and several spellings but the result is always the same.

Has anyone here managed to install it?

---

### Post by Cheesemill on 2012-04-18
What version of Ubuntu are you using?

I've just added the PPA to check for you and it all looks fine to me:
```
rob@precise:~$ aptitude search qupzilla
p   qupzilla                                                                     - Web browser based on QtWebKit                                                         
p   qupzilla:i386                                                                - Web browser based on QtWebKit                                                         
p   qupzilla-next                                                                - Web browser based on QtWebKit                                                         
p   qupzilla-next:i386                                                           - Web browser based on QtWebKit                                                         

```There are packages available in the PPA for all releases since Lucid:
[https://launchpad.net/~nowrep/+ppa-packages]("https://launchpad.net/%7Enowrep/+ppa-packages")

Can you post the result of:
```
ls -lh /etc/apt/sources.list.d/
```
Just to make sure the PPA installed successfully.

---

### Post by maureenc on 2012-04-18
Hi Cheesemill,

Thank you for responding.

The machine I am having problems with is running Ubuntu 11.10 on a Toshiba AC100 Nvidia Tegra.... Not sure of that makes a difference but I notice that you are on Precise 12.04.

Have tried sending the sending the result back on the ls-lh command but the forum doesn't seem to like it.... I think I need to format it some way but not sure how? I keep getting the message that there are erros with my submission and I must send at least 1 character? Trying it here on my old desktop!

But the gist of it is that the repository is definitely in the list as "rw-r--r--1 root root 134 3012-14-18 15:52 nowrep-qupsilla-oneric.list and .save

---

