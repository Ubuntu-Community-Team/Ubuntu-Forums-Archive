---
title: "Can't install EasyCam2 =("
date: 2010-04-14
forum: General Help
---

### Post by awall86 on 2010-04-14
I cant seem to install EasyCam2...

I used this link [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) and followed the instructions exactly how they are listed

I added the repositories, that worked just fine. 

But when I go to Terminal to do my sudo apt-get install easycam2-gtk

This is what i get:
[I]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
                Depends: easycam2-core but it is not going to be install[/I]


Can anyone help? Please

---

### Post by gunnarlinux on 2010-04-14
> **awall86 said:**
> I cant seem to install EasyCam2...

I used this link [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) and followed the instructions exactly how they are listed

I added the repositories, that worked just fine. 

But when I go to Terminal to do my sudo apt-get install easycam2-gtk

This is what i get:
[I]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
                Depends: easycam2-core but it is not going to be install[/I]


Can anyone help? Please

You need to install python2.4-glade2, try using ```
sudo apt-get update
``` Then try to install the dependency with the command ```
sudo apt-get install python2.4-gtk2
```

Hope this works :lolflag:

---

### Post by awall86 on 2010-04-14
Alrighty welllll I tried that and this is what it said:

[I]sudo apt-get install python2.4-gtk2
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package python2.4-gtk2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python2.4-gtk2 has no installation candidate[/I]

---

