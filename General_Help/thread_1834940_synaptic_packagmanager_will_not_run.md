---
title: "synaptic packagmanager will not run"
date: 2011-08-28
forum: General Help
---

### Post by mgeib1 on 2011-08-28
I recently tried to install dassault-system Draft-sight and the installation failed. now when I try to start Synaptic Package manager I get the following error message:

E: The package dassault-systemes-draftsight needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


When I hit the X or close it closes the entire Synaptic package manager and will not let me continue or install other packages.

any assistance would be most appreciated.

---

### Post by Chiel92 on 2011-08-28
> **mgeib1 said:**
> I recently tried to install dassault-system Draft-sight and the installation failed. now when I try to start Synaptic Package manager I get the following error message:

E: The package dassault-systemes-draftsight needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


How did you exactly try to install dassault-system Draft-sight?

---

### Post by oldos2er on 2011-08-28
Can you run ```
sudo apt-get autoclean && sudo apt-get update
``` in a terminal, and if there are errors post the output here?

---

