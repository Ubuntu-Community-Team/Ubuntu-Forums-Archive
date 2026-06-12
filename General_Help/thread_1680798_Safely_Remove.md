---
title: "Safely Remove"
date: 2011-02-03
forum: General Help
---

### Post by phanie on 2011-02-03
What is the equivalent terminal command of the "safely remove hardware"?

---

### Post by sikander3786 on 2011-02-03
Simply un-mount your intended partition.

```
sudo umount /media/disk
```

Refer here.

[http://ubuntuforums.org/showthread.php?t=1365343](http://ubuntuforums.org/showthread.php?t=1365343)

---

### Post by phanie on 2011-02-03
Thank you so much!!

---

### Post by phanie on 2011-02-04
then again,i dont think that umount is the answer. umount is not the same as safely remove. I dont know what else is going on inside the system after safely removing a device but all i know i that the lights of the device go off when it is safely removed. But when i use u mount the lights are still on and it still can be seen in the places tab which is a big problem for the software i am creating. Please guys, give me something here.

---

### Post by ronnielsen1 on 2011-02-04
Right click on the device's icon and click [COLOR=Blue]Safely Remove Drive[/COLOR]

---

### Post by timgood on 2011-02-04
> **ronnielsen1 said:**
> Right click on the device's icon and click [COLOR=Blue]Safely Remove Drive[/COLOR]

If you read the Topic title he is referring to terminal commands that are equivalent to 'Safely Remove'.

Unmounting the drive is the equivalent according to this post on the Community Documentation:

> Before disconnecting devices, you must unmount them first. This is similar to "Safely Remove" in Windows in that the device won't unmount until data is finished being written to the device, or until other programs are finished using it. This applies to all types of storage devices, including flash drives, flash cards, external hard drives, ipods and other media players, and even remote storage like Samba or NFS shares. 

You can find this information [here]("https://help.ubuntu.com/community/Mount/USB").

Hope this helps.

---

### Post by nothingspecial on 2011-02-04
To unmount my ipod I use ```
sudo umount /mnt/ipod && sudo eject /dev/sdh1
```

If I use one or the other, the ipod itself doesn`t say it`s ok to disconnect.

The combination of the 2 works though.

---

### Post by phanie on 2011-02-06
thanks guys for the reply!you're a lot of help. thanks also for blowing off ronnielsen1. =)

---

### Post by SpikeBzzz on 2011-02-22
Hello!

Does anybody know why do I get this message, everytime I press "Safely remove drive" on my External Harddrive? Does it damage my disk?
[COLOR=Green]
[COLOR=DarkOliveGreen][COLOR=Sienna]Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or direc[/COLOR]tory[/COLOR][/COLOR]

---

