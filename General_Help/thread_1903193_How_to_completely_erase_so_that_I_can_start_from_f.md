---
title: "How to completely erase so that I can start from fresh?"
date: 2012-01-01
forum: General Help
---

### Post by umfan92 on 2012-01-01
Well the title says it all. I have had a few problems and want to completely erase ubuntu. I dual boot windows and ubuntu and I would like to leave my windows partition alone. 

How can I erase ubuntu so that I don't harm my windows partition? And how can I reinstall it?

---

### Post by Rodney9 on 2012-01-01
Boot from your Ubuntu CD/DVD and Install, go thru the steps till it asks where, then tell it to install over the old install.

Rodney

---

### Post by Mark Phelps on 2012-01-02
Yeah ... and if you accidentally pick the WRONG partition, you end up erasing Windows!

My suggestion is to boot from an Ubuntu desktop CD, choose Try Ubuntu, then launch Gnome Partition Editor (GParted).

When it opens, you will see a list of paritions.  Format the Ubuntu (Ext4) partition. It's a LOT harder to pick the wrong partition using GParted than it is with the Ubuntu installer.

---

### Post by saneearth on 2012-01-02
During the Ubuntu install you have three options: install alongside, completely erase disk and install or an "other" option. Choose this option and you will get to the partition tables. It is pretty easy to see the windows partition, so leave it alone. You should also have a smaller partition that is likely ext4 and a larger ext4 partition. The smaller partition 15GB or so is the root and you should select change and put / in the drop down box and check the box to format. For the Larger ext 4 partition select change, put /home in the dropdown box and check the format box for it also. This will install Ubuntu to the same partitions you had, but completely format everything. 

I typically just reformat the root partition and delete all the .config files and associated files in the home and not format it. That way I preserve my data. If you don't have a lot of data saved the reformatting both home and root will give you a completely fresh new install. If there is a /swap partition showing you can just leave it as is. This is my method anyway.

---

