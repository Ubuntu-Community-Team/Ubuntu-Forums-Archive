---
title: "GPG error -packages medibuntu?"
date: 2010-06-15
forum: General Help
---

### Post by germanix on 2010-06-15
When I go to the Update Manager to update my system I get the following error message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I am not sure what this exactly means and what I need to do to fix this. Could someone please advise?
Thank you.

---

### Post by philinux on 2010-06-15
[http://ubuntuforums.org/showthread.php?t=318519](http://ubuntuforums.org/showthread.php?t=318519)

---

### Post by germanix on 2010-06-15
Thanks philinux, worked for me.
"sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update"
All fine now. Have a nice day. :lolflag:

---

