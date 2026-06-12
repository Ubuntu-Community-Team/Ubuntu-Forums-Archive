---
title: "Bleachbit"
date: 2011-11-12
forum: General Help
---

### Post by rajeevkvasu on 2011-11-12
[SIZE=3]I tried to run bleachbit as root in Ubuntu 11.10, but it shows an error message[/SIZE][Errno 13] Permission denied: '/root/tmp4nVCUDsU6ccxxaOa-8wq4y7afQpFvEqkI1BGvNxGc9TTWtOmY_OqGZ9IHg3otPIu2NQbvR_yKIQhXiBYQogdlkT1Wl01cL-TFTtfEkZio9bH77BSBJx5Of-2ruAF6.OxRnsevmMRfnRzX.8fp7nTXa seAHsO7-qdN11VjX-gvbG8_u1mt.a3d6vo5ki2l.yt_LHiO3r1ox3uO-HVLGQ9wG9sgPk_Wvp1VzJumZJGS.pcHSA7_BNQSxDcCf'

[SIZE=3]What it means?


[/SIZE]

---

### Post by techvish81 on 2011-11-12
only meaningful info in it is "permission denied" all other things seem to be written in a language harder than hebrew...hahahha

---

### Post by techvish81 on 2011-11-12
it asked your password before starting?

---

### Post by Rubi1200 on 2011-11-12
> **rajeevkvasu said:**
> [SIZE=3]I tried to run bleachbit as root in Ubuntu 11.10, but it shows an error message[/SIZE][Errno 13] Permission denied: '/root/tmp4nVCUDsU6ccxxaOa-8wq4y7afQpFvEqkI1BGvNxGc9TTWtOmY_OqGZ9IHg3otPIu2NQbvR_yKIQhXiBYQogdlkT1Wl01cL-TFTtfEkZio9bH77BSBJx5Of-2ruAF6.OxRnsevmMRfnRzX.8fp7nTXa seAHsO7-qdN11VjX-gvbG8_u1mt.a3d6vo5ki2l.yt_LHiO3r1ox3uO-HVLGQ9wG9sgPk_Wvp1VzJumZJGS.pcHSA7_BNQSxDcCf'

[SIZE=3]What it means?


[/SIZE]
Hi and welcome to the forums :)

Open a terminal using Ctrl+Alt+T and run the following commands one at a time:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```You will be asked for your password. This is the same password you use to login.

The password is not echoed on screen but just type it correctly and then press Enter.

If any of these commands produce errors, post the content here please.

One question: are you the only user on the computer?

---

