---
title: "K3B - vcdxbuild returned an unknown error (code 1)"
date: 2009-11-22
forum: General Help
---

### Post by davidjmayo on 2009-11-22
Hi all,

I'm trying to burn a VCD with K3B and get the error in the thread title.
There is no other problem with K3B - I can burn a data CD.

A quick google shows this is a problem but no thread has a solution.

K3B burned VCDs fine in 9.04 this problem is with 9.10.

I did find a work around using DeVeDe to create the cue/bin files but it takes ages compared to K3B. Also the quality of the VCD was pretty poor (the quality was OK before with K3B considering the video comes from a digital camera)

Any help would be greatly appreciated

---

### Post by lpetersen on 2009-12-21
Hi, I had the same problem and just found a solution on the German ubuntuusers.de Forum:

You have to specify a user-supplied parameter to vcdxbuild, namely --filename-encoding=iso8859-1

From the main menu, choose Settings -> Configure k3b, then select the "Programs" tab, within the dialog activate the "User Parameters" sub-pane, and enter "--filename-encoding=iso8859-1" in the "Parameter" field next to "vcdxbuild".

This worked for me. Good luck, and let me know if it works for you, too.

---

