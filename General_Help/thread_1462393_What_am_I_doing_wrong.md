---
title: "What am I doing wrong?"
date: 2010-04-25
forum: General Help
---

### Post by curtis122 on 2010-04-25
Hello and I am new to using ubuntu. I have access to the itnernet only on a windows PC (because of family reasons) however I run ubunut on my offline PC for the fun of it :) what I do is I download packages and I did a bit of research on how to do it but iv obviously done something wrong . (I am trying to unpack and install secret mayro chronicles). Here is an attachment im hoping you could tell me were im going wrong and how to resolve it.

---

### Post by itiswhatitis on 2010-04-25
You have the packages on your Desktop and your terminal is in your home folder.

in terminal:
cd ~/Desktop

Then run your dpkg.

---

### Post by howefield on 2010-04-25
Just as an aside, I see you have a .bin file for Real Player on your desktop. You can download a .deb package from here should you wish to ...

[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

That's for Karmic.

---

### Post by mk1w86 on 2010-04-25
Instead you could use the download script function in Synaptic, for a guide have a look here:

[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript?action=show&redirect=SynapticPackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript?action=show&redirect=SynapticPackageDownloadScript)

You can also do similar things using apt. ;)

---

### Post by bumanie on 2010-04-25
Also ensure you have build-essential installed - > sudo apt-get install build-essential

---

### Post by curtis122 on 2010-04-25
Thank you for your suggestions . I have done what itiswhatitis instructed but now I have a new problem. When I press enter I get this :

dpkg: error processing smc_1.9.orig.tar.gz (--install): 
 subprocess dpkg-deb --control returned error exit status 2 
Errors were encountered while processing: 
 smc_1.9.orig.tar.gz

---

### Post by mk1w86 on 2010-04-25
> **curtis122 said:**
> Thank you for your suggestions . I have done what itiswhatitis instructed but now I have a new problem. When I press enter I get this :

dpkg: error processing smc_1.9.orig.tar.gz (--install): 
 subprocess dpkg-deb --control returned error exit status 2 
Errors were encountered while processing: 
 smc_1.9.orig.tar.gz

It looks like you're trying to install the source package which you cannot install using dpkg which is designed to install .deb packages.

Secret Maryo Chronicles is available in the repositories which you can install by running:

```
sudo aptitude install smc
```

EDIT: Just remembered your machine is offline ](*,), you can mark the smc package for installation in Synaptic (it will also automatically mark all dependencies required) and use the method I mentioned in my previous post to download and install the packages.

---

### Post by curtis122 on 2010-04-25
thanks I will do that

---

### Post by mk1w86 on 2010-04-27
These are the contents of some PM's between curtis122 and I, I have posted them here to see if anyone else can help or has any suggestions. :D

> Originally Posted by **curtis122**
*Hi im currently trying your suggestion on how to get SMC. However when i look for it in the package manager I cannot find it do I need to update it? Were am I going wrong?*

First, which Ubuntu version are you using?

Your package lists are probably out of date because your machine is offline and that could be the problem as you suggested.

I have just had another look at this (the link I gave you in my forum post):

[https://help.ubuntu.com/community/Sy...DownloadScript](https://help.ubuntu.com/community/Sy...DownloadScript)

and at the top of the page it says

> You can download old packages this way but you can not get any updated packages.

which I think is referring to being unable to update the package lists, so that particular method of installing packages offline might not be suitable for you.

Here is what I did to find the package anyway, just in case your problem is not what I have described above:

I went to System >> Administration >> Synaptic Package Manager. I then typed smc in the Quick search bar at the top of the window and marked the first package which was called smc for installation.


> Originally Posted by **curtis122**
*I am using the latest vesion 10.4 LTS.  iv just tryed what you said and nothing comes up. Iv also tryed unpacking the game from a tar.bz (i just right clicked) but i dont know if or how to install and how to run it.*

That is because the .tar.bz archive contains the source code for the game and you would have to compile it before installing it. You would be better off installing the Ubuntu .deb packages from the repository.

You could try apt-offline or apt-medium to download and install packages to your computer instead of the Syanptic method. They should both allow you to update your package lists. You can see details on them here and some other methods of installing packages offline here:

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

As a last resort you could always install the package and its dependencies manually. You can download them from here:

[http://packages.ubuntu.com/hu/lucid/games/smc](http://packages.ubuntu.com/hu/lucid/games/smc)

---

