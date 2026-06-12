---
title: "Update Manager Error Message"
date: 2010-04-14
forum: General Help
---

### Post by chome4 on 2010-04-14
Going through the usual Update Manager and getting:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.19+nobinonly-0ubuntu0.9.04.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.19+nobinonly-0ubuntu0.9.04.1_i386.deb)

Google searching tells me xlrunner is related to Mozilla but doesn't cause Firefox any problems.

When I try to manually run 

[http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.19+nobinonly-0ubuntu0.9.04.1_i386.deb]("http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.19+nobinonly-0ubuntu0.9.04.1_i386.deb..........and")

and run it via Package Installer, I get:

Error: Breaks exisiting package 'xulrunner-1.9-gnome-support' dependency xulrunner-1.9 (= 1.9.0.18+build1+nobinonly-0ubuntu0.9.04.1)

Any ideas on how to resolve this?

Thanks.

---

### Post by zvacet on 2010-04-14
Try under system>admin>software sources to change server to main and see if that help.

---

### Post by chome4 on 2010-04-15
Seemed to do the trick. No error message.

Thank you very much....

---

