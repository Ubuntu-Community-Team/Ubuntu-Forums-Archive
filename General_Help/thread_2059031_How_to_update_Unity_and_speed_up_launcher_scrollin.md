---
title: "How to update Unity and speed up launcher scrolling"
date: 2012-09-17
forum: General Help
---

### Post by firekage on 2012-09-17
Hi.

I've checked over internet and i haven't found solution yet. My question is: how to update Unity? In synaptic i have version 5.xxx but i know that version 6.xxx for 12.04 contains few fixes, i especially want this one:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/906072](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/906072)

In unity 2D scrolling launcher with apps is much way faster, while on unity 3D is so slow that in fact it is not useable - i had to install cairo-dock in order to have full functioning desktop with Unity interface.

Could you tell me how to either speed up launcher scrolling and update Unity?


Thanks.

---

### Post by Cheesemill on 2012-09-17
What version of Ubuntu are you using?

---

### Post by firekage on 2012-09-17
> **Cheesemill said:**
> What version of Ubuntu are you using?


Ubuntu: 12.04.
Unity: 5.16.0

---

### Post by Cheesemill on 2012-09-17
Unity version 6.xx is only available on Ubuntu 12.10.

You need to wait for about a month until 12.10 is released and then upgrade your system, the repositories for Ubuntu 12.04 will only ever have the 5.xx branch of Unity.

[http://packages.ubuntu.com/search?keywords=unity&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=unity&searchon=names&suite=all&section=all)

---

### Post by firekage on 2012-09-18
> **Cheesemill said:**
> Unity version 6.xx is only available on Ubuntu 12.10.

You need to wait for about a month until 12.10 is released and then upgrade your system, the repositories for Ubuntu 12.04 will only ever have the 5.xx branch of Unity.

[http://packages.ubuntu.com/search?keywords=unity&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=unity&searchon=names&suite=all&section=all)

Thanks.

I would like still to know is there a way to upgrade one software to a new version without changing system version?

---

### Post by MG&amp;TL on 2012-09-18
> **firekage said:**
> Thanks.

I would like still to know is there a way to upgrade one software to a new version without changing system version?

There is a [Unity PPA]("https://launchpad.net/~unity-team/+archive/ppa") but this may (and probably will) break things. If you're prepared for breakage, this is how you get an updated Unity.

---

### Post by Cheesemill on 2012-09-18
> **MG&TL said:**
> There is a [Unity PPA]("https://launchpad.net/~unity-team/+archive/ppa") but this may (and probably will) break things. If you're prepared for breakage, this is how you get an updated Unity.

This PPA only contains the current versions of Unity that are supplied with the standard repositories and nothing newer, you can't update Unity by using it.

As I said earlier, if you want a version of Unity that is > 5.10.0 then your only current option is to upgrade to 12.10.

---

### Post by MG&amp;TL on 2012-09-18
> **Cheesemill said:**
> This PPA only contains the current versions of Unity that are supplied with the standard repositories and nothing newer, you can't update Unity by using it.

As I said earlier, if you want a version of Unity that is > 5.10.0 then your only current option is to upgrade to 12.10.

Derp. My bad, sorry OP.

---

### Post by serdotlinecho on 2012-10-23
Hey, i found this ppa...maybe you can get your hands dirty a little bit by adding this unity backport on ubuntu 12.04 :guitar:

[https://launchpad.net/~benkai/+archive/precise-unity-backport](https://launchpad.net/~benkai/+archive/precise-unity-backport)

---

