---
title: "Accidentally changed hostname!  Please help ASAP!"
date: 2006-01-29
forum: General Help
---

### Post by DisposableHero on 2006-01-29
Hello.  I was toying with the network connections and settings in Ubuntu while attempting to get my internet to work either via ethernet or my atheros wireless.  Well, in the process, I accidentally renamed the hostname of the computer to where it is just blank. :(  I cannot change it back because when I go to the System>Administration menu, it does not load...I assume this is due to my error.  Please give me commands to type in terminal or recovery mode that will fix the hostname back to my original or where I can set it.  Or should I just completely reinstall Ubuntu?  Please help and thanx in advance!:)

---

### Post by lnxpwr on 2006-01-29
try this:     sudo hostname <your_new_hostname>
and don't forget to update your /etc/hosts!

---

