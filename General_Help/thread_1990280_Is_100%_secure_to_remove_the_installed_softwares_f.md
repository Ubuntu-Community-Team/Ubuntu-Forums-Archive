---
title: "Is 100% secure to remove the installed softwares from Ubuntu?"
date: 2012-05-29
forum: General Help
---

### Post by pelerin21 on 2012-05-29
Hi,

I will make a backup of Ubuntu 12.04. But before make a backup, I need to be sure if I can remove the softwares which I don't use. 

When I remove the softwares from software center, Ubuntu gives me an error. I could not get the error, but I always face different problems a while after removed the softwares which comes with Ubuntu default.

But now I am using 12.04. I never remove the apps which asks it will remove also gnome-desktop.

Thanks for your comments...

---

### Post by rai4shu2 on 2012-05-29
Feel free to remove any "-desktop" package you don't want. They don't really do anything other than provide a convenient way to change from one desktop to another (without actually fixing underlying issues with certain desktops that don't interact well with others).

---

### Post by wilee-nilee on 2012-05-29
> **pelerin21 said:**
> Hi,

I will make a backup of Ubuntu 12.04. But before make a backup, I need to be sure if I can remove the softwares which I don't use. 

When I remove the softwares from software center, Ubuntu gives me an error. I could not get the error, but I always face different problems a while after removed the softwares which comes with Ubuntu default.

But now I am using 12.04. I never remove the apps which asks it will remove also gnome-desktop.

Thanks for your comments...

The question is to broad, all packages have dependencies, which may get left behind, or take ones you need if removed.

If you want an answer here you need to get real specific. :)

I would would just run the OS removing stuff if you are not familiar can brick your setup in 2 seconds, and leave it unfixable except for a real geek.

---

### Post by wilee-nilee on 2012-05-29
> **rai4shu2 said:**
> Feel free to remove any "-desktop" package you don't want. They don't really do anything other than provide a convenient way to change from one desktop to another (without actually fixing underlying issues with certain desktops that don't interact well with others).

Really bad advice, is all I'm going to say.

---

### Post by pelerin21 on 2012-05-30
> **wilee-nilee said:**
> Really bad advice, is all I'm going to say.

?! I was not waiting this anwer from an Linux forums. Everyone says that you can remove apps from any Linux distro safely, it is not like windows OS...

---

### Post by wilee-nilee on 2012-05-30
> **pelerin21 said:**
> ?! I was not waiting this anwer from an Linux forums. Everyone says that you can remove apps from any Linux distro safely, it is not like windows OS...

Your question is not specific in which apps, some will remove the whole desktop as well, and some will remove other things you need. You have to know what your removing is attached to, dependencies.

That post was faulty in that a desktop has a ton of stuff that will not be removed by just running a remove desktop, look at this link and you will see what I mean.

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

With Linux you can brick your computer it will let you, so you have to do this from a informed position.

Basically what I am saying is be careful.

---

### Post by pelerin21 on 2012-05-30
> **wilee-nilee said:**
> Your question is not specific in which apps, some will remove the whole desktop as well, and some will remove other things you need. You have to know what your removing is attached to, dependencies.

That post was faulty in that a desktop has a ton of stuff that will not be removed by just running a remove desktop, look at this link and you will see what I mean.

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

With Linux you can brick your computer it will let you, so you have to do this from a informed position.

Basically what I am saying is be careful.

The apps which I want to remove from Ubuntu 12.04 are:

All games
brasero
gnome contacts
rhytmobox
totem
thunderbird
gwibber
simple-scan
ubuntu-one
shotwel

---

### Post by Paqman on 2012-05-30
> **rai4shu2 said:**
> Feel free to remove any "-desktop" package you don't want. They don't really do anything other than provide a convenient way to change from one desktop to another (without actually fixing underlying issues with certain desktops that don't interact well with others).

They're also crucial during upgrades. They can be removed without causing any immediate trouble, but the same can't be said for further down the line. There's no real point in removing them without removing their dependencies though. It won't save any real space.

In short: don't remove them if you actually want to use that desktop environment on your system.

---

### Post by Paqman on 2012-05-30
> **pelerin21 said:**
> The apps which I want to remove from Ubuntu 12.04 are:

All games
brasero
gnome contacts
rhytmobox
totem
thunderbird
gwibber
simple-scan
ubuntu-one
shotwel

I like [Synaptic]("apt:synaptic") for doing stuff like this, it's much more explicit about what will happen when you hit the "apply" button than Software Centre.

Put each one in and see what dependencies will be removed along with it. If there's nothing in there you mind losing then go for it.

---

### Post by Mark Phelps on 2012-05-30
> Everyone says that you can remove apps from any Linux distro safely, it is not like windows OS...

"Everyone" ... is usually WRONG.

In fact, you are generally safer removing apps from MS Windows since they tend to be independent of one another -- because they all tend to install all the components they need, on an individual basis.

In contrast, in Linux, if components an app needs are already installed (e.g., libraries), they will NOT be installed again.  But, when you later attempt to remove that same app, it will try to remove the components that were previously installed -- possibly breaking other apps or some critical system function.

So, my advice in general, is NOT to remove anything from Linux.  It takes far less space than any current Windows OS, and given the huge size of hard drives these days, drive space is no longer at a premium.

---

### Post by Paqman on 2012-05-30
> **Mark Phelps said:**
> 
In contrast, in Linux, if components an app needs are already installed (e.g., libraries), they will NOT be installed again.  But, when you later attempt to remove that same app, it will try to remove the components that were previously installed -- possibly breaking other apps or some critical system function.


No it won't. If the libs are still a dependency of another package they won't be uninstalled.

---

### Post by pelerin21 on 2012-05-31
1) Every app has it's own unistaller. When we remove an app, it reads what ever writes on the unistaller. So if the developers of the app (which we will remove it) has not write the unistaller properly, we can lost many libaries.

2) Or if Linux saves dependencies for every app, than the unistaller will not remove the dependencies which are using by other applications.

