---
title: "No updates, yes updates: which is it?"
date: 2011-07-12
forum: General Help
---

### Post by chrisstankevitz on 2011-07-12
Please see the attached screen shot.

> There is an upgrade to install
> There are no updates to install
> There is a distribution update
> Your system is up-to-date

Q1: How can my system be up-to-date if there is an upgrade available?
Q2: How can my system be up-to-date if there is a distribution update?
Q3: How can my system have no updates to install if there is a distribution update?
Q4: What am I supposed to do/click?
Q5: Why can't I click the checkbox next to boost? (it is gray-ed out)

Thank you,

Chris

---

### Post by FormatSeize on 2011-07-12
> **chrisstankevitz said:**
> 
Q1: How can my system be up-to-date if there is an upgrade available?
```
sudo apt-get update
```
Don't do an upgrade unless you are well prepared for things to break. It's a common consensus that one should go with a fresh install instead of an upgrade.

---

### Post by CatKiller on 2011-07-12
> **chrisstankevitz said:**
> 
Q2: How can my system be up-to-date if there is a distribution update?
Q3: How can my system have no updates to install if there is a distribution update?

Packages can be upgraded. This doesn't remove existing packages, it just updates packages that are already installed.

Distributions can be upgraded. This will probably remove many packages.

These are independent, other than newer distributions contain newer packages.

Sometimes newer versions of packages can only be installed by removing existing versions of other packages. This generally only happens when you've added other repositories. Upgrading these packages can only be done with a dist-upgrade, to signal that you're happy to remove existing packages to satisfy the dependencies.

Whether you click on the button to upgrade to 11.04 is entirely up to you. You don't have to.

---

### Post by chrisstankevitz on 2011-07-12
CatKiller,

Thank you for describing "upgrades".  However, I am still unclear on what is an "update".  Specifically a "distribution update".

Thank you,

Chris

---

### Post by CatKiller on 2011-07-12
> **chrisstankevitz said:**
> Thank you for describing "upgrades".  However, I am still unclear on what is an "update".  Specifically a "distribution update".

In a packaging context, "update" means to refresh the list of which packages and which versions are available. "Upgrade" means to install a newer version of one, some or many packages. A "dist-upgrade" means

>        dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages.

The Update Manager refers to newer versions of packages as updates, and uses a refresh button to denote getting an up-to-date list of versions. I'd imagine that this is seen as more user-friendly. Perhaps Windows uses this nomenclature, or something.

If you do a dist-upgrade from the command line, it will sort out dependencies to install the latest versions of packages and that's it. You'll still be running your existing version of Ubuntu, just with newer packages.

If you select to upgrade to a new release in Update Manager, you'll generally end up downloading different versions of all of the packages you have installed. At the end of it you'll be on a different version of Ubuntu. It's functionally equivalent to changing all the entries in your list of repositories to point to the new version instead of the existing version and doing a dist-upgrade at the command line.

They're all similar concepts, and it doesn't help that different interfaces use the same words to mean different things, but hopefully that's helped show you what's going on.

---

### Post by chrisstankevitz on 2011-07-12
CatKiller,

Thank you for helping me and explaining what is a "distribution upgrade".  However, I am not asking about a "distribution upgrade", I am asking about a "distribution update".

The reason I am so interested in knowing about a "distribution update" is that, as you can see in the screenshot attached to the first post in this thread, that the "update manager" is trying to get me to perform a "distribution update" on "boost".  The checkbox next to boost is uncheckable.  Some people describe this as "grayed out".

Thank you again for your help and I hope I haven't scared you away with my quest to understand this mysterious "distribution update".

Chris

---

### Post by wildmanne39 on 2011-07-12
Hi, it just means that there is an update for that package which usually is to fix a problem, or improve performance, have you ever updated a program or driver in windows? it is the same thing.

---

### Post by devansh.j2007 on 2011-07-12
Well I dont know exactly but it happened to me also when i had wrong repositories added in softwear sources! so check it out if u the source u add is working or not!

---

### Post by CatKiller on 2011-07-13
> **chrisstankevitz said:**
> Thank you for helping me and explaining what is a "distribution upgrade".  However, I am not asking about a "distribution upgrade", I am asking about a "distribution update".

> **CatKiller said:**
> The Update Manager refers to newer versions of packages as updates, and  uses a refresh button to denote getting an up-to-date list of versions.  I'd imagine that this is seen as more user-friendly. Perhaps Windows  uses this nomenclature, or something.

You can upgrade that package by doing a dist-upgrade. I'd imagine that the reason you can't just upgrade that package normally is because you've added other repositories.

---

### Post by 3rdalbum on 2011-07-13
You should be able to go into Synaptic Package Manager and manually update that package. Just check that it's not going to remove a lot of packages. Sometimes new Ubuntu packages require the removal of a conflicting package, and Update Manager will not allow you to do the update if this is the case.

---

