---
title: "meld not working as well after upgrade to Lucid"
date: 2010-05-10
forum: General Help
---

### Post by tfotherby on 2010-05-10
Since upgrading from Ubuntu 9.10 (Karmic) to 10.04 (Lucid Lynx) meld has been inaccurate when highlighting the differences between two files.

If I run "meld file1 file2", it highlights roughly the right line but is often one wrong and so when you try to merge the files, it all gets in a mess. Basically, for me at least, Meld is broken in Lucid.

Does anyone have the same problem? Know a fix?

I downloaded some previous releases of Meld and found the same problem still occurs. So perhaps the problem is not with Meld but with some library that Meld uses that has changed in Lucid?

I have filed a bug: [#578121]("https://bugs.launchpad.net/ubuntu/+source/meld/+bug/578121") (includes example screenshot)

---