If the first is true, that means we have a really big problem. If the second is true, that mean I can remove any app that I want safely.

Can someone expain it please...:confused:

---

### Post by Paqman on 2012-05-31
A major component of your system is the package manager. In the case of Ubuntu this is a system called APT, which relies on another underlying system called dpkg. It handles all installs, uninstalls and upgrades of software on your system, and connects to the repositories to get packages that it needs.

The package manager is able to manage the dependency relationships between all packages on your system. It will not remove any package that is required by another package. Specifically telling it to remove a package that other packages depend on will result in all of them being removed, rather than being broken. In fact by default APT won't even remove dependencies that are not required any more unless you tell it to.

Example:
A user installs Package A. This depends on Packages B & C so they get automatically installed too.
The user then removes Package A. Only Package A is removed.
The user then installs Package D, which depends on Packages B & E.
The user then decides to do a bit of maintenance and tells the package manager to remove all superfluous packages, so the package manager removes Package C, which is no longer required.
If the user told the package manager to remove Package B it would also remove Package D, but would leave E installed.

The command to remove all packages that are no longer required is:
```
sudo apt-get autoremove
```

The primary aim of the package manager is to keep your system working. It won't break anything unless you go out of your way to do so. The worst it will do will be try to uninstall big chunks of things, and will warn you to give you the chance to change your mind first.

---

### Post by flemur13013 on 2012-05-31
> The apps which I want to remove from Ubuntu 12.04 are:
All games, brasero, gnome contacts, rhytm[o]box, totem, thunderbird, gwibber, simple-scan, ubuntu-one, shotwel[l].

FWIW, I removed all those except thunderbird and "ubuntu-one" (there's no package named that) without any problems at all.

You're right that the dependencies are sometimes messed up, but, from what I've seen, in the opposite direction: you tend to get a bunch of unnecessary stuff thrown in when you install something. (Why do I keep getting the completely extraneous "freepats"?)

---

### Post by pelerin21 on 2012-05-31
> **Paqman said:**
> 
The package manager is able to manage the dependency relationships between all packages on your system. It will not remove any package that is required by another package. 

How package manager knows the dependencies of each package? The developers of packages writes that inside the installer? Or Linux (Ubuntu - Package manager...) can understand it?

> **flemur13013 said:**
> FWIW, I removed all those except thunderbird and "ubuntu-one" (there's no package named that) without any problems at all.


Sorry, I mean ubuntu one.

> **flemur13013 said:**
> 
You're right that the dependencies are sometimes messed up,...

I do not clearly sure yet, because (on this thread) everyone writes something little bit different than others... :-#:confused:

---

### Post by Paqman on 2012-06-01
> **pelerin21 said:**
> How package manager knows the dependencies of each package? The developers of packages writes that inside the installer? Or Linux (Ubuntu - Package manager...) can understand it?


Part of the standard package for software on Debian systems (the .deb package standard) includes a list of what other packages it depends on or conflicts with. One of the package manager's main jobs is reconciling all those requirements and installing or removing things accordingly. It's clever stuff.

---

### Post by pelerin21 on 2012-06-01
> **Paqman said:**
> Part of the standard package for software on Debian systems (the .deb package standard) includes a list of what other packages it depends on or conflicts with. One of the package manager's main jobs is reconciling all those requirements and installing or removing things accordingly. It's clever stuff.

That means I can remove any apps 100% safe...

!?!?!?

---

### Post by garyzw on 2012-06-01
Would not "sudo apt-get autoremove (program name)" work? Substituting the name of the program for (program name)such as 

"sudo apt-get autoremove gwibber"

> **pelerin21 said:**
> The apps which I want to remove from Ubuntu 12.04 are:

All games
brasero
gnome contacts
rhytmobox
totem
thunderbird
gwibber
simple-scan
ubuntu-one
shotwel

---

### Post by Paqman on 2012-06-01
> **pelerin21 said:**
> That means I can remove any apps 100% safe...

!?!?!?

You should always check what the systems says it's going to remove before agreeing, just in case. But in general, yes it's completely safe to uninstall software.


> **garyzw said:**
> Would not "sudo apt-get autoremove (program name)" work? Substituting the name of the program for (program name)such as 

"sudo apt-get autoremove gwibber"

Yep. Adding the option "purge" also removes the config files.

[Lots more info here]("https://help.ubuntu.com/community/AptGet/Howto") if you want to get stuck into using APT on the command line.

---

