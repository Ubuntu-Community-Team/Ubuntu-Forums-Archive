---
title: "getting an anti virus through ubuntu to attack windows platform"
date: 2011-06-25
forum: General Help
---

### Post by Dempseydaze on 2011-06-25
I just put Ubuntu on my system due to a virus on  the windows app. side.  I'm not what you call very PC savy...so....can I  down load something via the Ubuntu platform to take care of the viruses  bogging down the windows platform??  Thanks

---

### Post by ahears on 2011-06-25
Open the  Synaptic Package Manager and look for a package called clamav, and klamav the frontend gui for clamav. Also, there is a package for linux from Avast! than may be of help as well.

---

### Post by haqking on 2011-06-25
> **ahears said:**
> Open the  Synaptic Package Manager and look for a package called clamav, and klamav the frontend gui for clamav. Also, there is a package for linux from Avast! than may be of help as well.

that will only offer protection (debatable if needed on linux) within his Linxu system it will not protect or clean his windows system.

best bet is to download a AV boot disk to scan your windows system such as this [http://www.softpedia.com/get/Antivirus/Kaspersky-Rescue-Disk.shtml](http://www.softpedia.com/get/Antivirus/Kaspersky-Rescue-Disk.shtml)

there are many out there to choose from though

though a AV in linux could scan a drive that windows is on, it is better to run the AV within windows or from a AV boot disk in my opinion or use a Ubuntu live CD such as this [http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/)

---

### Post by Enigmapond on 2011-06-25
> **ahears said:**
> Open the  Synaptic Package Manager and look for a package called clamav, and klamav the frontend gui for clamav. Also, there is a package for linux from Avast! than may be of help as well.

The GUI for clamav is clamtk so just open the terminal and do:

```
sudo apt-get install clamav clamtk
```

and then run it on your windoze partition.

---

### Post by dFlyer on 2011-06-25
I would recommend you search google for avg-recovery cd. It's an iso you can burn to cd and scan your windows disc for virus. You do need a hardwire connection to the internet.

---

### Post by DawieS on 2011-06-25
Welcome to the forums!:smile:

Also please keep in mind that after a scan, **clamav** will only point out the files that contain known viruses. You still have to delete or move these files yourself.

You can do this with a file browser. Click on **Places**, then **Computer**, then click on the left pane to mount the Windows partition.

The file browser is immune to normal Windows viruses, and you may safely click on the virus-containing files. However, depending on the file system in use, you may be unable to delete these files.

I have seen some nasty viruses on a FAT32 file system, where the file system itself is infected. Attempts to delete the files returns an **Operation not Supported** error. In such a case, it is best to copy out all the clean files, then reformat the partition.

---

### Post by Dempseydaze on 2011-06-26
wow...thank you to all of you for the quick, and hopefully, good advise.  Im sure from the confidence in all your threads Ill be good to go!  Thanks so much-

---

