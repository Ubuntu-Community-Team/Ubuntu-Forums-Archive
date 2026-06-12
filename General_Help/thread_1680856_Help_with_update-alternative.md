---
title: "Help with update-alternative"
date: 2011-02-03
forum: General Help
---

### Post by snimavat on 2011-02-03
I am trying to make update-alternatives work with two different version of grails.

I have grails-1 installed (extracted from zip) at ~/work/grails-1/
and grails-2 installed (extracted) at ~/work/grails-2/

Now I want to have ability to choose between the two grails version. can any one explain how can I do this with update-alternatives

---

### Post by mcduck on 2011-02-03
Sorry, but the update-alternatives only works with packages installed through the package management, not with things you install manually. (Manually installed packages don't provide any information required for this kind of things, from the system's point of view they are just some files somewhere in the filesystem)

---

### Post by tredegar on 2011-02-03
Either give the full path to the version you want to run, each time, or you could make a symlink in **/usr/bin** (or somewhere else on your $PATH) that points to the one you wish to be the default, so that is the one that runs if you just type **grails**

---

