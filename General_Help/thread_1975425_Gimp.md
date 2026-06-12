---
title: "Gimp"
date: 2012-05-07
forum: General Help
---

### Post by botokiller on 2012-05-07
Hi everyone!
How do I install GIMP 2.7 or 2.8 on Ubuntu. I literally tried dozens of different methods, but after each one I saw good old 2.6 logo. Apt-get has only 2.6, installing from tar.bz2 requires some "babl" library which i cannot install. How do I solve this problem?

---

### Post by Cavsfan on 2012-05-07
This should get you version 2.8.

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

---

### Post by Cavsfan on 2012-05-07
Maybe not. I just tried it and it could not find the repository.

---

### Post by davidvandoren on 2012-05-07
Which ubuntu are you using?
If you are using 12.04 there is the option to compile it from source or to add the repos.

```
 [COLOR=red][FONT=monospace]
[COLOR=Black]sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp[/COLOR]
[/FONT][/COLOR]
```Installing it from source has the advantage that you can install both gimp 2.6 and 2.8
go here

[http://ubuntuforums.org/showpost.php?p=11822010&postcount=22](http://ubuntuforums.org/showpost.php?p=11822010&postcount=22) 

follow the instruction and instead ```
wget ftp://ftp.gimp.org/pub/gimp/v2.8/gimp-2.8.0-RC1.tar.bz2
```download the latest version gimp-2.8.0 not RC1

  **wget [ftp://ftp.gimp.org/pub/gimp/v2.8/gimp-2.8.0.tar.bz2](ftp://ftp.gimp.org/pub/gimp/v2.8/gimp-2.8.0.tar.bz2)**

---

### Post by Cavsfan on 2012-05-07
I just removed the repo and the key.
I am sticking with gimp 2.6.11 myself.

---

### Post by botokiller on 2012-05-07
I use ubuntu 11.04. I need gimp 2.7+ for its single window interface.

---

### Post by Cavsfan on 2012-05-07
Try this:

```
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update 
sudo apt-get dist-upgrade gimp -y
sudo apt-get install gimp-plugin-registry -y
```This should pull in gimp 2.7.x for Ubuntu 11.04

---

### Post by traditionalist on 2012-05-07
This worked for me; ( on 12.04 64 BIT), running well, no problems at all.

[http://www.noobslab.com/2012/04/install-deepin-software-center-on.html](http://www.noobslab.com/2012/04/install-deepin-software-center-on.html)

Screenshot;

[[IMG]http://img193.imageshack.us/img193/8509/selection004c.png[/IMG]](http://img193.imageshack.us/i/selection004c.png/)

Regards...Trad

---

### Post by forrestcupp on 2012-05-07
> **Cavsfan said:**
> This should get you version 2.8.

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

That works great in 12.04, but it doesn't work in any earlier versions of Ubuntu. The mattheus ppa that you posted later should work. I was kind of interested in whether or not he updated to 2.8 in that ppa, or stuck with 2.7?

---

### Post by Cavsfan on 2012-05-07
> **forrestcupp said:**
> That works great in 12.04, but it doesn't work in any earlier versions of Ubuntu. The mattheus ppa that you posted later should work. I was kind of interested in whether or not he updated to 2.8 in that ppa, or stuck with 2.7?

Yes, that otto-kesselgulasch ppa did not even exist. And I believe the mattheus ppa will work.
I have no interest in a new gimp myself. Mine serves me fine.

```
cavsfan@cavsfan-desktop:~$ gimp --version
GNU Image Manipulation Program version 2.6.11
```

Hopefully botokiller will let us know which version it pulls in.

---

### Post by ragtag on 2012-05-07
If you're on 2.7, you should definitely update to 2.8. The odd number versions of Gimp are really previews for the next version, and are not considered stable (even though they often are), while 2.8 is a "proper" release.

I hope the Ubuntu team updates the default Gimp version in Ubuntu to Gimp 2.8.

---

### Post by Cavsfan on 2012-05-07
> **ragtag said:**
> If you're on 2.7, you should definitely update to 2.8. The odd number versions of Gimp are really previews for the next version, and are not considered stable (even though they often are), while 2.8 is a "proper" release.

I hope the Ubuntu team updates the default Gimp version in Ubuntu to Gimp 2.8.


Good to know!
OK, I added the ppa and performed the steps in post #7.

```
cavsfan@cavsfan-desktop:~$ gimp --version
GNU Image Manipulation Program version 2.7.2

```From looking at the Gimp website, it looks like 2.8 was just released a couple of days ago and I could not find a way to get it.
I am guessing the normal ppas and the one I just added will update to 2.8 eventually.

---

### Post by Cavsfan on 2012-05-07
On the About for Gimp 2.7.2 it clearly states "This is an unstable development release" as **ragtag** stated.
I'm removing the ppa, key and uninstalling it.

Going back to 2.6.11.

2.8 should be made available soon one would think.

---

### Post by botokiller on 2012-05-08
I installed 12.04 and [davidvandoren]("http://ubuntuforums.org/member.php?u=1150513")'s way worked, thanks to all of you guys.

---

