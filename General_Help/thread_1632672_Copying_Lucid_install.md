---
title: "Copying Lucid install"
date: 2010-11-28
forum: General Help
---

### Post by pratikk on 2010-11-28
Hi, I'd like to copy my OS, plus all packages I have installed, settings files and the home folder, and replicate it on various devices, including thumb drives. I've read the literature and nothing seems to be just right:

1. APTonCD excludes packages not installed through apt.

2. Cloners cannot replicate on smaller target partitions. 

3. SBackup seems to be focused on data, not the whole system. 


Is there an obvious solution I'm missing? 

Grateful for advice

Pratik

---

### Post by mikewhatever on 2010-11-28
Some cloners, Clonezilla, Partimage, Partclone, only copy used blocks and don't care about the size of the partition, as long as the data to copy fits. Note that Partimage doesn't support ext4 file system.

---

### Post by pratikk on 2010-11-28
Thanks a lot, Mike. Checked them out, and Partclone seems to fit the bill. The others seem to have have filesystem or size restrictions. 

Regards

Pratik

---

### Post by Megaptera on 2010-11-28
You could also have a look at Remastersys if (like me) you like a CD/DVD to hold ...

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by pratikk on 2010-11-29
Thanks, Remastersys does look right. But I can't figure out how to install the source from geekconnection. Make doesn't seem to be an option. I tried gksu/sudo remastersys/remastersys-gui. No dice, and no installation instructions on the Website. How did you get it to work? 

Pratik

---

### Post by ezsit on 2010-11-29
Just download the .deb file from their Sourceforge site:
[http://sourceforge.net/projects/remastersys/files/](http://sourceforge.net/projects/remastersys/files/)

remastersys_2.0.17-1_all.deb is the file you want if your version of Ubuntu is above Karmic (9.10). This version relies on Grub2, so an updated system from before Karmic will not work unless Grub2 has been installed instead of the older Grub from versions before Karmic.

Use gdebi to install or if using 10.10, the .deb file should open up in Software Center. It will pull in all the dependencies and install automatically. The menu item will be placed in the System menu.

---

### Post by pratikk on 2010-11-30
Thank you, ezsit, got it installed now. Thanks also to everyone else who gave advice. This will save me a lot of pain doing repeat installs. 

Best

Pratik

---

### Post by Megaptera on 2010-11-30
You're welcome!

---

