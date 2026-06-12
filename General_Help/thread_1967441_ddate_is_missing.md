---
title: "ddate is missing"
date: 2012-04-28
forum: General Help
---

### Post by Chronon on 2012-04-28
After upgrading to 12.04 I find that ddate is missing.  Searching for ddate on launchpad doesn't return anything, though the string is apparently mentioned in i3status.

Anybody have a clue on what happened to it or how to get it back?

---

### Post by Chronon on 2012-04-29
Apparently it is missing from the Precise version of util-linux.  (It's there in the Oneiric package.)

---

### Post by RSparker on 2012-05-01
As you probably know, or maybe not, ddate has a long and checkered history. If you want a bit of context look through the util-linux Debian package [changelog]("http://changelogs.debian.net/util-linux"). You'll find gems such as this:

```
* Drop ddate.  Closes: #149321, #174459, #180737
```

Bug [#149321]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=149321") is a famous one and represents the core of the problem, i.e. some people with dubious moral compasses are easily offended by fictional/satirical religions. Needless to say common sense prevailed and ddate was put back in on the next version.

But a while ago it was nipped in the bud (upstream) when someone at Red Hat made building it [optional]("https://git.kernel.org/?p=utils/util-linux/util-linux.git;a=commit;h=4a8962f3a7cb970b28add7d770528edebbe03635"):

```
build-sys: add --enable-ddate

Don't build this crazy thing by default.

Signed-off-by: Karel Zak <kzak@redhat.com>
```

Nice.

So there you have it, you now have to build util-linux with --enable-ddate to get it. I think I'll start to separate distros on the basis of whether or not they use this flag when building the package.

---

### Post by Chronon on 2012-05-02
Thanks for the reply!  Yes, I knew that there had been some attempts to remove it in the past.

Do you think a bug report would do any good or is its absence intentional by Ubuntu?

---

### Post by RSparker on 2012-05-02
I don't believe it was intentional, the build defaults just changed and the maintainer probably doesn't use ddate so it went unnoticed.

There's already a bug ([#988925]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/988925")) open on launchpad which I updated with the information I mentioned previously.

---

### Post by Chronon on 2012-05-11
Thanks for all of the useful information.  I successfully built my own util-linux with ddate enabled.  Hopefully this gets fixed in Ubuntu's repositories soon.

I'll mark this thread as solved, since I have recovered ddate on my system and the ultimate resolution of the problem depends on action taken on the bug report.

---

### Post by lisati on 2012-05-11
> **Chronon said:**
> Thanks for all of the useful information.
+1. For a moment, I had memories of a similarly named MS-DOS utility that performed an almost entirely unrelated function, and needed to look it up!

---

### Post by frankob on 2012-06-19
I have solved this by installing the Debian package of util-linux, as the ddate flag seems to be the only difference with the Ubuntu one.
But this crazy inquisitor at Fedora/Red Hat/upstream (Karel Zak) has serious intentions of removing ddate whatsoever in the future... [http://osdir.com/ml/fedora-devel-list/2011-08/msg01725.html](http://osdir.com/ml/fedora-devel-list/2011-08/msg01725.html)

We must stop them!
Hail Eris!

---

