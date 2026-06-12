---
title: "qns on virtualbox"
date: 2010-07-03
forum: General Help
---

### Post by guest_user on 2010-07-03
let's say I use a virtualization program like virtual box to install an os on top of my main os and the os installed in the virtual machine gets infected with some virus or worm or bot. 

1) Would the virus or worm affect my main os or would it be isolated to the os installed in the virtual machine?

2) if isolated, does that mean that if i delete the os then the problem is solved permanently?

3) Is there any way to disable network access for a particular os installed in virtualbox?

---

### Post by Irony on 2010-07-03
[LIST=1]
[*]Yes it is isolated, unless of course you use a shared folder to transfer it to your main os.
[*]Yes.
[*]Yes just disable the network interface of the guest os or use the guest firewall to block everything just as your would with a normal os.
[/LIST]

---

