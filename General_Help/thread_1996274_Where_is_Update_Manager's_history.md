---
title: "Where is Update Manager's history?"
date: 2012-06-04
forum: General Help
---

### Post by Handssolow on 2012-06-04
Before if I wanted to review Update Manager's history I could look in Synaptic Package Manager>File>History but for some while now the only items recorded are those directly installed by SPM, not those installed by Update Manager.

The information I seek looks to be there in var/log/dpkg.log.1 though I am not certain if it's a complete record or the best file to look at.

Is there a way to return so Synaptic Package Manager displays all my install history as it used to do?

---

### Post by raja.genupula on 2012-06-04
open```
 software center -> History -> Updates 
``` navigate as i mentioned and that will leads you to the history of update manager .

---

### Post by inashdeen on 2012-06-04
I would suggest using mintupdate. cleaner :)

---

### Post by oldos2er on 2012-06-04
> **inashdeen said:**
> I would suggest using mintupdate. cleaner :)

I wouldn't recommend using a tool meant for a different distro on Ubuntu.

Handssolow, have you checked /var/log/apt/* ? I'm not sure how you might go about adding this info to Synaptic though.

---

### Post by Handssolow on 2012-06-04
Many thanks raja.genupula, I'll mark this thread as solved.

---

