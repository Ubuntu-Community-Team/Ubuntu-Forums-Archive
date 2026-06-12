---
title: "why does it say networking disabled?"
date: 2010-08-05
forum: General Help
---

### Post by foolguy on 2010-08-05
My computer was working just fine earlier today, now I can't connect to the intetnet and it says networking disabled. What happened? I didn't change any settings or anything.

---

### Post by murphycc on 2010-08-05
Did you go into hibernate mode between when it worked and didn't?

Below is a write-up I had found that helped me, but perhaps yours is unrelated.

At the very least, try checking that NetworkManager.state file.

-Chris

-----


Network Manager worked in the beginning after patching and rebooting the KNetworkManager showed "Network Management disabled". No option to enable it again was available.

The issue was caused by
  NetworkingEnabled=false
in
 /var/lib/NetworkManager/NetworkManager.state

After changing it back to
 NetworkingEnabled=true
in
 /var/lib/NetworkManager/NetworkManager.state
and running
 sudo service network-manager restart
everything worked fine again.

---

### Post by nerdy_kid on 2010-08-05
try suspending and resuming, and if it still doesnt work reboot.

---

### Post by foolguy on 2010-08-08
> **nerdy_kid said:**
> try suspending and resuming, and if it still doesnt work reboot.
Ok, that worked perfect for me, thanks. Typing from the problem computer now.

---

