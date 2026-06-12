---
title: "Trash / Delete / Uninstall / Remove all PEAR?"
date: 2012-08-24
forum: General Help
---

### Post by dotchristopher on 2012-08-24
Hi All,

Sorry to ask another question so quickly, but I've had no luck (although generous support) asking in the PEAR forums.

I've got a very broken PEAR install- apt has lost track,* PEAR itself doesn't know what/which channels/roles/files are actually installed and available (i.e. present on the filesystem^)... not quite sure how I got into this situation but there you are...


Could anyone ***please*** tell me how to (or where I should look to) remove *every file* associated with PEAR, so that I can go back to the good old apt-get install PEAR thinking it's never been installed before (not worried that apt knows it's a "previously selected package!)?

Any suggestions or comments are most welcome- though I doubt you'll manage to fix the PEAR installation you can try and I'll supply some info... a clean start is preferred ;)

Thanks! 

*(apt-get remove will fail, --purge doesn't trash enough files- e.g. afterwards PEAR still knows it has channels 'installed', pear show-config gives system conf file as /etc/pear.conf but it's actually /etc/pear/pear.conf < although using the -c [config file] toggle doesn't work either!)
^(if it thinks it knows a role is installed it seems to gamble/assume, then crashes out with file not found/role not installed correctly)

---

