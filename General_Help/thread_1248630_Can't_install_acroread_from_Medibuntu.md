---
title: "Can't install acroread from Medibuntu"
date: 2009-08-24
forum: General Help
---

### Post by nemarona on 2009-08-24
Hi all,

I'm running 32-bit Xubuntu Jaunty with all the latest updates.
I enabled the Medibuntu repository following the instructions on [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

When I try to install the acroread package I get the following error:
```
sudo apt-get install acroread
[sudo] password for eduardo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
```

The contents of the file /etc/apt/sources.list.d/medibuntu.list:
```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free #Medibuntu - Ubuntu 9.04 "jaunty jackalope"
#deb-src http://packages.medibuntu.org/ jaunty free non-free #Medibuntu (source) - Ubuntu 9.04 "jaunty jackalope"
```

Any ideas?

---

### Post by credobyte on 2009-08-24
Open Add/Remove and install it from there. Mediabuntu offers x64 acroread only.

---

### Post by Bucky Ball on 2009-08-24
... and did you also install the key?

---

### Post by michy99 on 2009-08-24
Make sure you have the partner repositories enabled.

---

### Post by drs305 on 2009-08-24
Edit: That's what a distraction does ... michy99 got to you first.

If you don't find it in the medibuntu repository for your release, I think you can find it by enabling the canonical partner repository in Synaptic, Settings, Repositories, Third Party, enable the canonical partner link. Then hit "Reload" to refresh the list.

---

### Post by nemarona on 2009-08-24
Thanks for all the answers!

Enabling the partner repositories did the trick. I find it odd that Medibuntu provides only the 64-bit version of acroread.

Thanks again!

---

### Post by fballem on 2009-08-27
Where is the key for the Partner repository?

---

### Post by nemarona on 2009-08-28
I don't think you need a key for the partner repositories. Bucky Ball was presumably referring to the Medibuntu key (which I installed).

---

### Post by scouser73 on 2009-08-28
Is Acroread the same as [[COLOR="Red"]**Adobe PDF Reader**[/COLOR]]("http://get.adobe.com/uk/reader/otherversions/")?  If so you can install [[COLOR="Red"]**Adobe PDF Reader**[/COLOR]]("http://get.adobe.com/uk/reader/otherversions/") by selecting **Linux -x86 (.deb)** from the drop-down menu, selecting your choice of language via the drop-down menu & then clicking **Download Now**.

---

### Post by drs305 on 2009-08-28
> **scouser73 said:**
> Is Acroread the same as [[COLOR="Red"]**Adobe PDF Reader**[/COLOR]]("http://get.adobe.com/uk/reader/otherversions/")?  If so you can install [[COLOR="Red"]**Adobe PDF Reader**[/COLOR]]("http://get.adobe.com/uk/reader/otherversions/") by selecting **Linux -x86 (.deb)** from the drop-down menu, selecting your choice of language via the drop-down menu & then clicking **Download Now**.

Yes it is and yes you can. 

Download the .deb, double-click it and gdebi will install it for you. Installing it by this method will register it but if you don't have the correct repositories enabled (see above posts) you won't get updates.

---

