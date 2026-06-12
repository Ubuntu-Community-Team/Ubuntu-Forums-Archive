---
title: "Java update?"
date: 2010-01-28
forum: General Help
---

### Post by duthieamber on 2010-01-28
How do i get the newest version of Java? I have 1.6.0_0 but I need the newest version in order to do something. Can somebody please help me I am new to Ubuntu so im not really sure on how to do everything. Thanks in advance and I hope this is easy to do:)

---

### Post by gradinaruvasile on 2010-01-28
For the latest java ( 1.6.0.18 ) there is a PPA:

[https://launchpad.net/~voronov84/+archive/andreyv/+packages](https://launchpad.net/~voronov84/+archive/andreyv/+packages)

Read the installation instructions by clicking on the "Technical details about this PPA"

---

### Post by doas777 on 2010-01-28
usually that is not done in ubuntu, but there may be ways to accomplish it. one option is to enable the backports in your System->Administration -> Software Sources applet. then just run synaptic or software center, to update your lists, and soon an update window should pop up. I'm not sure if there is a backport for the latest jdk though.

another option is to download it directly from sun. this can be more complicated and is not officially supported so there may be complications.

I do some java development, but have never needed to get a newer jre/jdk than comes by default.

good luck

---

