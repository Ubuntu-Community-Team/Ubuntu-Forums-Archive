---
title: "Apt pinning quick question"
date: 2010-09-13
forum: General Help
---

### Post by rolandpish on 2010-09-13
Hi.

I added an apt pinning in my /etc/apt/preferences:

Package: geany
Pin: release a=lucid-getdeb
Pin-Priority: -1

However, if I replace the first line with: Package: geany* the apt pinning is not applied.

How can I do a "multi-package" apt pinning entry like geany*? (Note that I'm not meaning the "all packages" line: Package: *)

Another question, in "release" line, I've seen the use of "a", "o"... what does these letters stand for and which are the allowed letters for this line?

Thanks!

---

### Post by bodhi.zazen on 2010-09-13
No, you can use either a * or you need to specify each package. You can list packages separated by white space.

Package: foo foo-bar bar another-package

See : 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2202850.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2202850.html)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=121132](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=121132)

---

### Post by rolandpish on 2010-09-13
> **bodhi.zazen said:**
> No, you can use either a * or you need to specify each package. You can list packages separated by white space.

Package: foo foo-bar bar another-package

See : 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2202850.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2202850.html)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=121132](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=121132)

Thanks for your reply bodhi.zazen. It's very good to know that I can specify several packages in the same line.

Regards.

PS: how can I mark this thread as solved?

---

### Post by bodhi.zazen on 2010-09-13
Glad that worked for you =)

At the top -> Thread tools -> mark this thread as solved

---

### Post by dcstar on 2010-09-14
> **rolandpish said:**
> Hi.

I added an apt pinning in my /etc/apt/preferences:
.........

Be very aware that some Pinning in Ubuntu is ignored by any "Upgrade" process offered. Pinning something in Synaptic does not mean that it will survive an Upgrade, only the regular Updates that occur.

I'm not sure if the direct APT Pinning survives this sort of thing.

---

### Post by JoelOl75 on 2010-09-14
> **dcstar said:**
> Be very aware that some Pinning in Ubuntu is ignored by any "Upgrade" process offered. Pinning something in Synaptic does not mean that it will survive an Upgrade, only the regular Updates that occur.

I'm not sure if the direct APT Pinning survives this sort of thing.

This is true, a simple and very effective method I use is to symbolically link, such as:

sudo ln -s /usr/lib/synaptic/preferences /etc/apt/preferences

This way, you can use synaptic to "Lock Version" and dropping to a terminal and doing an apt-get upgrade will honor locked packages from the GUI.  I think this would be a good default behavior but it's not followed.  This lends to much confusion as packages "locked" in Synaptic will be overwritten by a newer version if you use the terminal commands.

---

### Post by rolandpish on 2010-09-14
Oh, ok, I'll better add that symbolic link.

Thanks for your tips!

---

### Post by salvage0989 on 2010-09-14
i just upgraded my 10.04 ubuntu to 10.10 but i cannot get it to start 

it came up with 
user 
password 

got tue wit that part but i don't know wat to do next

---

### Post by emarkay on 2010-10-05
> **dcstar said:**
> Be very aware that some Pinning in Ubuntu is ignored by any "Upgrade" process offered. Pinning something in Synaptic does not mean that it will survive an Upgrade, only the regular Updates that occur.
I'm not sure if the direct APT Pinning survives this sort of thing.


Encountered this recently  in "Recovery Console" , and info added to bug:
[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222)
Subscribe to this one to keep updated.

---

