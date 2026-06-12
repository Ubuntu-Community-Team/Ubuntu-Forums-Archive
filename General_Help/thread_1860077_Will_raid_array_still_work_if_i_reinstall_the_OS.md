---
title: "Will raid array still work if i reinstall the OS?"
date: 2011-10-14
forum: General Help
---

### Post by sumasage on 2011-10-14
I am currently running Ubuntu 11.04 and for some reason it is not booting now.  It just come up to an ubuntu screen (the purple-ish screen) and just stay there.  I am not too savvy with linux so i am not sure how to troubleshoot it.      I am debating the option of reloading the OS with the latest version 11.10.  However, i currently have a 4 TB drives Raid 5 setup, i dont want to lose data.  If i just reload the OS will my Raid array info still work when booting into the reloaded OS?    I dont have any of the array ID info back up so i wont know what to put in the mdadm.conf file.  Any help on this is appreciated.  Thanks.

---

### Post by blueridgedog on 2011-10-14
It should be possible.  See the second page of this Linux Journal Article:

[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

You should boot on a LiveCD and test the ability to rebuild the array. From the linked article:

```
Listing 3. Scanning a Disk for RAID Array Members

[root@recoverybox ~]# mdadm --examine --scan  /dev/sda1 /dev/sda2 /dev/sda3
ARRAY /dev/md2 level=raid1 num-devices=2
 &#8618;UUID=532502de:90e44fb0:242f485f:f02a2565
   devices=/dev/sda3
ARRAY /dev/md1 level=raid1 num-devices=2
 &#8618;UUID=75fa22aa:9a11bcad:b42ed14a:b5f8da3c
   devices=/dev/sda2
ARRAY /dev/md0 level=raid1 num-devices=2
 &#8618;UUID=b3cd99e7:d02be486:b0ea429a:e18ccf65
   devices=/dev/sda1
This format is very close to the format of the /etc/mdadm.conf file that the mdadm tool uses. You need to redirect the output of mdadm to a file, join the device lines onto the ARRAY lines and put in a nonexistent second device to get a RAID1 configuration. Viewing the the md array in degraded mode will allow data recovery:

[root@recoverybox ~]# mdadm --examine --scan  /dev/sda1
 &#8618;/dev/sda2 /dev/sda3 >> /etc/mdadm.conf
[root@recoverybox ~]# vi /etc/mdadm.conf
Edit /etc/mdadm.conf so that the devices statements are on the same lines as the ARRAY statements, as they are in Listing 4. Add the “missing” device to the devices entry for each array member to fill out the raid1 complement of two devices per array. Don't forget to renumber the md entries if the recovery computer already has md devices and ARRAY statements in /etc/mdadm.conf.
```

You would need to specify your local disks in place of the examples, but you should be able to build a mdadm.conf file while in LiveCD mode and test the ability to access the data.  I recommend a backup of /etc regardless and that you make that backup while in the LiveCD session.  I would not do a reinstall until I could build a proof of concept access in the LiveCD environment.

---

### Post by sumasage on 2011-10-14
> **blueridgedog said:**
> It should be possible.  See the second page of this Linux Journal Article:

[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

You should boot on a LiveCD and test the ability to rebuild the array. From the linked article:

```
Listing 3. Scanning a Disk for RAID Array Members

[root@recoverybox ~]# mdadm --examine --scan  /dev/sda1 /dev/sda2 /dev/sda3
ARRAY /dev/md2 level=raid1 num-devices=2
 &#8618;UUID=532502de:90e44fb0:242f485f:f02a2565
   devices=/dev/sda3
ARRAY /dev/md1 level=raid1 num-devices=2
 &#8618;UUID=75fa22aa:9a11bcad:b42ed14a:b5f8da3c
   devices=/dev/sda2
ARRAY /dev/md0 level=raid1 num-devices=2
 &#8618;UUID=b3cd99e7:d02be486:b0ea429a:e18ccf65
   devices=/dev/sda1
This format is very close to the format of the /etc/mdadm.conf file that the mdadm tool uses. You need to redirect the output of mdadm to a file, join the device lines onto the ARRAY lines and put in a nonexistent second device to get a RAID1 configuration. Viewing the the md array in degraded mode will allow data recovery:

[root@recoverybox ~]# mdadm --examine --scan  /dev/sda1
 &#8618;/dev/sda2 /dev/sda3 >> /etc/mdadm.conf
[root@recoverybox ~]# vi /etc/mdadm.conf
Edit /etc/mdadm.conf so that the devices statements are on the same lines as the ARRAY statements, as they are in Listing 4. Add the “missing” device to the devices entry for each array member to fill out the raid1 complement of two devices per array. Don't forget to renumber the md entries if the recovery computer already has md devices and ARRAY statements in /etc/mdadm.conf.
```You would need to specify your local disks in place of the examples, but you should be able to build a mdadm.conf file while in LiveCD mode and test the ability to access the data.  I recommend a backup of /etc regardless and that you make that backup while in the LiveCD session.  I would not do a reinstall until I could build a proof of concept access in the LiveCD environment.

  I am trying to get into the live CD but cant.  It would boot from the CD until the point i get to pick "install" or "try ubuntu".  I click on Try Ubuntu and it show me a black screen with the cursor in the middle then shortly after just rebooted my machine.  I've tried this about 5 times already and it just going into the described loop :(

---

### Post by blueridgedog on 2011-10-14
Which LiveCD?

---

### Post by sumasage on 2011-10-14
11.04.  Now i'm trying 11.10

---

### Post by sumasage on 2011-10-14
Ok so i am able to login the LiveCD 11.10 and able to start my raid array successfully.    However i am unable to access my data to do backup on the RAID due to permission.  How can i fix this?  It said the owner:group is 1000:1000  I can access the data via terminal when doing sudo -i (root).  How can i get it so i can access the info in GUI?  much easier to do backup since i have to divide the data into multiple external drives.

---

### Post by CharlesA on 2011-10-14
Is Nautilus installed on 11.10?

Run gksu nautilus from a terminal.

---

### Post by sumasage on 2011-10-16
I was able to grab the config file using nautilus.  I reinstalled Ubuntu 11.10, put the info into the mdadm.conf file and the array worked just fine.  No data lost.    Thanks for the helps guys.

---

