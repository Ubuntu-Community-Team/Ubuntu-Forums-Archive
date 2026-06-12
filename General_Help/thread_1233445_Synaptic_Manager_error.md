---
title: "Synaptic Manager error"
date: 2009-08-06
forum: General Help
---

### Post by cp3o on 2009-08-06
**Synaptic Manager error or warnng**

Can someone advise me:
Changed server from Main to Canada with no change
Internet is good no changes.
reboot no change.
Not 100% sure what a ppas is (via another post)


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Soul-Sing on 2009-08-06
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by TeoBigusGeekus on 2009-08-06
Have you added the key to use the medibuntu repository?
If not, type this in a terminal
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by cp3o on 2009-08-06
> **leoquant said:**
> ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


This is the return:

Fetched 198B in 2s (93B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Soul-Sing on 2009-08-06
Before running apt-etc.in the terminal close any other package/datamanager: synaptic/addremove software....

---

### Post by cp3o on 2009-08-06
Thanks guys
Yes i did add that repository
I closed spm and it asked me if i wanted to install that  repository i said no 
results: same error
So i redone that and applied Y and all is fixed

I'm in the break and fix mode with ubuntu, would like to make this my main computer.
I hope i can be of service down the road.
What is your opinions on the ubuntu classes that are available?

Steve

---

