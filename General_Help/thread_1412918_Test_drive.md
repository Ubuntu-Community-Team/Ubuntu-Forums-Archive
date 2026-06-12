---
title: "Test drive"
date: 2010-02-21
forum: General Help
---

### Post by windowsfree on 2010-02-21
Ok, I installed TEST DRIVE and opened it up and downloaded an image for Virtual OSE.
Where did it go?  Appeared to have DL'd as an ISO, but cannot find it by searching.

Any input greatly appreceiated.

---

### Post by derande on 2010-02-21
i installed test drive and used it to download the most recent lucid. 
after downloading, it would attempt to open in virtualbox and got as far as the language then install/live disc option, then it would freeze and do nothing.
not happy with this so i removed it and i, too, was wondering where there iso was stored as i didn't see ~650mb of space restored.

---

### Post by windowsfree on 2010-02-21
it starts the remote session for me, but Virtual box never powers on.  It shows up but the test drive machine remains powered off.  
After numerous attempts it started and is running!

---

### Post by Piotr.Sniady on 2010-03-04
> **derande said:**
> i installed test drive and used it to download the most recent lucid. 
after downloading, it would attempt to open in virtualbox and got as far as the language then install/live disc option, then it would freeze and do nothing.
not happy with this so i removed it and i, too, was wondering where there iso was stored as i didn't see ~650mb of space restored.

File /etc/testdriverc contains your setup.
Probably your iso is located in ~/.cache/testdrive

---

