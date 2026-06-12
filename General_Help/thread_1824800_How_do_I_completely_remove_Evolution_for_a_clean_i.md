---
title: "How do I completely remove Evolution for a clean install?"
date: 2011-08-14
forum: General Help
---

### Post by JRPettus on 2011-08-14
I think I'm in love with 11.04 Natty Narwhal.  But I ran into a problem with evolution.

I'm running it on a Toshiba Satellite laptop.  After getting the OS installed and configured evolution, I did a backup of the evolution on my desktop version of 10.04 and attempted to restore it to evolution on my laptop and while it did seem to work, it became corrupted and now won't load.

I uninstalled multiple times and reinstalled to get the same problem.  I also removed a number of folders trying to get a clean install but ran into the same problem as soon as restored again.  

How can I completely remove evolution so that I can get a truly clean install where the wizard comes up for set up again once I open it for the first time?

---

### Post by HereInOz on 2011-08-14
Have you deleted the .evolution folder in your home folder?  If you don't remove that one, it will always come back with the same settings again.

You will have to press CTRL + H to see the .evolution folder.

---

### Post by merry_meerkat on 2011-10-24
Hello, 
a related question. I have upgraded to 11.10 Oneiric and subsequently removed evolution - or more precisely, I removed the package "evolution".

However, when I search for "evolution" in synaptic I see a bunch of things that are still installed. This includes the packages "evolution-common", "evolution-data-server", "evolution-webcal", etc. --> please see screenshot below.

I was wondering which of these packages I can safely remove and which I shouldn't touch because other parts of the system make use of them.

Is there anyone who can enlighten me?
Thanks.

---

