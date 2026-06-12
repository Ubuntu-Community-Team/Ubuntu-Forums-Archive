---
title: "Wubi install?"
date: 2010-10-07
forum: General Help
---

### Post by JshPuppy on 2010-10-07
Someone help me out here... Wubi isn't installing UNR correctly. Every time it downloads the iso, the next step is to download it again? And then again? And again? And again?

What's going on here? It will forever download! And it wont install.

Ubuntu Desktop Edition seems to install fine, so if there is a way to change Ubuntu Desktop Edition to UNR, that would be cool too.

Computer: Aspire One 160 GB. Trying to install UNR using Wubi (Don't want to deal with that partitioning nightmare again!)

---

### Post by bcbc on 2010-10-07
wubi.exe is hardcoded to release 10.04.1. Not all flavours of Ubuntu were released with 10.04.1 including Netbook. You just need to find an older version of wubi.exe.

Either mount the .iso and extract the wubi.exe from there or download a copy from the net. e.g. pick rev189 from [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/)

---

### Post by JshPuppy on 2010-10-07
Ah, thank you! That explains why it's stuck in an endless loop.

I've tried everything, like puting the iso in the same folder, running it as admin, restarting the internet, stopping updates, etc.

Well, it's safe to say that this installation finished in two minutes flat!

---

### Post by cgroza on 2010-10-07
Good to hear that. Maybe later you will consider making a real install because Wubi is slower than normal install.

---

