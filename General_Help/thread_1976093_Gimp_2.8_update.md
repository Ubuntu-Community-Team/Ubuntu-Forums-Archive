---
title: "Gimp 2.8 update?"
date: 2012-05-08
forum: General Help
---

### Post by linuxuser12345 on 2012-05-08
Will Ubuntu be releasing the Gimp update to version 2.8 for Ubuntu 12.04? I don't want to have to go through installing a new PPA, completely removing the old Gimp, and fixing all the problems removing it created, so I would like to just wait for Ubuntu to distribute an update.

---

### Post by lukeiamyourfather on 2012-05-08
Generally the answer is no. If you want the latest and greatest all the time another distribution with rolling releases would be better.

---

### Post by smurphy on 2012-05-08
Didn't have any issues here. Worked out of the box.

---

### Post by PaulW2U on 2012-05-08
> **linuxuser12345 said:**
> Will Ubuntu be releasing the Gimp update to version 2.8 for Ubuntu 12.04? I don't want to have to go through installing a new PPA,

It'll probably be released as part of Ubuntu 12.10 so adding the PPA will be the way to get it while running Ubuntu 12.04.

---

### Post by raja.genupula on 2012-05-08
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp sudo apt-get update && sudo apt-get install gimp
```

do that to get Gimp latest .

---

### Post by Teber on 2012-06-22
ok so i followed the instructions. apt-get install output said latest version already installed. which is 2.6!

i'm using 64 bits. would that be it?

---

### Post by flipper T on 2012-06-22
you have added the ppa ?

---

### Post by Teber on 2012-06-22
yes i did.
software sources shows this url: [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu)

i then did apt-get update and apt-get install gimp

no joy :(

---

### Post by digithal on 2012-06-23
> **Teber said:**
> yes i did.
software sources shows this url: [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu)

i then did apt-get update and apt-get install gimp

no joy :(
sudo apt-get upgrade should get it :)

---

### Post by Teber on 2012-06-23
> **digithal said:**
> sudo apt-get upgrade should get it :)

thanks for your efforts. i'm still mystified as the following happened:

tried again. first sudo apt-get upgrade as suggested with the following result:

```
jan@jan-G31-M7-TE:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

then:

```
jan@jan-G31-M7-TE:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gimp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

gimp still version 2.6.11

now i'm lost. as it would seem, i made some kind of mistake somewhere...

---

### Post by blackbird34 on 2012-06-23
Have a look in the Software Center: there is a button in the top panel called "All Software", with a little arrow for a drop down menu which allows you to choose between browsing "All Software", "Canonical Partners", etc, and also lists your PPAs. 
I have installed Gimp through the same PPA; under this drop down menu, I can find _[otto-kesselgulasch's ]("http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu")_PPA under the name "gimp": if I click on it, I can browse *only* the packages that are in this PPA repository (i.e. the GIMP and a few graphics utilities). 

Check there. And I think you have to remove Gimp 2.6 before installing 2.8.

---

### Post by Teber on 2012-06-23
as suggested i removed the old version of gimp. and my system went fubaar(fouled up beyond almost all repair)! oh my, how could i be so stupid!

i repaired things by upgrading to 12.04 (note to self update your profile, you git!).

then installed the gimp as described in post #4. woot! i got gimp 2.8 now.

thanks to everybody for the help. the fubar part of things is of course entirely my fault :oops:

---

