---
title: "GRUB Editor"
date: 2010-02-21
forum: General Help
---

### Post by physic.dude on 2010-02-21
[COLOR=black][FONT=Verdana]When I turn on my computer and get GRUB selector I have many different entries related to ubuntu and simply 2 for Windows XP. I know that 2 more appear at every update for ubuntu and are used incase something fails. Anyway I am asking if someone could tell me what I need to do to remove some of them. I am not sure how to use the GRUB editor so I need help with it. [/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by oldos2er on 2010-02-21
Which version of Ubuntu are you running?

You can use Synaptic Package Manager to uninstall kernels you no longer need. Search for 'linux-image' packages.

---

### Post by ajgreeny on 2010-02-21
Yes, search in synaptic for 2.6.31 if using karmic or 2.6.28 if using jaunty, and then uninstall al but the last two versions on your machine.  That will also remove them from the grub menu and release about 173MB per kernel removed, by the time you have got rid of all the ancilliary packages for each kernel.

Always keep one previous kernel that you know works just in case anything goes wrong with the newest; not likely, but it does occasionally happen.

---

