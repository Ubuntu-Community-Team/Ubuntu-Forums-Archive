---
title: "two hp printers, one with s scanner, only one recognized,  scanner has never worked"
date: 2010-02-08
forum: General Help
---

### Post by w.g.hanna on 2010-02-08
i have two hp printers.  one is a laser printer and it has never given me a problem.  the other is an hp f4480 desk jet multi function.  my jaunty system recognized the desk jet as a printer - not so as a scanner.

i went to hp's site, and the site for hplip indicated it should work with ubuntu.  so i downloaded it, and ran it from a terminal (something i'm not very good at unless i have very good instructions).  

it didn't seem to work.  instead, it seemed to make things worse.  when i clicked xsane, still no scanner.  however, when when i printed to the laser printer from open office, all that printed was an error page.

i just did a clean install to karmic - it was time to start over for a number of reasons . . . . . 

so i want to finally get both printers and the scanners to work.  i'm nervous about downloading and running hplip again.  i did some hunting in the forum, and one poster reported success on a different (but related) scanner model by downloading hplip using synaptic.  they said they then got an application launcher for hplip in the menu and that it works.  

so, my question for those in the know:  does downloading it from synaptic make losing the laser printer less likely.  does it make using the scanner more likely?  any tips from experience on how to get it running?

---

### Post by w.g.hanna on 2010-02-08
oh yeah - the guy that had the success downloading posted a long time ago.   probably running gutsy, maybe hardy.

---

### Post by ajgreeny on 2010-02-08
You need hplip v 3.9.6, so check which version you already have in hardy.  You may find that
it is not recent enough, 2.8.2, I think, so you will have to update to the one on the hplip site. That version is known to work on hardy, so the site says, so get it and try it from here.
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

