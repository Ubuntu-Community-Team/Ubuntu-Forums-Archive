---
title: "failed to update default ppas"
date: 2011-11-12
forum: General Help
---

### Post by SGFzc2U= on 2011-11-12
W:Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net//ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net//ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What I'm supposed to do now?

All other ppas succeed and update without problems.

I've googled this problem but didn't find anything relevant...:confused:

---

### Post by BillyBoa on 2011-11-12
Just remove those 2 PPAs from your sources.

Open the Software Sources and from the tab Other Software, uncheck the 2 PPAs. Then update

---

### Post by SGFzc2U= on 2011-11-12
Yeah, but aren't they the default ppas of ubuntu? I would like to update my system.
Thanks anyway!

---

### Post by raja.genupula on 2011-11-12
> **SGFzc2U= said:**
> Yeah, but aren't they the default ppas of ubuntu? I would like to update my system.
Thanks anyway!

1..change your server (from update manager settings)to another best mirror and then update again.

if error still exists follow above suggestion

---

### Post by SGFzc2U= on 2011-11-12
How do you choose other mirrors from there?

---

### Post by raja.genupula on 2011-11-12
> **SGFzc2U= said:**
> How do you choose other mirrors from there?

update manager --> settings  --> 1st tab ubuntu software --> download from .....change there

---

### Post by SGFzc2U= on 2011-11-12
Thanks! Now it works perfectly!:)

---

### Post by raja.genupula on 2011-11-12
thats really good news .. please mark the thread as solved from thread tools.

Thank you.

---

