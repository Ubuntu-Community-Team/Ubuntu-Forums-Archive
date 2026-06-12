---
title: "Can't print from Lucid Lynx"
date: 2010-07-15
forum: General Help
---

### Post by dluzius on 2010-07-15
Ubuntu 10.04 is unable to set up my Canon Pixma IP 6000D printer.
So earlier tonight when my wife wanted 2 recipes she saw on this am's Today Show, I had to restart my computer with a Fedora 13 live CD in the drive. F13 quickly installs my Canon printer and I am able to print the recipes.
But this sure is a convoluted way of printing 2 short text files.
Please somebody tell me how , step-by-step, to get my printer to work with Ubuntu.

I've been using Ubuntu almost 2 years now, and love it, love it, love it, except for this one little thing.
Please help me, please.
           Dave

---

### Post by techunit on 2010-07-16
Make sure you are updated there was some sort of problem with CUPS earlier on but it seems to have been fixed in an update... Make sure you are completely up to date.

---

### Post by ibates on 2010-07-18
The topic heading is not quite accurate for my difficulty, although I am using Ubuntu 10.04 LTS.

I have installed all the downloaded software from the Canon Australia site for installing my Canon PIXMA MP640.  Everything installed just fine, and the printer operated flawlessly - until yesterday. Now the system seems unable to connect with the printer.

Although there is a USB icon in "Computer" labelled Canon MP640 Series, and the MP scanner operates perfectly normally using the Canon software downloaded and installed at the same time as the software for the printer function, it seems the printer has disappeared.

System->Preferences->Default Printer shows no printer.

System->Administration->Printing shows no printer, and further, all options are greyed out.

The system is completely up to date (checked).

Any ideas what might be going on?

In the meantime it is back to Windows again.  If printing cannot be done from Ubuntu, then why even boot it up?

---

### Post by ibates on 2010-07-18
A reply to a similar question on this forum solved the particular problem for me.

The advice given was:

sudo service cups restart

This worked for me and I once again had full printing capability with the Canon MP640 Series.

I no longer have a printing problem.

---

