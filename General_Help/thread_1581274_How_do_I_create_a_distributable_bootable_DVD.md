---
title: "How do I create a distributable bootable DVD?"
date: 2010-09-24
forum: General Help
---

### Post by sr_guy on 2010-09-24
My Lucid entire setup (progs, sys files, & OS) size = 5.9GB

4GB of ROMs


Is there a way to compress this to fit on a dual layer, and then make the DVD bootable?

---

### Post by IcewindDale on 2010-09-24
Hello.
Although I have never done what you asked I found the following articles to be of possible interest to you.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by JOHNNYG713 on 2010-09-24
Try Remastersys  Download the .all.deb [http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download ]("http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download")
Go to your home folder click view then show hidden files, copy the entire content to ect/skel (Delete anything in skel before you past the content from your home folder) while the content is still greyed out right click any icon, properties permissions and give group and others access files permission and close, now go to system administration remastersys backup and set up your new back up or distro ! It is recommended that before you copy and past your home folder content that you clean up your system, I use Ubuntu tweak and bleach bit (non- admin) also clean your browser history for distro mode! If all goes well, after you have burnt your DVD, and are booting from the DVD,back up mode, you will log in as usual, in distro mode you  A, will boot right to the desktop, B, you will get the login screen, enter the user name you gave in the remastersys set up and at the password just press enter, That should take you to the descktop, C, You will not be able to login at all, This is a glitch with one or more of the installed programs, I have made many "Distros" this way, I hope you have great success !=D>

---

### Post by sr_guy on 2010-09-25
I use remastersys, but since iso size is limited to 4.7GB, its hard to make an all-in-one distro copy with all my ROMs

---

