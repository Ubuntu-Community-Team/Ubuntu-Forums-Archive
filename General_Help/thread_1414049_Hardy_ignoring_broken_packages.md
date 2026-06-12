---
title: "Hardy ignoring broken packages"
date: 2010-02-23
forum: General Help
---

### Post by neil86 on 2010-02-23
I have recently installed davmail on hardy. When I done this I had to install an old package to get it to work. 

My problem is now that I keep getting told that I have a broken package. Is there any way to ignore a broken package? It is stopping me from updating my system and from installing new packages.

Thanks

---

### Post by slakkie on 2010-02-23
Can you show the output of the error when installing packages?

---

### Post by neil86 on 2010-02-23
When I try to install a program using Synaptic it shows the "Mark for additional changes?" window saying that it will remove davmail. I dont want to mark it for removal because i need the package that will be removed.

Is this the error message that you meant?

---

### Post by slakkie on 2010-02-23
Could you, for the heck of it post output of the following command:

aptitude install -s hello


I don't use the GUI to update, so all the messages it shows are jibrish to me :)

---

### Post by neil86 on 2010-02-23
This is the output after the "aptitude install -s hello" command. I hope this helps.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  davmail 
The following packages are unused and will be REMOVED:
  dkms linux-headers-2.6.24-25 linux-headers-2.6.24-25-generic 
The following NEW packages will be installed:
  hello 
0 packages upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 19.8kB of archives. After unpacking 68.2MB will be freed.
The following packages have unmet dependencies:
  davmail: Depends: libswt-gtk-3.4-java which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
davmail

---

### Post by slakkie on 2010-02-23
I see what is going on, the required dependency cannot be met, so it tries to remove the broken package..

Since I cannot find the dependency in the hardy repo's.. The error is expected :)

```

$ apt-cache policy libswt-gtk-3.4-java
libswt-gtk-3.4-java:
  Installed: (none)
  Candidate: 3.4-2ubuntu3
  Version table:
     3.4-2ubuntu3 0
        300 http://archive.ubuntu.com jaunty/universe Packages
     3.4-1ubuntu1 0
        300 http://archive.ubuntu.com intrepid/universe Packages

```

As you can see, both Intrepid and Jaunty have the package. You could try and install that one. Or wait a couple of months (end of april) and upgrade to Lucid and you don't have to mix your system.

---

### Post by neil86 on 2010-02-24
Can the missing package be ignored in some way?

---

### Post by slakkie on 2010-02-24
> **neil86 said:**
> Can the missing package be ignored in some way?

Perhaps, but if you want to do that, you have to look into the documentation. I'm not going to "support" that. 

You can install the missing package from Intrepid. For mixing packages you can have a look at apt pinning, see also my blogpost on this matter: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

Best of luck!

---

