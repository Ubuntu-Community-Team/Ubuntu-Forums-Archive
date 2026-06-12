---
title: "Network simulator 2"
date: 2011-09-18
forum: General Help
---

### Post by akash.abhinav on 2011-09-18
Hey everyone,
i am new to this forum and ubuntu altogether.I need ubuntu to work on my project which would require ns2.can someone guide me as to how to get and install it.Also i have heard that ubuntu poses a lot of problems when it comes to ns-2.I dont want to start on my project and then hit a dead end because of some error.Please guide me.I am using ubuntu 10.04.
Regards

---

### Post by haqking on 2011-09-18
> **akash.abhinav said:**
> Hey everyone,
i am new to this forum and ubuntu altogether.I need ubuntu to work on my project which would require ns2.can someone guide me as to how to get and install it.Also i have heard that ubuntu poses a lot of problems when it comes to ns-2.I dont want to start on my project and then hit a dead end because of some error.Please guide me.I am using ubuntu 10.04.
Regards


Do you require ns 2 as it is pretty old.

[http://www.gns3.net/](http://www.gns3.net/) is much better..it is in the repos as well i think, not sure on version though but still much better than ns2

---

### Post by akash.abhinav on 2011-09-18
Hey,
The problem is i have to use it as it is in my course curriculum.If i screw up bad then maybe my prof will allow me.So for now i least wanna give it a try.You think you could help me please.
Regards :)

---

### Post by haqking on 2011-09-18
> **akash.abhinav said:**
> Hey,
The problem is i have to use it as it is in my course curriculum.If i screw up bad then maybe my prof will allow me.So for now i least wanna give it a try.You think you could help me please.
Regards :)


There is a guide here [http://lukasz.chrost.com/node/25](http://lukasz.chrost.com/node/25)

it is a couple of years old, not sure how well it work on recent Ubuntu versions, shouldnt be too bad.  But im pretty sure there are a few issues with it.

If you can i would go with gns3 if you can as it will do everything and more than ns-2 did.

from what i recall it isnt much simpler to install on to windows either.

gns3 is the way to go if you can

---

### Post by sanderj on 2011-09-18
> **akash.abhinav said:**
> Hey everyone,
i am new to this forum and ubuntu altogether.I need ubuntu to work on my project which would require ns2.can someone guide me as to how to get and install it.Also i have heard that ubuntu poses a lot of problems when it comes to ns-2.I dont want to start on my project and then hit a dead end because of some error.Please guide me.I am using ubuntu 10.04.
Regards

Normally I would ask you to tell 3 things you tried yourself, and what happened. And I certainly don't want to do your homework.

But, hey, well, OK, here's the link: [https://launchpad.net/~wouterh/+archive/ppa](https://launchpad.net/~wouterh/+archive/ppa)

> PPA description

This PPA contains packages for the network simulator (ns-2), see [http://www.isi.edu/nsnam/ns/](http://www.isi.edu/nsnam/ns/) for more information.

These packages are based on the debian packages for an older version of ns-2 by Andre Herms (see [http://bode.cs.uni-magdeburg.de/~aherms/debian/](http://bode.cs.uni-magdeburg.de/~aherms/debian/)).

There are currently no 64-bit packages. The current packages do not compile on 64-bit and I have no 64-bit machine available to troubleshoot the compilation process. If you succeed in compiling the packages on 64-bit, let me know. I'll be glad to host the updated packages here.


---

### Post by uRock on 2011-09-18
If the OP would like help with installing a PPA, then he/she may feel free to ask for such help. That's what we're here for. :)

---

### Post by akash.abhinav on 2011-09-26
Thanks one and all for the help.I have done the installation upto the part where it is mentioned in the link.Now how to go about it further.It seems that i need to start installing the software from this ppa.

abhinav@ubuntu:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/wouterh/ppa/ubuntu/](http://ppa.launchpad.net/wouterh/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done

What to do now??

---

### Post by akash.abhinav on 2011-09-26
I tried to find the next step to my last sent msg.I now know that i have to build a package but i have no clue how to start about it.Please guide, 
reagrds

---

### Post by haqking on 2011-09-26
> **akash.abhinav said:**
> I tried to find the next step to my last sent msg.I now know that i have to build a package but i have no clue how to start about it.Please guide, 
reagrds

```
sudo apt-get install ns
```

I am guessing seeing as that is the software you want from the added ppa. or it might be **ns-2**

---

### Post by tspradeepkumar on 2011-12-12
Hey 
please look at these websites for ns2 installation and help
[http://www.pradeepkumar.org](http://www.pradeepkumar.org)
[http://www.nsnam.com](http://www.nsnam.com)

---

