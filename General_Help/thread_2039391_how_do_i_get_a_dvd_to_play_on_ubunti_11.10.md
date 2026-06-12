---
title: "how do i get a dvd to play on ubunti 11.10"
date: 2012-08-08
forum: General Help
---

### Post by edpiet on 2012-08-08
hi how do i get a dvd to play on ubunti 11.10 i put dvd in drive but nothing comes up on sreen open door and dvd is spinning please help

---

### Post by Frogs Hair on 2012-08-08
Hello and Welcome

Install the Lubuntu restricted extras package from the software center if you haven't already  . The package includes Flash & codecs for playing media. 

For some encrypted DVDs the package at the link may be required.[http://www.ubuntuupdates.org/package/medibuntu_free/oneiric/free/base/libdvdcss](http://www.ubuntuupdates.org/package/medibuntu_free/oneiric/free/base/libdvdcss)

---

### Post by Frogs Hair on 2012-08-08
To get the last package you have to add the medibuntu repository see the link for the terminal commands and enter them one by one.  [http://www.ubuntuupdates.org/ppa/medibuntu_free?dist=oneiric](http://www.ubuntuupdates.org/ppa/medibuntu_free?dist=oneiric)

After the repository is added install the codec. ```
sudo apt-get install libdvdcss2
 
```

---

### Post by edpiet on 2012-08-10
hi yyah i have e bigger problem than that bought laptop from internet from ebay has ubuntu 11.10 guy bought fromsomeoe else sommm he doesnt not the first guys password so i been to all how too reset password sites on web and when i getto the type new password i type a new password in but its not typing anything so i figure that you just dont see when typing so i re type password hit enter next screen says no changes an i wipe hard drive clean with out a password and re insall if how is it done thanks

---

### Post by edpiet on 2012-08-11
Help!!!!!!!!!!!!!!!!!!!!!!! Cant download repairs for dvd not working untill i can fix  this problem 
from the beginning bought laptop from ebay (big mistake) 
this guy bought from someone else who put a password in for it needless to say the secound guy doesnt know password now i cant intsall or even set clock so been checking different sites and found how to reset password get to the part were i type new password and retype password and then get a error password unchanged authenication token maniplation error password unchanged( by the way the sytsem is ubuntu 11.10) so still more looking around sites and really cant find any thing that helps  different sites say try dirrerent comands my question to that is do i type the commands in the same place i am in now drop down shell prompt or do i have to get to some other aerea sorry i didnt mention that  before i bought this laptop i never heard of ubuntu  is there a way that i can just elinate the use of passwords all to gether that may solve all the problems thanks ed

---

### Post by marlow59 on 2012-08-11
Please make an effort to write in a more accurate way, I really had a lot of troubles to understand your problem.
Anyway, when you boot the computer, can you connect to a user? does this user have any password assigned ?

---

### Post by uRock on 2012-08-11
If you are looking to reinstall, then download the ubuntu 12.04 image here, [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

You can find directions for installing [here.]("https://help.ubuntu.com/community/InstallingXubuntu") If someone sent you the system with xubuntu already installed, then I do recommend a doing the install. Once reinstalled, we can help you get DVDs working.

---

### Post by Primefalcon on 2012-08-11
first run this

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update; sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```

then.....

if 32 bit run this
```
sudo apt-add-repository; sudo apt-get update; sudo apt-get install w32codecs libdvdcss2
```

if 64 bit run this
```
sudo apt-add-repository; sudo apt-get update; sudo apt-get install w64codecs libdvdcss2
```

---

### Post by edpiet on 2012-08-12
> **marlow59 said:**
> Please make an effort to write in a more accurate way, I really had a lot of troubles to understand your problem.
Anyway, when you boot the computer, can you connect to a user? does this user have any password assigned ?
sorry for the confusion
see if this is better when iboot computor it comes up guest , john ( password protected) now i f ii want to do any changes on computor like (change time ) or i tried to get dvd to work it always say that i need to have the adminastrators (JOHNS)PASSWORD and as in the first post i stated that john is the fisrt owner and computor has been sold now 3 time and password was not given 
SO HERE IS THE PROBLEM I HAVE A LAPTOP RUNNING UBUNTU 11.10 WITH A ADIMINASTRATOR PASSWORD UNKOWN TO ME SO I CANT MAKE CHANGES TO IT CAN I REINSTALL UBUNTU ON THIS LAPTOP WITHOUT PASSWORD (JOHN THE AMINASTRATOR ) 
ALSO I TRIED TO CHANGE PASSWORD BUT I GET A ERROR SAYING PASSWORD ERROR AUTH TOKEN ERROR UNCHANGED PASSWORD I REALLY DONT CARE ABOUT GETTING DVD TO PLAY UNTILL I CAN GET ETHER A NEW PASSWDORD SO I CAN CHANGE THINGS THEN I CAN WORRY ABOUT DVD

---

### Post by llamabr on 2012-08-12
Yes, that does seem frustrating.

If you do not know the admin password, and cannot contact the previous owner, the best thing to do is to reinstall ubuntu.  It will probably just take 30 minutes, including downloading, burning a disk, and reinstall.

In this way, you can be sure you're in control of what's actually on your machine, as well as what you put on there in the future, since you'll know the admin password.  It will also give you a little insight into the ubuntu process, which is very easy.  Start here:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Then, if you run into problems before, during, or after installation, bring them back here.

(Also, try to use punctuation in your posts.  Long run-on sentences are difficult for readers to parse).

---

### Post by nothingspecial on 2012-08-12
Prefix changed from lubuntu to ubuntu.

---

### Post by edpiet on 2012-08-12
> **llamabr said:**
> Yes, that does seem frustrating.
 
If you do not know the admin password, and cannot contact the previous owner, the best thing to do is to reinstall ubuntu. It will probably just take 30 minutes, including downloading, burning a disk, and reinstall.
 
In this way, you can be sure you're in control of what's actually on your machine, as well as what you put on there in the future, since you'll know the admin password. It will also give you a little insight into the ubuntu process, which is very easy. Start here:
 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
 
Then, if you run into problems before, during, or after installation, bring them back here
 
(Also, try to use punctuation in your posts. Long run-on sentences are difficult for readers to parse). thanks will i be able to reinstall with out a password

---

### Post by edpiet on 2012-08-12
thanks can i reinstall without a password and do i need to get cd or can i directly downlod from iternet

---

### Post by edpiet on 2012-08-12
i downloaded installlation to cd and tried to install nothing happened just a cd showed up in the icon section do i need a password to reinstall

---

### Post by uRock on 2012-08-12
Yes, you can reinstall without a password. When you turn the PC on, you have to interrupt the boot cycle, so that you can choose to boot from the CD. On many systems you have to press F12 to interrupt the boot cycle.

---

### Post by llamabr on 2012-08-12
> **uRock said:**
> Yes, you can reinstall without a password. When you turn the PC on, you have to interrupt the boot cycle, so that you can choose to boot from the CD. On many systems you have to press F12 to interrupt the boot cycle.

If you tell us what kind of machine you have, probably we can give you instructions about booting from cd.  You may have to adjust this in bios, or probably it's as easy as pressing f12.

---

