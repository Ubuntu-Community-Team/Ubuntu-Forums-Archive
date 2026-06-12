---
title: "Upgrading software on unsupported old Ubuntus"
date: 2012-01-24
forum: General Help
---

### Post by Hylas de Niall on 2012-01-24
Here's the thing: I have an old laptop onto which i want to put an older version of Ubuntu. I have iso's of 6.1, 6.06.1, 7.04 and 7.10 and want to use one of them.
Is it possible to update the browsers and other software for these releases to more recent versions via ppa's, or would there be issues with the kernel(s) and/or dependencies?

---

### Post by QIII on 2012-01-24
Each of those has long since reached end of life and is no longer supported.  You won't find repos for them.  Using a hodge-podge of PPAs would probably be a disaster.

If low specs are a problem, use Xubuntu or Lubuntu.  If you don't mind a somewhat adventurous minimalistic route, you might give Bodhi a try.  I put it on a PIII w/ 512 and it works like a charm.

---

### Post by snowpine on 2012-01-24
The recommendation for older hardware is to use a currently-supported "lightweight" distro (Lubuntu, Xubuntu, AntiX, Puppy, SliTaz, Tinycore, etc) rather than an old, unsupported Ubuntu release. If you tell us your hardware specs, you will get some good recommendatons I'm sure. :)

To answer your specific question: no, third-party PPA packagers do not typically waste time updating their PPA's for releases that are "end of life."

---

### Post by Hylas de Niall on 2012-01-24
> **QIII said:**
> Each of those has long since reached end of life and is no longer supported.  You won't find repos for them.  Using a hodge-podge of PPAs would probably be a disaster.

If low specs are a problem, use Xubuntu or Lubuntu.  If you don't mind a somewhat adventurous minimalistic route, you might give Bodhi a try.  I put it on a PIII w/ 512 and it works like a charm.

Yep, I know the repos are all closed for these releases, and i'm well aware of Xu and Lu, and Bodhi (have tried all successfully on the machine), but i really want a vanilla Gnome Ubuntu on there so that i'm a little more savvy finding my way around it.

I suppose it's mainly the browser that i'd want up to date, do you think just that one ppa would break it?

---

### Post by snowpine on 2012-01-24
You can always download the latest version of Firefox for any Linux distro (supported or unsupported) from:

[http://firefox.com](http://firefox.com)

This does not change my recommendation to use a supported release. :)
If you are looking for a traditional Gnome 2 desktop then 10.04 is your best choice (and it will be supported through April 2013, plenty of time to save up for a new computer ;)).

---

### Post by Frogs Hair on 2012-01-24
I think dependencies will be a problem  even if a PPA is used . Finding maintained  PPAS that still support older version may be possible but unlikely . I would find out if the computer can run 10.04 or  newer versions of Ubuntu . You would have to have access to the Ubuntu old repositories to install any programs and the update manager would be pretty much useless .

[]("http://soniahamilton.wordpress.com/2...ons-of-ubuntu/")

---

### Post by JKyleOKC on 2012-01-24
The only way to know for sure would be to try it and see. The danger of using a no-longer-supported distribution is that you get absolutely NO security fixes for it. Every kernel upgrade brings with it a new libc system library upgrade to match, which means that current versions of things like Firefox may use library calls that are not compatible with the out-of-date system.

I can run Xubuntu 10.04, the current LTS release, on an old box with an AMD K6 CPU and only 256 MB of RAM. It's slow, but (barely) usable. I can even run VirtualBox on that system. There's at least another year of support for this version, so it could be a solution for you. The interface of Xubuntu isn't all that different from basic Ubuntu, but it doesn't have all the bells and whistles.

If you, however, want to stay with something like 7.04 Feisty Fawn, you can always try downloading applications in source form from the developers' own sites rather than from the repository, and compiling them for yourself (install the "build-essentials" package to make this possible). This should detect dependency problems if they occur, and might be the ultimate solution for you even though it's an approach that's usually discouraged since it leaves all responsibility for security up to you alone.

---

### Post by Hylas de Niall on 2012-01-24
Thanks to everyone for the info :)

The old lappy would be more for tinkering around with, and some browsing than for heavy, everyday use.

Specs for the machine are OK for the LTS, but only just, so i'm more keen to run an older version in the hopes of getting a snappier system.

I'll probably have a crack at Dapper, and see if the drake wants to fly!
:D

Thanks again!

---

