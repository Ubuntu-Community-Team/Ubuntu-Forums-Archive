---
title: "chkrootkit, wtf"
date: 2011-12-03
forum: General Help
---

### Post by snoninja on 2011-12-03
Am a bit concerned after getting packages from backtrack repository. I mean, who wouldn't want to install rootkits on the users of backtrack 5, lol. Still, chkrootkit won't start. Says it's updated and installed, but when I try to run it, it says it's not installed.. Going to try removing and reinstalling. But wtf. Could a rootkit disable local defenses causing chkrootkit not to run? Any advice is welcome...

---

### Post by Dangertux on 2011-12-03
> **snoninja said:**
> Am a bit concerned after getting packages from backtrack repository. I mean, who wouldn't want to install rootkits on the users of backtrack 5, lol. Still, chkrootkit won't start. Says it's updated and installed, but when I try to run it, it says it's not installed.. Going to try removing and reinstalling. But wtf. Could a rootkit disable local defenses causing chkrootkit not to run? Any advice is welcome...

...

Okay -- so rootkits , yes they can disable whatever they want if they are effectively installed on a system. Still, that's probably not what happened. A lot of Back Track's packages are custom compiled, and not from repositories , thus they may not have necessarily made it into your path. You need to explicitly execute it as such.

```

/pentest/forensics/chkrootkit/chkrootkit -x

```

Also -- since you said any advice is welcome, my advice is avoid Back Track until you know more about how Linux and Security principles work.

Hope this helps.

---

