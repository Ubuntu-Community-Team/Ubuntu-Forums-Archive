---
title: "Installed latest update and now I cannot connect via wireless."
date: 2010-10-15
forum: General Help
---

### Post by MSich on 2010-10-15
I just installed the latest updates from Update Manager in Lucid and I can no longer get a connection to my wireless router.  Is there a way to go back?  Unfortunately, I really don't remember what they were.  What I do remember is there were 11 or so, they were Lucid and networking components.  I did see a reference to SSL.

I update whenever the update manager comes up, and these were new in the last day.  I have a Karmic machine too, and those are not showing up on there.

I don't have any third party software sources on that pc.

Any ideas?

---

### Post by earthpigg on 2010-10-15
hi,

take a look at the log of what packages where installed/upgraded:

```
cat /var/log/apt/history.log
```

see if you can figure out which one you believe was the likely culprit - we can probably help you here.

once you believe you've isolated the package, see if you have an old(er) version of it in the machine's local archives:

```
ls /var/cache/apt/archives
```

if so, then uninstall the upgraded version and install the old version.

```
sudo dpkg -i /var/cache/apt/archives/package-name.deb
```

---

### Post by MSich on 2010-10-15
It's too bad there were so many.  My best guess (based on nothing really), one or more packages called erlang.

erlang-inets
erlang-syntax-tools
erlang-xmerl
erlang-ssl
erlang-mnesia
erlang-crypto
erlang-runtime-tools
erlang-base
erlang-public-key

All are version 13.b.3.dfsg-2ubuntu2.1.
All exist in the archive as 1%3a13.b.3-dfsg-2ubuntu2.1

If not those there were was a couple of gwibber upgrades and tzdata updates.

---

### Post by MSich on 2010-10-15
Synaptic Package Manager shows two versions of all the erlang packages one ending in ...2ubuntu2.1 (lucid updates) and one ending in ...2ubuntu2 (lucid).  It also indicates I have the 2.1 version installed.  Can I roll back to the earlier version?  I experimented with marking them for reinstallation and forcing the package.  But there were a lot of dependencies and they all weren't dependent on each other.  I decided to bail on the idea.

---

### Post by earthpigg on 2010-10-17
ya, you could potentially get stuck in dependancy hell if there are many.... i'm afraid i have no further advise, except maybe post all the updates that you took that day? maybe something will jump out or, hopefully, someone else will see something that i missed.

---

### Post by Hippytaff on 2010-10-17
If you get a choice of kernel at boot-up try choosing an older one and see if this works!?

---

### Post by xieon on 2010-10-17
i had a similar problem and fixed it 

[http://ubuntuforums.org/showthread.php?goto=newpost&t=1598798](http://ubuntuforums.org/showthread.php?goto=newpost&t=1598798)

---

### Post by MSich on 2010-10-17
Thanks for the suggestions guys. No luck on those.  I decided to backup my Home folder and try re-installing those packages through package manager.  I marked them all, and went for it.  It removed and reinstalled the dependencies ok.  Even though I reinstalled all the same versions, now everything seems to be working.  Something must have happened during the system update.

Thanks again.

---

