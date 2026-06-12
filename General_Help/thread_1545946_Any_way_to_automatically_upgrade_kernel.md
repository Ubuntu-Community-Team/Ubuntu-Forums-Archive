---
title: "Any way to automatically upgrade kernel?"
date: 2010-08-04
forum: General Help
---

### Post by inameiname on 2010-08-04
Currently, I added the PPA: 'deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main' and this seems to work in getting me the most recent kernel, however I must check it occasionally, and install it manually, with 'sudo apt-get install linux-image-2.6.35-14-generic linux-headers-2.6.35-14-generic' (which is the most recent in that PPA). So basically, every time there is a kernel update in there, such as 'linux-image-2.6.35-15-generic' or something, I must 'sudo apt-get install' it manually.

Anybody know how to have it automatically install the latest kernel? Is that even possible?

---

### Post by WorMzy on 2010-08-04
The linux-image package always depends on the latest available kernel in the default repositories, but unless this custom repository has a similar dummy package, I think you'll have to keep manually updating.

---

### Post by Cavsfan on 2010-08-04
I don't believe anything will update automatically on here.
You can use this command to see if one is available and install it **sudo apt-get dist-upgrade**

You can also use these two command instead of Update Manager as they will tell you more info about what is going to be installed.

[B]sudo apt-get update
sudo apt-get upgrade[/B]

---

### Post by inameiname on 2010-08-04
Oh, so sudo apt-get dist-upgrade will do that then? Thus, you are saying when say linux-image-2.6.35-15-generic becomes available, as the """-14-generic is the current one, it will be found by sudo apt-get dist-upgrade?

That'd be cool, as I always use the terminal anyway to update things, using such things as sudo apt-get update and sudo apt-get upgrade, so I can do that if it works.

---

### Post by Cavsfan on 2010-08-04
> **inameiname said:**
> Oh, so sudo apt-get dist-upgrade will do that then? Thus, you are saying when say linux-image-2.6.35-15-generic becomes available, as the """-14-generic is the current one, it will be found by sudo apt-get dist-upgrade?

That'd be cool, as I always use the terminal anyway to update things, using such things as sudo apt-get update and sudo apt-get upgrade, so I can do that if it works.

Yes, the terminal is the best way to get the updates and since this is an LTS, if you have your update settings 
to only pick up stable updates, then **sudo apt-get dist-upgrade** will get kernel updates every time. 
I think that is all it is for, but not 100%. That is all I have gotten from it.

---

### Post by mcduck on 2010-08-05
Since that kernel repository doesn't provide any metapackage for the kernel (and obviously the kernel metapackage in the official repositories doesn't use kernels from that repository) you just have to install the kernel updates manually when available.

dist-upgrade has nothing to do with kernel updates.

"apt-get upgrade" updates installed packages to latest available versions, and is also able to add a new packages if some update requires that.

"apt-get dist-upgrade" is exactly the same as above, but is also able to remove packages, if updates require that.

From the GUI tools, the Update Manager works like "apt-get upgrade", while updating through Synaptic works like "apt-get dist-upgrade".

What comes to update manager showing such updates, keep in mind that by default it will only show non-security updates one per every seven days. And if you run a manual update, the time resets and it's again 7 days before it can appear again.

---

### Post by TBABill on 2010-08-05
Why would you want to always have the latest kernel as soon as it is available? Why upgrade to a newer kernel at all unless you had some type of configuration, support or driver issue that the update would correct? If your system already works properly as configured, what do you gain with an incremental kernel update? Just curious about this unless there are important system security updates, speed enhancements or other more mission critical items contained....what would be the gain?

---

### Post by Indigo340 on 2010-08-05
I have been trying to solve a long standing problem with my DVD/RW drive and have just heard from someone else with the same problem that the latest kernel update appears to address this issue. As I am going to Thailand in a few days, it will be a welcome relief if I can get it sorted before I leave as the reliability of their Internet service is not good. I will be there for at least 6 months so I have a lot to gain by getting the latest release installed and tested asap.

Having said that, the latest release I just installed appears to be 2,6,32-24 when I was expecting it to be 2.6.35

---

### Post by TBABill on 2010-08-05
You won't see 2.6.35 in Ubuntu 10.04 that I'm aware of. That'll be a 10.10 change. Since you are very short on time you could look on [www.distrowatch.com]("http://www.distrowatch.com") and do a search. You can search by kernel version for any distro using the kernel you require. You may be forced to change distros, but if the issue is more important than which distro you use, changing over may be a possibility, especially on a separate partition until you are sure it is a good replacement distro for the time being.

---

### Post by 0004tom on 2010-08-05
Once you've updated your sources list with the PPA, reload the package list. Then your going to have to search thought Synaptic Package Manager for the new kernel to install it.

```
tom@L0CALH0ST:~$ uname -a
Linux L0CALH0ST 2.6.35-14-generic #19~lucid1-Ubuntu SMP Mon Aug 2 04:23:21 UTC 2010 x86_64 GNU/Linux
tom@L0CALH0ST:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid 
```

---

### Post by Cavsfan on 2010-08-05
Wonder why my kernel is older? It was just updated today.

```
cavsfan@cavsfan-desktop:~$ uname -a
Linux cavsfan-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
cavsfan@cavsfan-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:       Ubuntu 10.04.1 LTS
Release:           10.04
Codename:       lucid
cavsfan@cavsfan-desktop:~$ 
```

---

### Post by Cavsfan on 2010-08-05
> **mcduck said:**
> Since that kernel repository doesn't provide any metapackage for the kernel (and obviously the kernel metapackage in the official repositories doesn't use kernels from that repository) you just have to install the kernel updates manually when available.

dist-upgrade has nothing to do with kernel updates.

