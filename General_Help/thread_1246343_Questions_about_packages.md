---
title: "Questions about packages"
date: 2009-08-21
forum: General Help
---

### Post by capitanomalley on 2009-08-21
Hello,
I've just started using ubuntu and I have some questions about source install and installing package-wise through synaptic/manually.

Where and what environment variable do I edit the path for packages?

If I download a package manually (not using synaptic) is synaptic supposed to detect that it was installed and update it's repository?

I got a group of local packages (~20) and wanted to install all of them by selecting them and pressing enter but package manager only allows one instance at a time (I ended up opening 20 windows). Is there better way to do this?

Also off-topic but:
Is there a way to get the 'close by group' option for the task bar, similar to windows?

Appreciate any help.

---

### Post by kanikilu on 2009-08-21
> **capitanomalley said:**
> I got a group of local packages (~20) and wanted to install all of them by selecting them and pressing enter but package manager only allows one instance at a time (I ended up opening 20 windows). Is there better way to do this? Someone correct me if I'm wrong, but assuming the order of installation doesn't matter, then the easiest way to install a bunch of packages would be from the commandline: ```
cd /path/to/packages
sudo dpkg -i *.deb
```

---

### Post by decoherence on 2009-08-21
> **capitanomalley said:**
> Hello,
I've just started using ubuntu and I have some questions about source install and installing package-wise through synaptic/manually.

Where and what environment variable do I edit the path for packages?


now sure what you mean. what are you trying to accomplish? installing software under a certain directory? any particular reason why? (there might be better ways)

> 
If I download a package manually (not using synaptic) is synaptic supposed to detect that it was installed and update it's repository?


if you downloaded it manually, there is no repository associated with it, thus it will not be automatically updated (unless a version that IS in the repository becomes newer than the one you got manually.) However, Synaptic WILL recognize the package and allow you to remove/re-install it as if it were part of the repository (and just to be clear, by package we mean files with a .deb suffix and by 'repository' we mean Ubuntu's web servers that host the various repositories that Synaptic reads, combines and displays to you, alongside any manually downloaded packages which didn't come from a repository)

> I got a group of local packages (~20) and wanted to install all of them by selecting them and pressing enter but package manager only allows one instance at a time (I ended up opening 20 windows). Is there better way to do this?

under synaptic's file menu is an option that says "Add downloaded packages." I've never used this, but I'd guess it might do what you want.

> 
Also off-topic but:
Is there a way to get the 'close by group' option for the task bar, similar to windows?

Appreciate any help.

if your right click the area just to the left of the task bar and select "preferences" you can tell it to group windows. If you right click on a window group, you get an option to close them all.

since you say you're new to Ubuntu, I should mention that one doesn't generally manually download and install packages unless they have a good reason to. Packages that don't come from the repository have a higher chance of screwing up your system.

---

### Post by capitanomalley on 2009-08-21
thanks for the replies, both solutions worked for adding the packages. 
@decoherence
about path I was just being curious about the whole process and if there was some sort of order of precedence concerning those gotten from synaptic other than manually.

I installed them manually due to lack of an internet connection on the hosting computer, so that would be the reason.

---

### Post by decoherence on 2009-08-24
> **capitanomalley said:**
> @decoherence
about path I was just being curious about the whole process and if there was some sort of order of precedence concerning those gotten from synaptic other than manually.

I installed them manually due to lack of an internet connection on the hosting computer, so that would be the reason.

Cool. In that case, if/when you do get a net connection on the computer, those manually installed packages will be replaced automatically when the ones in the repository become newer. Ubuntu will always prefer the most recent version it can find unless you tell it to do otherwise.

cheers and enjoy!

---

