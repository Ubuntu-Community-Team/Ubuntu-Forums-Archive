---
title: "Custom CD installer"
date: 2006-03-05
forum: General Help
---

### Post by BiTRIDER on 2006-03-05
I wanted to customize the installer so that all my favorite applications would be installed by default without having to always retrieve them from somewhere off the net.

I have been playing around with the installer for a while now and have figured out most of it. I've also read the wiki on how this is done. Basically what I did was create a folder with dists and pool directories. I placed all the packages I wanted into the pool directory (including the udebs) and built the requisite Packages, Packages.gz and Release (Release.gpg) files. I managed to build everything the installer needed and the install process works fine.

However, and this is the problem, after finishing the "install" of the packages (I built a metapackage which depended on the packages I wanted to have installed by default) the process continues on to removing the same packages it had installed previously. What is left are the packages installed by the debootstrap script (the so-called base packages). The only way I could install the KDE desktop I wanted was to kill aptitude after it installs the last package and before it starts removing the same packages it installed and then bringing it(aptitude) up again and installing my metapackage manually. 

Any ideas why this is happening?

---

### Post by aysiu on 2006-03-06
I have no idea how to customize the installer, but there are two things you may want to look into that may help:

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)
[http://www.partimage.org](http://www.partimage.org)

With AptMove, you can create a custom CD with add-ons you want. Then you can do a server install and create an install script that installs just the packages you want and insert your new add-on CD.

With PartImage, you can customize your installation just as you want and then back up the partition image. That way you can just restore that image instead of reinstalling.

---

### Post by BiTRIDER on 2006-03-06
Thanks aysiu for your reply.

I did use apt-move to generate the packages for the pool directory and apt-ftparchive for the Packages, Packages.gz and Release files required by the installer. I've also modified the ubuntu-keyring package and added my key to it so it recognizes the packages I've added. The partimage trick does not really help because I would also like to use the same customized CD to install it on other PCs I have that have different specs so that would mean additional configuration after restoring the backup image though I have thought of that too.

I would be glad to post the step-by-step howto if someone could point me to where I can do that. Hopefully, this would help those who are thinking of doing the same. Its just the part where kubuntu installs the packages then subsequently removes them that bothers me.

---

