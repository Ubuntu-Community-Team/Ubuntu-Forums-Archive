---
title: "Backtrack 5 tools in 11.04"
date: 2011-05-17
forum: General Help
---

### Post by killians31 on 2011-05-17
Hello,

I recently got my macbookpro5,5 fully working with Ubuntu 11.04. One question i have though, is would it be possible to add the backtrack 5 tools (i.e. a repository, etc.) into this build of Ubuntu?

I tried following these steps ([http://www.zimbio.com/Ubuntu+Linux/articles/e1_qHsbCMfz/Install+Backtrack+Applications+Ubuntu](http://www.zimbio.com/Ubuntu+Linux/articles/e1_qHsbCMfz/Install+Backtrack+Applications+Ubuntu)), but i am unable to ping: repo.offensive-security.com (which leads me to believe they changed the repo).

Any help is appreciated!

Thanks,
Ben

---

### Post by wojox on 2011-05-17
Use the archives [http://archive.offensive-security.com/](http://archive.offensive-security.com/)

I would recommend downloading the Gnome version onto a usb stick. ;)

---

### Post by lajjr on 2011-06-18
The repo is added by doing the following:
get the GPG key:
 wget -q [http://archive.offensive-security.com/backtrack.gpg](http://archive.offensive-security.com/backtrack.gpg) -O- | sudo apt-key add -

Add the main repo:
sudo echo "deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse" > /etc/apt/sources.list

Add the testing repo:
sudo echo "deb [http://sun.offensive-security.com/repotest/](http://sun.offensive-security.com/repotest/) ./" >> /etc/apt/sources.list

reference info from:
[http://sun.backtrack-linux.org/README.txt](http://sun.backtrack-linux.org/README.txt)

---

### Post by killians31 on 2011-06-19
> **lajjr said:**
> The repo is added by doing the following:
get the GPG key:
 wget -q [http://archive.offensive-security.com/backtrack.gpg](http://archive.offensive-security.com/backtrack.gpg) -O- | sudo apt-key add -

Add the main repo:
sudo echo "deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse" > /etc/apt/sources.list

Add the testing repo:
sudo echo "deb [http://sun.offensive-security.com/repotest/](http://sun.offensive-security.com/repotest/) ./" >> /etc/apt/sources.list

reference info from:
[http://sun.backtrack-linux.org/README.txt](http://sun.backtrack-linux.org/README.txt)

Thanks Lajjr, would this install the backtrack 5 tools?

Looking at the Readme (via the URL), it seems to reference backtrack 4.

---

### Post by boodoo on 2011-06-25
just install bt5 in your hard drive

and do

1 - change the password with

> passwd

and write your old and your new password 

2 - apt-get install synaptic

3 - in synaptic go to repository

tick the ubuntu main 10.04 repository

3 - apt-get update && apt-get upgrade

4 - apt-get install sofware-center && apt-get install .....(all the package where you know the name)......

then if you do a "software-center" in a shell it will launch it , free to you making a quickstart wtih this command line.
so you can install everything you want

5 - do the same for every soft or function in ubuntu with apt-get or software-center or synaptic . more exemple :  libre office, deluge, pdf reader, pidgin, skype, chrome....

6 - you have to forget unity and ubuntu 11.04, bt5 is based on 10.04, and gnome2 is quite better than unity, wait gnome3 is operationnal. you can try to do a apt-get install unity with the good repository for unity (add it wih synaptic)
 
7 - Enjoy :p , so easy make your customisabled bt5 distrib, the power of ubuntu core and bt5 tools.

so it's easier to activate ubuntu main repository than to activate bt5 repository in the latest release of ubuntu.

bt5 is a very good distrib ubuntu-based, try with virtualbox before. 
the bt5 developper team keep one version less for more stability.

[SOLVED]

---

### Post by bishop379 on 2011-07-09
> **boodoo said:**
> just install bt5 in your hard drive

 
7 - Enjoy :p , so easy make your customisabled bt5 distrib, the power of ubuntu core and bt5 tools.

so it's easier to activate ubuntu main repository than to activate bt5 repository in the latest release of ubuntu.


[SOLVED]

I would go with boodoo on this, I did the bt 5 install, and added the right repos, and it's just like I implemented bt 5 straight into Ubuntu 10.04, especially after some sweet customizing

---

### Post by zartas on 2011-07-10
> **boodoo said:**
> just install bt5 in your hard drive

and do

1 - change the password with

> passwd

and write your old and your new password 

2 - apt-get install synaptic

3 - in synaptic go to repository

tick the ubuntu main 10.04 repository

3 - apt-get update && apt-get upgrade

4 - apt-get install sofware-center && apt-get install .....(all the package where you know the name)......

then if you do a "software-center" in a shell it will launch it , free to you making a quickstart wtih this command line.
so you can install everything you want

5 - do the same for every soft or function in ubuntu with apt-get or software-center or synaptic . more exemple :  libre office, deluge, pdf reader, pidgin, skype, chrome....

6 - you have to forget unity and ubuntu 11.04, bt5 is based on 10.04, and gnome2 is quite better than unity, wait gnome3 is operationnal. you can try to do a apt-get install unity with the good repository for unity (add it wih synaptic)
 
7 - Enjoy :p , so easy make your customisabled bt5 distrib, the power of ubuntu core and bt5 tools.

so it's easier to activate ubuntu main repository than to activate bt5 repository in the latest release of ubuntu.

bt5 is a very good distrib ubuntu-based, try with virtualbox before. 
the bt5 developper team keep one version less for more stability.

[SOLVED]



Will You Marry Me? :D
just think all these magic tools together in a flash drive

---

### Post by dszprog on 2011-08-14
I can install drivers for my Broadcom Wireless on Ubuntu 11.04 (and Ati driver works well too)  I installed Backtrack 5, and followed your steps. At jockey-gtk both driver get error again and again :( At Ubuntu 11.04 they didn't stucked. :(  I have now [backtrack5 gnome 64]

---

### Post by taco taco tacos on 2012-01-12
this helped me alot thanks!!

---

### Post by boodoo on 2012-02-16
After working a bit more on bt5, lot of package are done to be used as root, and bt5 use specific kernel header.

So if you activate ubuntu main repositories, you will crush some BT5 system package. some of package of bt5 ppa won't work anymore correctly with ubuntu main repositorie activated.

More over don't install proprietary graphic driver like ATI or Nvidia. They should work but you won't use anymore BT5 GPU based calculs. Like Pyrit etc...

Best pratice are following:

1 - change root pswd  

2 - (All accessible from bt5 ppa) 
sudo apt-get install synaptic sofware-center open-office banshee chromium pidgin apache2 php5 etc ......

3 - never active ubuntu main repositories 

4- eventualy, add PPA if you really need a specific app not present in bt5 repo, or dld the .deb and do a [COLOR=DarkGreen]dpkg  --install packageName.deb[/COLOR]  _but never_ ubuntu main repository, 

5 - BT5 ppa has a lot of accessible package used on ubuntu

5 - the only one problematic package is Skype, i success for all other daily used.

---

### Post by Ardent Maverick on 2012-05-04
I wrote a script to add the BackTrack 5 repositories to your non-BackTrack install, here it is:

[https://github.com/thomhastings/backtrack-scripts/blob/master/get-bt5-repos.sh]("https://github.com/thomhastings/backtrack-scripts/blob/master/get-bt5-repos.sh")

---

### Post by Zvlwab on 2012-05-05
I guess this is a little easier:
[http://ubuntuforums.org/showthread.php?t=1882653](http://ubuntuforums.org/showthread.php?t=1882653)

---

### Post by zboymoney on 2012-12-07
> **dszprog said:**
> I can install drivers for my Broadcom Wireless on Ubuntu 11.04 (and Ati driver works well too)  I installed Backtrack 5, and followed your steps. At jockey-gtk both driver get error again and again :( At Ubuntu 11.04 they didn't stucked. :(  I have now [backtrack5 gnome 64]

just a note i found the 32 bit gnome more stable than 64 bit gnome. Pulseaudio didnt work for me in 64 bit and every little bit the drivers would fail. In 32 bit i didnt even have one problem yet and its been almost a year since i switched from 64 to 32 bit.

---

