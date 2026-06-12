---
title: "How do I do a fresh install without loosing settings"
date: 2011-08-10
forum: General Help
---

### Post by Robbyx on 2011-08-10
I would like to transfer the settings and list of installed applications to a new partition as I propose to do a fresh install into a new partition.

Can it be done?
If I could run ubuntu from the old partition I would do:

SUDO dpkg -- get-selections >/home/robin/package.selections

but

I can no longer boot from the old partition. I can access it from within the live cd. Is there an application which will extract a list that will set the old application selections into the new partition?

---

### Post by thefasterblueone on 2011-08-10
First backup anything you need from the old partition. Put the file 'package.selections' on any type of removable media you may have, usb flash drive is best.

Then reinstall the new system, put in the media with the file 'package.selections',drag and drop the file to a 'directory of your choice'.

Then be sure you have an internet connection and if any of these packages rely on any PPA's or other sources be sure to add them in 'Software Sources'. 
Then in 'Terminal' run:

```
sudo apt-get update
sudo dpkg --set-selections < /directory/of/your/choice/package.selections
sudo apt-get -u  dselect-upgrade
```

---

### Post by Robbyx on 2011-08-11
> **thefasterblueone said:**
> First backup anything you need from the old partition. Put the file 'package.selections' on any type of removable media you may have, usb flash drive is best.

Then reinstall the new system, put in the media with the file 'package.selections',drag and drop the file to a 'directory of your choice'.

Then be sure you have an internet connection and if any of these packages rely on any PPA's or other sources be sure to add them in 'Software Sources'. 
Then in 'Terminal' run:

```
sudo apt-get update
sudo dpkg --set-selections < /directory/of/your/choice/package.selections
sudo apt-get -u  dselect-upgrade
```

Thank you for your reply. It will be useful once I have overcome the initial problem of accessing the old drive.

My question was really: **How do I extract the package selections in the first place**. I can not boot into the old system although I can see it and access the drives via the live CD. DPKG does appear to allow me to point to a particular partition in order to extract the selection from that partition.

---

### Post by Robbyx on 2011-08-11
Does anyone know the answer to creating a list of programs via dpkg that  are installed on an installation that will not load but which can be accessed by the file manager using the liveCD?

---

### Post by mringer on 2011-09-04
If I understand you, you want to find what packages were
installed on your PC before it became un-bootable. I believe that
this data is in the file 

/var/lib/dpkg/status

but mixed with lots of other information that you dont want. I 
am not sure how to remove the unwanted data. Maybe:

copy the live CD to a USB stick
boot from the stick
copy the status file onto the stick
(this might make the stick un-bootable)
run  dpkg-query.

Sorry I cannot help you if this fails.

---

