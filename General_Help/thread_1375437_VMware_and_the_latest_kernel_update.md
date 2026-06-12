---
title: "VMware and the latest kernel update"
date: 2010-01-07
forum: General Help
---

### Post by sefs on 2010-01-07
I just got a kernel update 2.6.31-17.  Vmware needs to recomiple the drivers but I keep getting the below msg.

```

Could not grab your mouse.

A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus.

Try again.

```

What is that all about.

---

### Post by running_rabbit07 on 2010-01-07
When you enter the ```
w
``` are you the only user shown?

---

### Post by sefs on 2010-01-08
Yes.

I kept trying and the problem seems to have went away by itself.  So not too sure what is going on.

It seems to be an intermittent problem and annoying one.

---

### Post by sefs on 2010-02-05
This problem is back with the new kernel update.

But it was solved by running the module update command from the command line.

The command-line was given to me by a nice person over at the vmware forums.

It is.

```

sudo /usr/bin/vmware-modconfig --install-all --console

```

---

