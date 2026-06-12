---
title: "can I toggle between versions of wine?"
date: 2010-07-19
forum: General Help
---

### Post by d3v1150m471c on 2010-07-19
Is there some way to have both wine 1.0 and wine 1.2 installed. I ask because somethings run better or not at all on certain versions and having to install a different one if i get in the mood to use a certain piece of software is slightly redonculous. thanks in advance.

---

### Post by d3v1150m471c on 2010-07-24
bump

---

### Post by bodhi.zazen on 2010-07-25
> **d3v1150m471c said:**
> Is there some way to have both wine 1.0 and wine 1.2 installed. I ask because somethings run better or not at all on certain versions and having to install a different one if i get in the mood to use a certain piece of software is slightly redonculous. thanks in advance.

No easily.

You can keep the .deb for the various versions and purge then install to switch between versions.

The phenomena you are experiencing is often termed "regression" , with each version of wine it seems some things work, and others break. Part of why wine can be frustrating.

The more complex your application, games in particular, the more likely you are going to have problems between versions of wine.

---

### Post by d3v1150m471c on 2010-07-25
ah but that's what i was afraid of. currently that's how i switch them around aside from the full purge. the configuration doesn't effect my applications, rather the version of wine itself. I'm going to go out on a limb and see if i can just copy the executables from /usr/bin themselves, rename them according to version, and then see if launching things via command line will allow me a "duct-taped" fix for this sort of thing. thanks for the reply, bodhi. I'll let you all know how it works out.

---

### Post by d3v1150m471c on 2010-07-28
we'll that failed miserably lol. But...I figured it out, though.
```

sudo apt-get install playonlinux

```

It will allow you to toggle and download various versions of wine with significant ease. very nice application.

---

