---
title: "SOLVED: Upgrading Liferea / Libwebkit"
date: 2009-07-13
forum: General Help
---

### Post by paradigm2 on 2009-07-13
Hello I put in the special PPA's to from the webkit team for both Liferea and webkit.  However when  try to upgrade Liferea I am told:

```

liferea:
 Depends: libwebkit-1.0-2 but it is not going to be installed
 Depends: liferea-data but it is not going to be installed

```

I am using these PPA's on Jaunty:

[https://launchpad.net/~liferea/+archive/ppa](https://launchpad.net/~liferea/+archive/ppa)
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa) (for libwebkit)

However when I search for libwebkit all I see is Libwebkit-1.0-1 (which is installed).  I see no Libwebkit-1.0-2.

**** Actually as I type this I figured it out but will leave it up for anyone else who has an issue!

My mistake?

I accidentally left the repository reference as "karmic" when I had Jaunty, thus it was not wanting to upgrade libwebkit.

For new people and those having issues, check your deb references!

---

