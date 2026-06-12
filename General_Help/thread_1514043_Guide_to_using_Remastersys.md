---
title: "Guide to using Remastersys"
date: 2010-06-20
forum: General Help
---

### Post by colorlessprism on 2010-06-20
Remastersys is an awesome application. It also allows you to create an installable LiveCD of your current install. If anything happens to your computer you can be back up and running in no time.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

First things first, we need to install Remastersys. Remastersys will not be repositories. We will have to manually add it.

There are numerous ways to add a source, but for ease of use click: ***System > Administration > Software Sources***

You should now have a menu of all the sources that Synaptic (package manager) looks at when searching for programs and updates. Click on the "Other Software" tab.

Click "Add" this will open a small window, where you need to copy the source address. For Karmic, Lucid and newer with Grub2 the address is:

***deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/***

Copy what is in bold into the address line and click "Add". After you have added the new repository click "Close" and when the sources have refreshed the window will close.

Now start up Synaptic: ***System > Administration > Synaptic*** , and type "Remastersys" in the "Quick Search" box and install it.

Before you run Remastersys, close every other application you are running and unmount any network shares. The GUI will warn you about this. If you do not do this, it is possible that your backup could fail. *You must close all windows, this really can affect the build*. Once you have unmounted network shares and closed all windows you can continue.

To start Remastersys: ***System > Administration > Remastersys Backup***

When the window opens you might notice you have several options to choose from:

**Backup**: allows you to backup your entire installation, along with all the personal data and configurations.

**Dist**: allows you to create a backup, minus your personal data, allowing you to share the "remastered" copy with other people.

**DistCDFS**: makes a distributable CD filesystem only, this is if you want to add files to the CD

**DistISO**: makes a distributable ISO file only, CD filesystem must be completed already

**Modify**: here you can set the name and the location of the backup file, along with several other configuration options. 

*_Remastersys is limited by the ISO standard and choosing the "Backup" option may cause the file size to be too large. The exclusion option should be used to reduce the file size. An example being: you already backup your documents and pictures to another location so it is not necessary to back them up with Remastersys. you will add the /path/to/file in the exclusion box in the Modify section. (/home/<username>/Documents)_*

**Clean**: after you have used Remastersys and have finished with the files created. You can run this option to remove files made by the program and free up the hard disk space. It's a good idea to run this option before running a new backup.

If you want an installable copy of your exact system choose the "Backup" option, it will create an ISO image based on your current install, any programs, downloads, etc will be on the CD as well. 

_*It might be a good idea to do some house cleaning before you start*_

If you want to give copies of your install to other people (minus your pictures, documents, etc). You should click the "Dist" option in the menu instead. Perhaps you've made a great setup for people who have never used Ubuntu, its got all the common programs installed and tweaks have already been done.

Select the option you want. This process will take quite some time, especially if you have a lot of applications installed. Once the process has finished, you can go to /home/remastersys. Inside you'll find your ISO. Move the ISO to your home directory. Make sure you grab the m5d checksum while you're there

Now we need to either burn the ISO to a CD or use "USB Startup Disc Creator" to make a bootable flash drive. Pick the option you prefer. When you have finished restart your computer. 

Once you have booted into your custom ISO. You can verify that it works by either selecting the "Test for Defects" option, or just let it load up to see if everything is where it should be.

If everything works well and you have a running copy of your install don't forget to run the "Clean" option from the Remastersys GUI.

---

