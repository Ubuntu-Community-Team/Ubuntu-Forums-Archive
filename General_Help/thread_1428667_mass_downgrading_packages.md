---
title: "mass downgrading packages"
date: 2010-03-13
forum: General Help
---

### Post by chris billington on 2010-03-13
Hello fellow ubuntu users,

I recently added a ppa that contained unstable versions of many packages that I already had. Doing an apt-get upgrade upgraded thirty packages or so.

Problem is, things broke and I want to go back to stable versions of all those packages. So I removed the ppa and thought about what to do next.

I could find all the packages and do a 'force version', but firstly there's no way I can remember what they all were, and secondly when I tried it for a few of them I was told many dependent packages would have to be removed. Packages that whilst dependent, worked fine with the older versions of their dependencies :|.

I've seen instructions whereby people in my position are told to do an apt-get update then apt-get upgrade after removing the ppa. This doesn't seem to work for me.

Is there a way to make all my packages downgrade to the most recent versions in the currently enabled repositories? Or will I just have to wait until the stable versions catch up and a normal upgrade replaces these packages?

---

### Post by topdownjimmy on 2010-07-10
I have exactly the same problem here.  Any help would be much appreciated, as I've now removed a couple very important packages that can't be reinstalled because of dependency version matching.

---

