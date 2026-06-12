---
title: "Upgraded to Maverick, got Natty?"
date: 2010-12-28
forum: General Help
---

### Post by dm_ntm on 2010-12-28
I upgraded by 10.04 to 10.10 using the instructions on the following page:

[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)

(Basically, just changing Release Upgrade from "long term" to "normal" and getting updates.)

The upgrade went fine, but now when I go to System > About Ubuntu, I read:

> You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.

I do not want a pre-release-bleeding-edge distro on this machine. What is going on? Did I do something really wrong? Is the About page simply out-of-sync? Is this a (rather severe) bug? Time travel miracle?

Is there a way to tell what version I am really on, assuming the About page is incorrect?

---

### Post by howefield on 2010-12-28
It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```

---

### Post by dm_ntm on 2010-12-28
> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick


Looks like we are good then ... that bug does look like the same thing. (Funny a Google search didn't pull that up before I posted.) Thanks for the help!

---

### Post by howefield on 2010-12-28
> **dm_ntm said:**
> Looks like we are good then ...

Yep, you don't have a pre-release-bleeding-edge distro on your machine.  :)

> Thanks for the help!

You're welcome.

---

