---
title: "general installation issues"
date: 2006-02-20
forum: General Help
---

### Post by Chemicalvamp on 2006-02-20
Hi, kubuntu is my first real, working linux install.. and i have a big problem... i have no idea how to install/upgrade anything...

i have a cd full of .tars i want installed.. I also have them on my hdd as .tar, And i have them extracted to a subfolder too.... can anybody tell me how you would do it?

p.s. i dont want a referal to a help file... i have looked through them and still cant get the info i need!

---

### Post by Jucato on 2006-02-20
First of all, welcome to the world of Linux and to Ubuntu! (or in your case, Kubuntu :D )
Secondly, what exactly are you trying to install? This info is important because o the third thing I'm going to say:

Thirdly, there are 3 ways to install stuff, ranging from absolutely easy to a bit (just a bit) difficult.
1. Easy way: installing from the repositories. Repositories are like databanks with loads and loads of programs configured for Ubuntu. Through a package manager (Adept, Synaptic, etc), everything will be automated: download of the package together with the necessary dependencies (things that are needed to successfully install and run it), and installation. 
2. Less easy way: installing a .deb file. You can think of .deb as a sort of installer. you run a command in the command prompt to install this. Actually, the packages in the repositories are all .deb files. the only difference is that installing through a package manager resolves (takes care) of the needed dependencies. Intalling a .deb manually, you need to know what dependencies are needed.
3. The least easy way: Installing from source code. Source code usually comes in .tar.gz files. But I'm not going into detail how to do this here. At least not until you could give us an idea what you are trying to install. Who knows, those might be found in the repository so it would save you a lot of trouble.

---

### Post by Adrian on 2006-02-20
Maybe you will find this document useful:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by Chemicalvamp on 2006-02-21
Sorry i didnt mention this before.. i didnt want to be refered to a help file because the dont usually help you do what you want to do *without* an internet connection. And the comuputer cannot be hooked up at the moment
so all i can do is take notes and burn cds

Sorry Fenyx but it looks like im going to be restricted to installing from code at the moment.. i noticed that alot of the packages i would like didnt come with the original installation.. (but thats ok cuz my last install of gentoo didnt install kde at all!) and those are all .tar.bz2, i have a few tar.tar, tar.gz and even a .tbz2    o.0

anyways i was messin around after my last post and found that i couldnt get administrative privlages... password didnt do anything... so i reformatted and tryed again.. after it was installed i hit the help files like i always do.. quit that and found package manager (adept).. tracked down the gcc thing and installed it, and a few other things. now when i try ./configure it says:
checking for blah... blah
checking blah... okay
checking for gcc... gcc
checking for c compiler defualt output file name... configure: error: c compiler cannot create executables

If i have to burn an entire repository i will :) just tell me the addy

---

### Post by Jucato on 2006-02-21
I think you also need to install the package build-essential to be able to compile properly. 
```
sudo apt-get install build-essential
```

Take note, however, that many of the packages on the CD might be a bit outdated and that perhaps many of the apps you like are available in the online repositories. (but what do you expect from a 1 CD installer anyway... ehehe!)

Also, there is a way to download only specific packages from the repositories (together with the needed dependencies) so that you could install it offline. However, I'm not entirely sure where these are downloaded/stored, and definetly sure that Adept doesn't offer this functionality. apt-get and synaptic (which can be installed from the cd installer) does have this.

Hope this helps. :D

---

### Post by Chemicalvamp on 2006-02-21
Well my ./configure no longer aborts 3 seconds in like before, i found and installed the files needed for c compiler, and it gets pretty far into it before it tells me this.
checking for X... configure: error can't find X includes. please check your installation and add the correct path

any ideas on what i need to install?

p.s. since the computer that is having these issues cannot be connected to the internet i dont think apt-get is going to connect to anything :/
thanks for the how-to for making my own repository, i should have fun with that one :)

---

### Post by aysiu on 2006-02-21
[QUOTE=Chemicalvamp]Sorry i didnt mention this before.. i didnt want to be refered to a help file because the dont usually help you do what you want to do *without* an internet connection. And the comuputer cannot be hooked up at the moment
so all i can do is take notes and burn cds[/QUOTE] Installing software in Ubuntu without an internet connection is going to be a painful experience. This may help:

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

Ultimately, though, I think you should be content with what you have for now and work on getting that connection later.

---

### Post by Chemicalvamp on 2006-02-21
that would work, but this computer.. my download and burn computer :) doesnt belong to me, it is a public computer and runs windows xp and i can only acess the guest account... (but it is connected to a 7mb/s down, 3mb/s up) so linux commands are no more then giberish to this computer :)

---

### Post by Chemicalvamp on 2006-02-23
ok so i got all the programs, games, and multimedia i wanted.. and all i had to do to get it was go to [http://www.kubuntu.org/packages/kde350/pool-breezy/](http://www.kubuntu.org/packages/kde350/pool-breezy/) and download every thing ending in _all.deb and _i386.deb, after burning and installing all of them (none of wich where properly configured) i ran adept and uninstalled and removed all of the packages that where "broken".. about 120 out of 560.

and the best part... i am now able to install from source :)
problem solved... for the most part.. btw if you do what i did.. get rid of the monopoly-like game right away.. if you dont... your gonna have issues.

---

