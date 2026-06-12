---
title: "partial update offered on kernels?"
date: 2012-07-05
forum: General Help
---

### Post by sdowney717 on 2012-07-05
Running the latest ubuntu and this has not been resolved for days.
So what to do?

---

### Post by msammels on 2012-07-05
Not to be picky here, but if you're using 12.04, then why are your buttons on the right?

Anyway, as for the kernel, open the terminal and type:

```
uname -r
```

Compare it to the ones above. If (assuming the current one is PAE), are newer then it's up to you if you want to install it or not. Otherwise, if it's older, don't install it.

---

### Post by QIII on 2012-07-05
> **msammels said:**
> Not to be picky here, but if you're using 12.04, then why are your buttons on the right?

They can be moved there.

@sdowny717:

As you know, partial upgrades are highly discouraged. 

It could be that the mirror you are using has not been updated and some dependencies are not available.  Are you using Main?

---

### Post by plucky on 2012-07-06
> **sdowney717 said:**
> Running the latest ubuntu and this has not been resolved for days.
So what to do?

If you open a terminal and run ```
sudo apt-get dist-upgrade
``` and carefully read what it wants to do and will not remove everything,you can then give it the go ahead.

**Do not just accept the DEFAULT setting**

If it tells you it wants to remove your Desktop or something that might break your system,then say No and it will abort.

This has always worked for me.

Good luck

---

### Post by sdowney717 on 2012-07-06
> scott@scott-P5QC:~$ sudo apt-get dist-upgrade
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gir1.2-muffin-3.0 libcogl5 libmuffin0
The following NEW packages will be installed:
  linux-headers-3.2.0-26 linux-headers-3.2.0-26-generic-pae
  linux-image-3.2.0-26-generic-pae
The following packages will be upgraded:
  libclutter-1.0-0 linux-generic-pae linux-headers-generic-pae
  linux-image-generic-pae
4 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
Need to get 51.3 MB of archives.
After this operation, 178 MB of additional disk space will be used.
Do you want to continue [Y/n]? 


Did this just now and it completed ok

afterwards ran this

scott@scott-P5QC:~$ uname -r
3.2.0-25-generic-pae
scott@scott-P5QC:~$ 

I should reboot, even though not getting prompted from terminal

---

### Post by sdowney717 on 2012-07-06
> scott@scott-P5QC:~$ uname -r
3.2.0-26-generic-pae
scott@scott-P5QC:~$ 


after reboot showing this new kernel in use

---

### Post by sdowney717 on 2012-07-06
> **QIII said:**
> They can be moved there.

@sdowny717:

As you know, partial upgrades are highly discouraged. 

It could be that the mirror you are using has not been updated and some dependencies are not available.  Are you using Main?

ASFAIK yes using main. The partial message is was stuck with for about a week. 
I have been running with latest ubuntu on this pc ever since the release and keeping up with updates.

Fixing this has also fixed my Chrome issue with certain websites becoming unresponsive.

I upgraded another PC with the latest Ubunut and got none of this problem.

---

