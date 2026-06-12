---
title: "license file + port"
date: 2009-08-05
forum: General Help
---

### Post by any.linux12 on 2009-08-05
Hi

How can I have a license file on the port 28000?

---

### Post by jocko on 2009-08-05
You may want to expand a little on that question. I'm sure no-one that reads it get a deep enough understanding of what you are trying to accomplish to even be able to guess what you need to do...

License file for what? Are you trying to run some kind of license server for some 3rd party software? In that case maybe you should look up the manual for that software...

---

### Post by any.linux12 on 2009-08-05
> **jocko said:**
> You may want to expand a little on that question. I'm sure no-one that reads it get a deep enough understanding of what you are trying to accomplish to even be able to guess what you need to do...



ok

the software is NX6 from Siemens and UGS. I need to run a license on the port 28000 of my desktop. On the manual it says that I should use their software but it's not working properly.

./lmgrd -c /root/Desktop/ugs.lic 28000@esp-CAD

(lmgrd) Still trying... 
11:54:41 (lmgrd) Still trying... 
11:54:48 (lmgrd) Still trying... 
11:54:59 (lmgrd) Still trying... 
11:55:03 (lmgrd) Failed to open the TCP port number in the license.
11:55:17 (lmgrd) Still trying... 
11:55:35 (lmgrd) Still trying... 
11:55:50 (lmgrd) Failed to open the TCP port number in the license

the lmgrd is the script from the NX software and should open the TCP port for the license. Well it's not working and I think that should be possible to do it in other way, manually with ubuntu.

Thanks in advance

---

