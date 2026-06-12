---
title: "dependecies not satisfiable"
date: 2011-09-22
forum: General Help
---

### Post by hotshot247 on 2011-09-22
i'm using the 64-bit ubuntu 11.04 and i'm trying to install the flashplugin-nonfree package and it tells me that it depends on flashplugin-installer but it is not going to be installed and it goes down the list...
i try to install what it says it depends on and it just keeps on going...
flashplugin-installer depends on ia32-libs
ia32-libs depends on lib32v4l-0
lib32v4l-0 depends on libv4l-0
and then it says that libv4l-0 is already the newest version and now i don't know what to do about this. can anybody help me with this issue? thanks!

---

### Post by seawolf167 on 2011-09-22
If you install 

```
sudo apt-get install ubuntu-restricted-extras
```

then try your original install do you still get the error?

---

### Post by hotshot247 on 2011-09-22
> **seawolf167 said:**
> If you install 

```
sudo apt-get install ubuntu-restricted-extras
```

then try your original install do you still get the error?

i tried to install ubuntu-restricted-extras and it said that it's already the newest version.

---

### Post by perspectoff on 2011-09-22
I think they took the newest proprietary flash installer out of ubuntu-restricted-extras. (The version in ubuntu-restricted-extras is an old one that will not work with the newest content.)

I had to install it separately in 11.04 (but was able to do so by hunting around the package manager for flash).

I used to like Flash quite a bit, but they've gotten so aggressive about updates that it is difficult to stay current with their most recent version and the dependencies required.

That should be a lesson to the Ubuntu MOTUs who want to go to a rolling release, too: Don't Do It!

No one can consistently update that frequently, and when one package insists on updating dependencies, other packages tend to stop working.

When content providers roll out content with the latest Flash in mind, it leaves a large number of users in the dust (not only in Linux but in other OS'). It's a good way to get users to search for other options. 

I no longer post my website content in Flash for this reason.

---

### Post by oldos2er on 2011-09-22
If you installed ubuntu-restricted-extras, it includes flash, although it's the 32-bit version + nspluginwrapper.

If you want to install 64-bit flash, click the FlashAid link in my sig.

---

### Post by hotshot247 on 2011-09-23
i fixed this issue. for the record just in case somebody wants to know, i went to ubuntu-tweak and enabled the Adobe Flash (x86-64) source and then installed it from there and it works like a charm.

---

