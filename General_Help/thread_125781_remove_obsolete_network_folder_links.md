---
title: "remove obsolete network folder links"
date: 2006-02-04
forum: General Help
---

### Post by harty83 on 2006-02-04
Howdy,

Any clue on how to remove obselete network folder links from Remote Places under kde?

Alan

---

### Post by dcstar on 2006-02-04
[QUOTE=harty83]Howdy,

Any clue on how to remove obselete network folder links from Remote Places under kde?

Alan[/QUOTE]
You will probably get a quicker answer by posting the question in the Kubuntu forum, not the Gnome one.

---

### Post by ndak on 2007-06-25
> **harty83 said:**
> Howdy,

Any clue on how to remove obselete network folder links from Remote Places under kde?

Alan

Alan or Anyone Please,

I have the same problem in Feisty - - - can anyone point me in the right direction?

Thanks,

Dennis

---

### Post by harty83 on 2007-06-25
Hi Dennis,

I figured it out.  There is a desktop file in ~/.kde/share/apps/remoteview for each server you set up.  Delete the file for the specific server and it no longer shows up in remote:/

Alan

---

### Post by OldGaf on 2007-09-03
Good one!
I have been looking for this answer too.

---

### Post by sirfinished on 2007-09-12
Here is  workaround I found.
switch to tree view
right click and choose >move to > Home folder
you can then go to your home folder and delete the file.
This worked for me on Kubuntu 7.04.  
Here is the link I found it on.
 [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/28031](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/28031)

---

