---
title: "All windows minimise when started - UNR is unusable"
date: 2010-05-02
forum: General Help
---

### Post by bwobbones on 2010-05-02
Hi,

  I've been using UNR since the 9.04 release on my Eee 1000HE and have been generally happy with it as a solution since then.

  Tonight I've upgraded to 10.04 using the package manager and everything starts correctly but when I start any application it minimises itself straight away making the system unusable.  If I click on the application to bring it to focus, I get about 1/2 a second of typing before it minimises itself again.

  Using that method I've been able to get around the problem with a sudo apt-get remove netbook-launcher - but I like the netbook launcher and I'd like to keep using it.

  Any ideas?

---

### Post by jaddi27 on 2010-05-03
Hi,

I have also got the same problem. I just upgraded UNR 9.10 to 10.04 on an Asus N10Jh, and the same problem occurs.

Nothing like this has happened before the upgrade, so must be some incompatibility.

Joel

---

### Post by straxus on 2010-05-03
I had this same problem.  I believe I fixed it by removing netbook-launcher from Preferences>Startup Applications, and then creating a new entry for it.

EDIT: The new entry should launch netbook-launcher-efl

---

