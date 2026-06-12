---
title: "Update Manager problem"
date: 2010-10-23
forum: General Help
---

### Post by compmom on 2010-10-23
When I use Update Manger I have this problem.  It says for me to install a meekrat 10.10 cd to continue.  I am using Netbook 10.04 and don't have cd requested and don't want to upgrade to it either.  But then when I press cancel it quits and doesn't update all the other items.  Suggestions?

---

### Post by luisito on 2010-10-23
Does it let you interact at all? It seems that you have the CD enabled as a software source. If you are able to get to the point where Update Manager lets you click on "Settings", go to "Other Software" and uncheck the CD.

If you cannot run Update Manager at all, go to System->Administration->Synaptic Package Manager, Then go to Settings->Repositories and do the same thing described above.

In the software sources dialog, you want to have at least the first two options in the "Ubuntu software" tab checked. The same for the "Updates" tab. In the "Other software" tab keep checked "partner" and only the other ones you may recognize as useful.

Make sure you are connected to the internet. Hopefully it will help.

---

### Post by orangemoose on 2010-10-23
> **compmom said:**
> When I use Update Manger I have this problem.  It says for me to install a meekrat 10.10 cd to continue.  I am using Netbook 10.04 and don't have cd requested and don't want to upgrade to it either.  But then when I press cancel it quits and doesn't update all the other items.  Suggestions?

I think the problem is that the CD source is checked in your sources list.

Ubuntu Software Center->Edit->Sources

HTH

---

