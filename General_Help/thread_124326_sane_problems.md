---
title: "sane problems"
date: 2006-02-01
forum: General Help
---

### Post by pbb on 2006-02-01
Hi,

I had some problems with my scanner on the default installed sane in Ubuntu 5.10. I saw on the sane/avision site that there had been updates, so I thought to temporarily activate the Dapper repository and check what is in there.

There was a new sane version in the Dapper repository, so I installed that. After that however, the xsane icon from Applications > Graphics had gone, and when starting xsane from the terminal I got a windows with the error "No deviced available".

Now I thought I could just un-install sane, and try a different approach. However, when I want to uninstall sane through synaptic, it says it also needs to uninstall ubuntu-desktop! Checking the dependencies, I see indeed that ubuntu-desktop depends on xsane. Now, I am really just a newbie at this, but it seems to me that uninstalling ubuntu-desktop is something I should NOT do? Or am I misunderstanding things? How could my desktop be dependend on the availability of a scanner program??

Can anybody help me any further?

---

### Post by noigeaR on 2006-02-01
in synaptic you could try to force the installation of the old (breezy) version of the sane package.
select the sane package and choose package-->force version (or press ctrl+e)
then select the older version of the sane package.

---

### Post by pbb on 2006-02-01
I've managed to uninstall the newer version, and re-install the original version. But I've still got the same problem that I got after upgrading (scanner not found). Ah well, it wasn't properly working anyway....

---

