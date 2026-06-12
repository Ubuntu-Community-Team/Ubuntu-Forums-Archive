---
title: "glibc-2.3.6 amd64"
date: 2010-01-01
forum: General Help
---

### Post by oxman on 2010-01-01
I would have posted in 64bit help but there wasn't a way for me to do it. The "New Thread" button wouldn't appear???

I'm using Hardy. Blender requires glibc-2.3.6 I can not find any packages for this lib. Any help is appreciated.

---

### Post by falconindy on 2010-01-01
2.3.6 is ancient (~4 years old). Surely, you could find a newer version of blender that uses a more up to date version of glibc.

---

### Post by LuisGMarine on 2010-01-01
The problem is that you are running Hardy.  Since it is an LTS you wont always have new packages for the purpose of keeping the system stable and not off setting the balance by having "new" packages that are prone to more bugs and borking your system.

Honestly here is the launchpad for the package ..
[https://launchpad.net/ubuntu/+source/glibc/2.3.6-0ubuntu3]("https://launchpad.net/ubuntu/+source/glibc/2.3.6-0ubuntu3")

You can try to install it, but I'm not sure if this will break your system.  But just so you know it's a problem when you want new packages and the libraries that it uses when you are running and older but more "stable" release of Ubuntu.  I ran into a similar problem with Banshee.  Not much help, but just letting you know some stuff =\ best of luck, and have a happy new year!

---

### Post by oxman on 2010-01-01
> **falconindy said:**
> 2.3.6 is ancient (~4 years old). Surely, you could find a newer version of blender that uses a more up to date version of glibc.

Thanks for the reply falconidy. glibc-2.3.4 is what Blender calls for to run properly with its latest release as per:[http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

Do you think a later version of glibc would work just as well?

---

### Post by oxman on 2010-01-01
> **LuisGMarine said:**
> The problem is that you are running Hardy.  Since it is an LTS you wont always have new packages for the purpose of keeping the system stable and not off setting the balance by having "new" packages that are prone to more bugs and borking your system.

Honestly here is the launchpad for the package ..
[https://launchpad.net/ubuntu/+source/glibc/2.3.6-0ubuntu3](https://launchpad.net/ubuntu/+source/glibc/2.3.6-0ubuntu3)

You can try to install it, but I'm not sure if this will break your system.  But just so you know it's a problem when you want new packages and the libraries that it uses when you are running and older but more "stable" release of Ubuntu.  I ran into a similar problem with Banshee.  Not much help, but just letting you know some stuff =\ best of luck, and have a happy new year!

Hey, thanks for the tip troop. I'm going to give it a shot. Perhaps aptitude will help me with any dependency issues. This is a big help. I appreciate your reply and your service marine!

---

### Post by adam814 on 2010-01-01
If I'm not mistaken glibc is one of the core libraries in any Linux system.  I believe almost everything links against it (including gcc which is used to build everything else).  I wouldn't downgrade it just to run one particular app and risk breaking it all.  It's probably decently backward compatible.  Or at least it's worth trying before you try to downgrade glibc.

---

### Post by oxman on 2010-01-01
You have all given me good advice. Takes a while for the message to penetrate my old cranium. Installed the latest Blender in my home directory and ping! Works perfectly and better than the repos version. No glibc messing around needed.
 
 Thanks again.

---

### Post by dcstar on 2010-01-01
> **oxman said:**
> I would have posted in 64bit help but there wasn't a way for me to do it. The "New Thread" button wouldn't appear???


The 64-bit forum is now officially "retired" - there is a post at the top of it explaining why (and yes, it took me a while too to figure out why I couldn't post to it as well).

---

### Post by oxman on 2010-01-03
> **dcstar said:**
> The 64-bit forum is now officially "retired" - there is a post at the top of it explaining why (and yes, it took me a while too to figure out why I couldn't post to it as well).

Ha! Thanks for the heads up. I was blaming my old release :)

---

