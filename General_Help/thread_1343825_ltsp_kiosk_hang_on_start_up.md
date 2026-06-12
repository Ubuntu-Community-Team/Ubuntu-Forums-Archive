---
title: "ltsp kiosk hang on start up"
date: 2009-12-02
forum: General Help
---

### Post by rolfm on 2009-12-02
kiosk setup hangs on start up

i'm working on a multi-screen installation -
every screen is driven by a disk-less, interaction-less client.

my system consists of Ubuntu 8.10 and LTSP 5.
the client image is build with the 'standard' kiosk script.

it took me some time, but with a few tweaks and tricks,
i got the installation running:
each client using a 'local' firefox + flash plugin,
which automatically starts at the end of the loading process,
expanding to full screen without disturbing questions.


the first 'hang-problem' occurs when the clients are powered up at the same time.
some of them will hang forever during the loading of the client image.

the second 'hang-problem' occurs
when i switch from NBD to NFS (following the "LTSPwithoutNFS" webpage).
(this to be able to change parameters for the clients when the installation is running).

the booting of the client goes well 
until the sand-colored screen (of the Human-theme) appears and stays empty.

when i plug in a mouse and move the cursor: the client continues!

if anybody has a suggestion i would be gratefull

rolf meesters

---

