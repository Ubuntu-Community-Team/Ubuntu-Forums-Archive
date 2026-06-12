---
title: "System Requirements"
date: 2006-06-04
forum: General Help
---

### Post by rcarring on 2006-06-04
To successfully run Dapper Drake:

128 mb system ram (dedicated ram so if you have a graphics card that shares system ram, you do not have 128mb)

Clean install 5GB - you may want to double this figure if you want to install a lot of the software packages - a default alternate cd install requires the best part of 3GB

Graphics cards are a separate issue and details may be found elsewhere. In summary nVidia and ATI will require more work to get them up and running.

A clean sources.list with ALL non-standard repositories commented out, or use the one provided by ubuntu_demon

If you have more than one partition or want to have a separate /home partition use the alternate cd if possible.

Read the Ubuntu installation guide -- [http://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf](http://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf)

If your only machine is the one you are upgrading/installing upon then print out a copy if possible, it's 80 pages but most printers will let you print two pages to a page.

Please allow sufficient time to perform the upgrade, you will need to watch for questions such as "I want to overwrite this conf file" if you are upgrading. For a fresh install, don't leave the house, but check back on progress periodically.

I would allow 3 hours minimum for a fresh install, this includes booting the desktop and making sure things like sound and network work.

If you are going to edit or replace sources.list make a back up copy.

If you have a non-standard setup: eg. XP and another Linux distribution installed, then you should use the alternate CD.

The Live CD should allow you to verify if your hardware is supported.

EDIT: You need 192mb ram for the Live CD because it creates a ram drive of 64mb. The ram drive is used for temporary storage, as the hard disk is unmounted and therefore unavailable to it.

---

### Post by rcarring on 2006-06-04
An additional step:

identify your hardware before you upgrade, then if the installation fails you can post your system specs here along with the error(s) and what you were trying to do at the point the installation fell over.

If you are upgrading from Breezy to Dapper, remember to do

sudo apt-get update

to get the correct version of update-manager installed.

I would also suggest, even if you are not going to use it to install, to download the alternate cd as this can act as an emergency repository and may help people whose dist-upgrade napped out due to slow servers.

---

