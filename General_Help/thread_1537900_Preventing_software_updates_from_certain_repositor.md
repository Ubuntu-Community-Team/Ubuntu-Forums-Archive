---
title: "Preventing software updates from certain repositories"
date: 2010-07-24
forum: General Help
---

### Post by User-007 on 2010-07-24
I just want to prevent updates from certain repos, which are intended only for installation purposes. Those repos, however, also include updates for officially bundled packages, and i dont want to update them - just want to keep those as official versions. Is there any way to do that?

Thanks
User JB

---

### Post by hhh on 2010-07-24
Your second sentence is confusing me, but to disable a repository (which will prevent those packages from updating), see this...
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by User-007 on 2010-07-24
Thanks.

Sorry for confusing. I just asked that how to prevent added repos to offer any updates.

I know thats possible to unselect those repos from Synaptic or mark them as comments in sources.list, but thats not the solution, because it also prevents me to install any software from those repos.

I am too lazy to always select any tickboxes or modify my sources.list when needed to install some software from that repos.

User JB

---

### Post by neoargon on 2010-07-24
It's so easy . there is an application named software sources (System->administration->software sources) . Open it. You can check and uncheck the software sources there (no need to open software sources file and mark as comment) . 

When you install a software, check the software source and uncheck  after installation . I don't think anything is possible other than that.

Any more help?

---

### Post by User-007 on 2010-07-24
Ok, so the answer is that added repositoires push software updates - that cannot be prevented. The only way is to keep repositories (which are not intended for update anything) unselected (or marked as comments in sources.list).

---

### Post by qamelian on 2010-07-24
> **User-007 said:**
> Ok, so the answer is that added repositoires push software updates - that cannot be prevented. The only way is to keep repositories (which are not intended for update anything) unselected (or marked as comments in sources.list).
You could lock the version of files you don't want changed in Synaptic, but if an application in a PPA requires a version other than what you've locked at, you just won't be able to install the app you wanted from the PPA.

---

### Post by howefield on 2010-07-24
> **User-007 said:**
> Ok, so the answer is that added repositoires push software updates - that cannot be prevented

Not exactly, you can lock the package version so that updates are not offered.

Synaptic Package Manager > Package > Lock Version.

---

### Post by User-007 on 2010-07-24
Yes, I know that I can use apt lock or something like that but that was not that I asked. Repositories like getdeb among others include lots of stuff and it would be giant job to lock those all. After that I still can't get updates from official repos...

Thanks a lot still!

---

### Post by ankspo71 on 2010-07-24
I thought "neoargon" gave some pretty good advice on how to disable certain repositories.

If worse comes to worse, you could disable automatic updates completely, and then manually update only the packages you want to update. I think there is an entry for "automatic updates" in Gnome's "start up applications" list over in the system menu. Simply uncheck the updater's entry to disable it.

---

### Post by emarkay on 2010-10-05
> **howefield said:**
> Not exactly, you can lock the package version so that updates are not offered.
Synaptic Package Manager > Package > Lock Version.

Be advised that this is ignored in "Recovery Console" if "Fix Broken Packages" is selected: [https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222)

---