"apt-get upgrade" updates installed packages to latest available versions, and is also able to add a new packages if some update requires that.

"apt-get dist-upgrade" is exactly the same as above, but is also able to remove packages, if updates require that.

From the GUI tools, the Update Manager works like "apt-get upgrade", while updating through Synaptic works like "apt-get dist-upgrade".

What comes to update manager showing such updates, keep in mind that by default it will only show non-security updates one per every seven days. And if you run a manual update, the time resets and it's again 7 days before it can appear again.

I am in no way even close to your amount of experience with linux/ubuntu, but my experience has been different than you state 
above. It works like this for me:

**sudo apt-get update** refreshes the repositories.

**sudo apt-get upgrade** upgrades, installs and removes packages or programs
producing this output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```**sudo apt-get dist-upgrade** has only provided new kernels to be installed with a "y" if a kernel is available.

This morning I got an upgraded kernel which came via **sudo apt-get upgrade**.
But, that was not a new kernel only an upgrade to the one I already had.

Every single kernel that has been installed on Lucid since initial installation was supplied via [B]sudo apt-get dist-upgrade.
[/B]And this command has never upgraded or removed anything. 

I have not used Update Manager to install a single update of any kind.
Via the **dist-upgrade** which produces the same output as displayed above I have seen where it is holding back
3 packages and each of those times they were parts of a new kernel and later that day or the next I was able 
to install that kernel via [B]sudo apt-get dist-upgrade.

[/B]I am not trying to argue with you on this issue. I was testing Lucid after beta and **Ranch Hand** explained that 
those three commands work in the manner I have mentioned.

He said he uses only those 3 commands also and called Update Manager Update Mangler.

---

### Post by mcduck on 2010-08-05
Sorry, my mistake on "upgrade" being able to add new packages. Indeed it doesn't do that.

But otherwise it really works like I said in my post, "upgrade" is able to update any package as long as that doesn't require removing existing packages or adding new ones. And "dist-upgrade" does exactly the same, but with the added ability of adding new packages and removing existing ones if that's required for the update.

So, you can install any update using the "dist-upgrade", not just the kernels, but you really rarely need to do so. Especially if you are only using official Ubuntu repositories, and aren't running on the development version, because the package version are frozen in Ubuntu releases and all the updates available are just security updates and fixes to serious bugs, patched to the current version of packages whenever possible instead of giving you brand new versions. So you'll never get a completely new kernel version, for example, if you are running a normal Ubuntu release and don't use some third-party repository to provide such kernels to you.

Basically you can just use "apt-get upgrade" all the time, and if there are packages that are held back, then try with "dist-upgrade".


From man apt-get:

upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version

dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary

---

### Post by mcduck on 2010-08-05
> **Cavsfan said:**
> Wonder why my kernel is older? It was just updated today.

```
cavsfan@cavsfan-desktop:~$ uname -a
Linux cavsfan-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
cavsfan@cavsfan-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:       Ubuntu 10.04.1 LTS
Release:           10.04
Codename:       lucid
cavsfan@cavsfan-desktop:~$ 
```

If you read the first post, inameiname is using a PPA repository that provides newer kernels.

2.6.32 is the only one that will ever be available in 10.04's official repositories.

---

### Post by inameiname on 2010-08-05
Seems like there is much discussed in this post since I made it. Thanks for all the input about upgrading a kernel and whatnot. As Mcduck said, 2.6.32 will be the only one available through the official repos for Lucid, and I believe 2.6.32-24 is the latest currently available there, and as such, I decided to test out that PPA I mentioned which houses the latest, 2.6.35. 

Anyway, as to why I feel like upgrading, I just like bleeding edge / latest things, and so far have found the latest kernels either have fixed or improved most things, so what not. Actually, I used to have this issue where my laptop's audio would not turn back on until restart once I opened the lid back up, an issue that resulted for a year, and it was fixed just in the last month with a kernel update. So there are advantages. Of course, for those that aren't able to restore to an older time, or repair what's been done, best not to update through a PPA like I am doing, but just let it upgrade the kernel through the usual Lucid repos.

Oh, and thanks to all for the input on just what "upgrade", "dist-upgrade", "update" means.

Guess I can concluded that using that PPA with 2.6.35, there is no way to have it automatically upgrade to a newer kernel when it's available like how the 2.6.32 one does in the official Lucid repos when a newer one comes out for it. Ah well. I'll just do it manually, no big deal.

---

### Post by Cavsfan on 2010-08-06
> **mcduck said:**
> Sorry, my mistake on "upgrade" being able to add new packages. Indeed it doesn't do that.

But otherwise it really works like I said in my post, "upgrade" is able to update any package as long as that doesn't require removing existing packages or adding new ones. And "dist-upgrade" does exactly the same, but with the added ability of adding new packages and removing existing ones if that's required for the update.

So, you can install any update using the "dist-upgrade", not just the kernels, but you really rarely need to do so. Especially if you are only using official Ubuntu repositories, and aren't running on the development version, because the package version are frozen in Ubuntu releases and all the updates available are just security updates and fixes to serious bugs, patched to the current version of packages whenever possible instead of giving you brand new versions. So you'll never get a completely new kernel version, for example, if you are running a normal Ubuntu release and don't use some third-party repository to provide such kernels to you.

Basically you can just use "apt-get upgrade" all the time, and if there are packages that are held back, then try with "dist-upgrade".


From man apt-get:

upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version

dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary

I wasn't trying to argue about it. I was just stating my experience with the 3 commands.

> **mcduck said:**
> If you read the first post, inameiname is using a PPA repository that provides newer kernels.

2.6.32 is the only one that will ever be available in 10.04's official repositories.

Thanks for the clarification...

---

