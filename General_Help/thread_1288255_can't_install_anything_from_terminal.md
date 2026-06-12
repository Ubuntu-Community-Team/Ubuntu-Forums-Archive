---
title: "can't install anything from terminal"
date: 2009-10-11
forum: General Help
---

### Post by bL3nDi.b0y on 2009-10-11
hello there:(

im trying to install filezilla,flash player..., but don't work:(
Im getting this message when im trying to install from terminal:

```
[B]r00t@bL3nDi:~$ sudo apt-get install filezilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package filezilla
r00t@bL3nDi:~$[/B] 
```

any help:?:

---

### Post by MelDJ on 2009-10-11
you seem to not have added the repository. add it, then try again. And you seemed to have logged in terminal as root. its unneccesary since you can just use sudo. add the medibuntu repo with the steps here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mcduck on 2009-10-11
Make sure you have Universe & Multiverse repositories enabled (in System/Administration/Software Sources).

..and of course remember to run "sudo apt-get update" first. ;)

---

### Post by Pvt_Beeano on 2009-10-11
Odd, I just tried that and it worked;

> ben@xpc-ubu:~$ sudo apt-get install filezilla
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  filezilla-common libwxbase2.8-0 libwxgtk2.8-0
The following NEW packages will be installed
  filezilla filezilla-common libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 4 newly installed, 0 to remove and 11 not upgraded.
Need to get 7674kB of archives.
After this operation, 22.4MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.


---

### Post by Pvt_Beeano on 2009-10-11
Oops, feel stupid now.....

---

### Post by bL3nDi.b0y on 2009-10-11
> **MelDJ said:**
> you seem to not have added the repository. add it, then try again. And you seemed to have logged in terminal as root. its unneccesary since you can just use sudo. add the medibuntu repo with the steps here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

thanks all:P

Repair code:P
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```again thanks so much MelDJ :P

---

### Post by MelDJ on 2009-10-11
> **Pvt_Beeano said:**
> Odd, I just tried that and it worked;

what do you mean?

---

### Post by Pvt_Beeano on 2009-10-11
Nothing, I tried his command and it worked on my computer, then felt like a fool as the solution had already been posted - please ignore.

---

### Post by mcduck on 2009-10-11
> **MelDJ said:**
> you seem to not have added the repository. add it, then try again. And you seemed to have logged in terminal as root. its unneccesary since you can just use sudo. add the medibuntu repo with the steps here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Actually it's not in the Medibuntu repository. It's in Universe. :)

---

