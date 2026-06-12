---
title: "How to back out of &quot;nightly build&quot; repo?"
date: 2011-05-28
forum: General Help
---

### Post by olwe on 2011-05-28
Does anyone have experience backing out of a "nightly build" repo? In my case I'm doing Chromium from a "nightly build" PPA. I'm thinking this isn't such a good idea anymore. I'd like to get "latest, greatest" but not this incessant nightly build, which I'm fairly sure is giving me a buggy Chromium more than not. How can I gracefully back out of nightly and into just the regular latest repo?

---

### Post by Frogs Hair on 2011-05-28
Search for ppa purge for and remove it through the terminal .You can also remove the application from the synaptic package manager and then remove the the source from software sources . Software sources can be accessed from the update manager > settings > other software. I don't know the name of the ppa , so I can't provide the command.

---

### Post by olwe on 2011-05-28
I can check the "remove" checkbox next to "http://ppa.launchpad.net/chromium-daily/ppa/ubuntu" in Software Sources/Other. But then what do I do? I've still got Chromium from a daily build.

---

### Post by linuxinstalledfromhdd on 2011-05-28
> **olwe said:**
> Does anyone have experience backing out of a "nightly build" repo? In my case I'm doing Chromium from a "nightly build" PPA. I'm thinking this isn't such a good idea anymore. I'd like to get "latest, greatest" but not this incessant nightly build, which I'm fairly sure is giving me a buggy Chromium more than not. How can I gracefully back out of nightly and into just the regular latest repo?

Only use a PPA Purge from command line if you want to make sure this is completely removed.. And then use the Stable PPA to re-install everything.

---

### Post by Frogs Hair on 2011-05-28
> **olwe said:**
> I can check the "remove" checkbox next to "http://ppa.launchpad.net/chromium-daily/ppa/ubuntu" in Software Sources/Other. But then what do I do? I've still got Chromium from a daily build.

Open the Synaptic Package Manager and use the search to locate the application . On the line where it appears , right click and mark for complete removal and select apply . This if you don't have a purge command to use in the terminal.

---

