---
title: "Ubuntu 9.04 and Rational Application Developer"
date: 2009-10-09
forum: General Help
---

### Post by radDeveloper on 2009-10-09
I have successfully installed IBM Rational Application Develop 7.5.4 on Ubuntu 9.04 32-bit, the only problem is that the installation manager will not save the license I have. The license works on other linux distros, and in fact I can step through the wizard with this license and the Installation manager will complete successfully. Unfortunately, the next time I go to "Manage Licenses" it still has the trial license in use. 

Has anyone successfully applied the license? Or can anyone provide tips to manually install the license. I've searched for the trial license and cannot find where it is located.

---

### Post by corep105 on 2009-10-12
i am running RAD 7.5.4 on ubuntu 9.04 64 bit. I did not have any issues with importing the license - but this is a full license and not the trial license.

My license file is a small file called RAD75lic.jar. I can't remember if you have to import a trial license - think that the update manager will just list RAD as trial if you do not have a full license.

---

### Post by albertogiantin on 2009-10-23
I have the same problem.
I've installed rad 3 month ago with the full license, last week i had an upgrade to manage ejb3 in was6.1 and now the license doesn't work. I tried many times to apply the license one more time but without success, the next time I go to "Manage Licenses" it still has the trial license in use. 
Any Idea?

---

### Post by radDeveloper on 2009-10-23
I actually have the permanent license - RAD75lic.jar. I installed successfully onto a Centos 5.3 distro, but for whatever reason it will not take on Ubuntu. For obvious reasons, I would prefer to work in that environment. Does anyone know where RAD stores the licenses information. I would like to try and copy everything from Centos install to the Ubuntu install for the license config.

---

