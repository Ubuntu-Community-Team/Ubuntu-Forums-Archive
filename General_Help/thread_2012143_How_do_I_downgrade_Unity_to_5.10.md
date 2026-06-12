---
title: "How do I downgrade Unity to 5.10?"
date: 2012-06-28
forum: General Help
---

### Post by AleveSicofante on 2012-06-28
Due to bug [https://bugs.launchpad.net/compiz-core/+bug/996604](https://bugs.launchpad.net/compiz-core/+bug/996604) I need to downgrade Unity to 5.10.


  I've tried doing it via terminal (sudo apt-get install unity=5.10.0-*) but I get dependencies issues.
  

Is there any other way? How do I solve those dependency issues? Is it  possible to do it in Synaptic? (That would be my preferred way.)

---

### Post by Frogs Hair on 2012-06-28
It's possible to resolve dependency problems with the synaptic GUI under Edit.Unity 5.10 is not even listed in synaptic and I suspect it is due to the problem you are currently facing.

---

### Post by AleveSicofante on 2012-06-28
As a matter of fact, after some research I was able to ask Synaptic to "force" an older version. I was offered 5.10 and Synaptic took care of the dependencies.

Unfortunately, I had tweaked the desktop before doing this and maybe some of the tweaks where incompatible with 5.10. As a result, my system is borked now.

I'm on my quest to reset the destop to its default values using some recovery boot. Any suggestion?

:(

UPDATE: Actually what happened is that forcing the 5.10 version under Synaptic simply uninstalled unity completely (WTF?). That's why I wasn't getting anything on my desktop. I reinstalled Unity, but it's 5.12 again. Now I'm back to square one. Frustrating.

---

### Post by Frogs Hair on 2012-06-29
The dependency problem probably couldn't be resolved.In that case a package that needs to be installed can't because of the presents of another package . It's catch 22 which usually ends in removal of the package. There is new information in the bug report you posted,   see post 22.

---

### Post by AleveSicofante on 2012-06-29
Thanks Frogs Hair. I'll try the proposed patch.

---

