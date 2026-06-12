---
title: "Stop APT from updating certain packages"
date: 2010-07-14
forum: General Help
---

### Post by olejon on 2010-07-14
I have som packages installed from the Ubuntu repos that I don't want to be updated (if a new version comes) when I run "apt-get upgrade". How can I forbid apt to update those packages, but update all of the others packages as normal?

---

### Post by plucky on 2010-07-14
> **olejon said:**
> I have som packages installed from the Ubuntu repos that I don't want to be updated (if a new version comes) when I run "apt-get upgrade". How can I forbid apt to update those packages, but update all of the others packages as normal?

Open Synaptic Package Manager,find your package and click on it,then  use the **Lock Version** under **Package** in **Synaptic Package Manager**.

Good Luck

---

### Post by olejon on 2010-07-14
> **plucky said:**
> Open Synaptic Package Manager,find your package and click on it,then  use the **Lock Version** under **Package** in **Synaptic Package Manager**.

Good Luck

Thanks, but the problem is that I use Ubuntu Server! So I need a way to do it in CLI.

---

### Post by nothingspecial on 2010-07-14
```
echo package hold | dpkg --set-selections
```

---

### Post by QLee on 2010-07-14
> **olejon said:**
> Thanks, but the problem is that I use Ubuntu Server! So I need a way to do it in CLI.

The concept is called APT pinning and it is too complicated to explain in a few sentences in a forum. Careful decisions have to be made and the state of the individual system involved will have to be considered. But you have the keyword to start your investigation, you can set the pin in a file, /etc/apt/preferences. After that you can apt-get as usual.

However, there should be a good reason for holding a package at a specific version and you want to be sure that you don't miss any security updates that might leave your server exposed. Hopefully, you've already considered that.

---

### Post by dcstar on 2010-07-14
> **QLee said:**
> The concept is called APT pinning and it is too complicated to explain in a few sentences in a forum. Careful decisions have to be made and the state of the individual system involved will have to be considered. But you have the keyword to start your investigation, you can set the pin in a file, /etc/apt/preferences. After that you can apt-get as usual.

However, there should be a good reason for holding a package at a specific version and you want to be sure that you don't miss any security updates that might leave your server exposed. Hopefully, you've already considered that.

AFAIK APT Pinning uses a different database then the Synaptic method, so anyone using the Synaptic method to pin packages will have those settings totally ignored by any APT Upgrade process. There is a bug that has been around for ages, but it was acknowledged and basically put in the "too hard at the moment" basket: 

[https://bugs.launchpad.net/synaptic/+bug/42178](https://bugs.launchpad.net/synaptic/+bug/42178)

I believe that you can pin them using things like Aptitude, but I am not 100% sure on that.

**If more people go to that bug report and add themselves to the list of affected users then it might actually get some attention!**

---

### Post by QLee on 2010-07-14
[QUOTE=dcstar]AFAIK APT Pinning uses a different database then the Synaptic method, so anyone using the Synaptic method to pin packages will have those settings totally ignored by any APT Upgrade process. There is a bug that has been around for ages, but it was acknowledged and basically put in the "too hard at the moment" basket: 

[https://bugs.launchpad.net/synaptic/+bug/42178](https://bugs.launchpad.net/synaptic/+bug/42178)

I believe that you can pin them using things like Aptitude, but I am not 100% sure on that.
[/QUOTE]

Except that this is a server, no X, no GUI.

---

### Post by emarkay on 2010-10-05
> **QLee said:**
> Except that this is a server, no X, no GUI.

Yes, but that wasn't specified in teh title, so searches on this topic are read by all with this issue.

Regardless, be advised that "recovery Console", "Fix Broken Packages" also ignores any Pinning or Locking: [https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222)

---

### Post by Crazedpsyc on 2010-10-05
Here, have some more beans (even though they're hidden) thank you for that post. I have been staring at an upgrade for vice for months not knwoing how to get rid of it (since the repo 64 bit version doesn't work) and that just made it go away. I'm much happier now that I can just check all updates when I come bach from vacation and find 50 available!

---

