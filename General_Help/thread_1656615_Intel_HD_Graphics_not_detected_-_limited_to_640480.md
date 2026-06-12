---
title: "Intel HD Graphics not detected - limited to 640*480 resolution .."
date: 2010-12-31
forum: General Help
---

### Post by Simple Nok on 2010-12-31
**OS:** Ubuntu 10.10[COLOR=Silver] ( running in VirtualBox )[/COLOR]
**Video card:** Intel HD Graphics

Installation went through as expected and I did a full system update before proceeding.

Now, the problem is quite simple - the given video card isn't being detected. 
Hardware menu section says it can not find any hardware drivers ( none listed ).

I'm limited to 640*480 resolution.

What can I do in this situation ?

---

### Post by dcstar on 2010-12-31
> **Simple Nok said:**
> **OS:** Ubuntu 10.10[COLOR=Silver] ( running in VirtualBox )[/COLOR]
**Video card:** Intel HD Graphics

Installation went through as expected and I did a full system update before proceeding.

Now, the problem is quite simple - the given video card isn't being detected. 
Hardware menu section says it can not find any hardware drivers ( none listed ).

I'm limited to 640*480 resolution.

What can I do in this situation ?

[LIST=1]
[*]VM questions belong in the Virtualization forum.
[*]VMs use their own Virtual hardware as provided by the VM when it is set up correctly, not the physical hardware.
[/LIST]

---

### Post by Yellow Pasque on 2010-12-31
Install the Virtualbox "guest additions" (under the Device menu of VirtualBox). [http://ubuntu-tutorials.com/2010/06/26/install-virtualbox-guest-additions-on-virtualbox-guests/](http://ubuntu-tutorials.com/2010/06/26/install-virtualbox-guest-additions-on-virtualbox-guests/)

---

