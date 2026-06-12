---
title: "how does Ubuntu deal with broken packages?"
date: 2011-02-03
forum: General Help
---

### Post by mahela007 on 2011-02-03
I read somewhere (on these forums) that broken packages are uninstalled the next time Ubuntu starts up. Is that true?

---

### Post by kpkeerthi on 2011-02-03
What exactly is a 'broken package' by your definition?

---

### Post by mikewhatever on 2011-02-03
Don't think so, since broken packages can't be installed in the first place. You usually need to run 'sudo apt-get install -f', otherwise they just sit there.

---

### Post by Frogs Hair on 2011-02-03
If broken packages can't be installed Why does the Synaptic Package Manager have a functions for isolating and repairing broken packages ?

Is this for packages that are broken prior or after installation only ?

---

### Post by mahela007 on 2011-02-03
> **kpkeerthi said:**
> What exactly is a 'broken package' by your definition?

A package that has unmet dependencies.

@ Mike
Could you please elaborate on what you mean by 'just sit there'? Are they installed even through you can't use them?

---

### Post by mikewhatever on 2011-02-03
The package remains in /var/cache/apt/archives, and you get a message about a broken package every time you use the package manager.

---

### Post by mahela007 on 2011-02-03
So no files get copied into the installation directories ? (sorry if I seem persistent. I'm dealing with some printer drivers and I want to make sure they're all gone before I try reinstalling. ) EDIT: What if I force an installtion using dpgk -ignore-depends?

---

