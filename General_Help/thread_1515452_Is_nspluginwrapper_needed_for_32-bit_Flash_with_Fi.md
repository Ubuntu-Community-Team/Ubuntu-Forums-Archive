---
title: "Is nspluginwrapper needed for 32-bit Flash with Firefox 3.6.4"
date: 2010-06-22
forum: General Help
---

### Post by mgol on 2010-06-22
I wonder if the Firefox 3.6.4 Out-Of-Process-Plugins mechanism makes nspluginwrapper needed any more. Isn't it possible to have a 32-bit plugin-container process along with 64-bit Firefox? Then we could get rid of still buggy nspluginwrapper and at the same time not care about 64-bit Flash any more (especially that it's abandoned for some time).

Or am I misled?

---

### Post by lovinglinux on 2010-06-22
Interesting question, but I don't think that would be possible, because the process that runs the flash plugin is still a browser process. I'm just guessing anyway.

---

### Post by mgol on 2010-06-22
> **lovinglinux said:**
> Interesting question, but I don't think that would be possible, because the process that runs the flash plugin is still a browser process. I'm just guessing anyway.

Why would it mean anything? Another process is another process, 32-bit processes can easily communicate with 64-bit processes.

There may be some specific implementation-related difficulties, but the fact it's still a Firefox process IMHO doesn't really matter.

---

