---
title: "Disable 'Waiting for Network' during boot"
date: 2011-10-28
forum: General Help
---

### Post by decoherence on 2011-10-28
During the boot process I get this 'waiting for network' message, then 'waiting up to 60 more seconds for network' -- how do I disable this, or skip it? I frequently need to boot without network connectivity and the delay is annoying.

thanks,

---

### Post by gsmanners on 2011-10-28
Looks like they're [working on it]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/881079").

---

### Post by decoherence on 2011-10-28
Thanks, gsmanners!

marking thread solved. even though the problem still exists, i have my answer

---

### Post by mavenuparker on 2011-11-08
Hey I too encounter the same problem.
Can you tell me how did you fix it?

---

### Post by t4thfavor on 2011-11-26
I now have the same problem after upgrading from 10.10 -> 11.04 -> 11.10. It also hangs waiting for nfs mounts, something that did not happen in 10.10, I'm not sure about 11.04 since I only booted it once.

This is a laptop with several nfs mounts that I only want mounted when I am on a network.

---

