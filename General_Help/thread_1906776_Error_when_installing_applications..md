---
title: "Error when installing applications."
date: 2012-01-09
forum: General Help
---

### Post by NBPX on 2012-01-09
In Kubuntu 11.10, when I try to install applications through the package manager or by the central application the following message appears.

> This operation can not continue because it was not provided proper authorization.

This began to occur after uninstalled kubuntu-desktop accidentally. It happened as follows. I tried to remove the LAMP server with the command ```
 sudo apt-get remove lamp-server ^ 
``` and when I went to see there were several desktop applications being removed. The applications were being removed without even asking me before, and without telling me this would happen. Why there was a mine there? And worse because there was an unmarked land mine?

I did a quick Google search and found the following command to reinstall kubuntu-desktop ```
sudo apt-get install kubuntu-desktop
```.

But after restarting the system were missing some applications I had installed after installing Kubuntu. Ok, let's install again. Damn! Began to appear the error noted above.

How do I solve this?

---

### Post by NBPX on 2012-01-10
Neither Windows 98 brought me so many problems. I have to reinstall Kubuntu every two weeks due to problems that arise and I that can not solve. :cry:

---

### Post by NBPX on 2012-01-10
I solved the problem as follows:


- Right click on the Application Launcher button (start menu button);
- Left click on "Edit Application ...";
- Open the item "System" (on the left by clicking with the left button on the arrow to the left of "System");
- Left click on "Muon Software Center";
- In the "Command" field of the "General" tab (on the right), at the beginning, insert "kdesudo" so that the command turns into a "kdesudo muon-installer% i-caption"% c "";
- Left click on "Muon Package Manager";
- In the "Command" field of the "General" tab (on the right) at the beginning insert "kdesudo" so that the command turns into a "kdesudo muon% i-caption"% c "";
- CTRL + S to save and close.


Note: The Muon and Muon installer now ask for the password when they are open rather than ask for a password when installing applications.

---

