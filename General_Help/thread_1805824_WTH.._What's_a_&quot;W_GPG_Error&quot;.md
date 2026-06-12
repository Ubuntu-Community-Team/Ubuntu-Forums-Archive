---
title: "WTH.. What's a &quot;W: GPG Error&quot; ?"
date: 2011-07-16
forum: General Help
---

### Post by UltraNEO* on 2011-07-16
OK.. I'm officially lost. What's a GPG? :confused::confused:

My machine has been presenting me this error for last few hours and I really don't know how to fix it, less understand what it means. :( I can tell you this much, it seems to happen when I'm attempting to "reload" the repositories in Synaptic. How i fix it? 

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21


---

### Post by CatKiller on 2011-07-16
[GPG]("http://en.wikipedia.org/wiki/GNU_Privacy_Guard").

The error message is telling you that you haven't added the encryption key for whichever PPA it is that you've added.

---

### Post by UltraNEO* on 2011-07-16
> **CatKiller said:**
> [GPG]("http://en.wikipedia.org/wiki/GNU_Privacy_Guard").

The error message is telling you that you haven't added the encryption key for whichever PPA it is that you've added.

Great.. |I'm sorry but that doesn't really help me there dude. 

I'm guessing "[http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release" might give me some clues? But ain't that part of the OS I'm running?

---

### Post by CatKiller on 2011-07-16
> **UltraNEO* said:**
> Great.. |I'm sorry but that doesn't really help me there dude. 

That's 'cause I can't remember the exact commands and I've been drinking. Don't want to give you bad info :)

When you added the PPA for whatever new-and-shiny software that wasn't included by default (not part of the OS, something you've added since), there were probably instructions to tell you how to add the key. Or you could search for "Ubuntu add PPA key" and you'll probably find some step-by-step instructions.

Or you could just not use that PPA, which would fix your immediate problem. Either through System -> Administration -> Software Sources, or by commenting out lines from your sources.list

---

### Post by UltraNEO* on 2011-07-16
> **CatKiller said:**
> That's 'cause I can't remember the exact commands and I've been drinking. Don't want to give you bad info :)

When you added the PPA for whatever new-and-shiny software that wasn't included by default (not part of the OS, something you've added since), there were probably instructions to tell you how to add the key. Or you could search for "Ubuntu add PPA key" and you'll probably find some step-by-step instructions.

Or you could just not use that PPA, which would fix your immediate problem. Either through System -> Administration -> Software Sources, or by commenting out lines from your sources.list


Don't worry... I appreciate you trying and understand it's the weekend. 
However, I found a solution..

> To solve this problem use this command:
  ```
gpg --keyserver keyserver.ubuntu.com --recv 9BDB3D89CE49EC21
```   Which retrieves the key from ubuntu key server and then this:
  ```
gpg --export --armor 9BDB3D89CE49EC21 | sudo apt-key add -
```   Which adds the key to apt trusted keys. This will solve the problem.
  
Just thought I'd post it here for whoever else that needs it. :)

---

### Post by SkippoGuangiacomo on 2011-07-17
that helped me too. Thanks! I did it in synaptic, but I wasn't successful...

---

