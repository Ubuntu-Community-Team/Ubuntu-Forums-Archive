---
title: "Move Ubuntu installation"
date: 2010-02-18
forum: General Help
---

### Post by p2ranger on 2010-02-18
I found a post once on how to move your Ubuntu installation. I can't find it any more and I am having trouble finding one that tells me what I want.

Does anyone know of any links to tutorials or something?

I currently have Ubuntu 9.04 server installed on a usb thumb drive and want to move it to a larger external usb drive. I don't have a CD drive on this computer, so I would prefer to not have to use the installation disk if I can avoid it. Although I know I can use Unetbootin to make another usb stick to boot from.

Thanks for your help

Jason

---

### Post by dcstar on 2010-02-19
> **p2ranger said:**
> I found a post once on how to move your Ubuntu installation. I can't find it any more and I am having trouble finding one that tells me what I want.

Does anyone know of any links to tutorials or something?

I currently have Ubuntu 9.04 server installed on a usb thumb drive and want to move it to a larger external usb drive. I don't have a CD drive on this computer, so I would prefer to not have to use the installation disk if I can avoid it. Although I know I can use Unetbootin to make another usb stick to boot from.

Thanks for your help

Jason

Unmount the USB drives:
```

sudo dd if=/dev/old_drive of=/dev_new_drive
```

---

### Post by p2ranger on 2010-02-19
Thanks for the reply. I'm a little confused. If I unmount the two drives, won't it make it so I can't run that command to copy the contents? The file system is currently running on the USB thumb drive that I want to copy from.

Thanks

Jason

---

### Post by C.S.Cameron on 2010-02-20
You need to boot and run the dd command from a third thumb drive, (or Live CD).

---

### Post by p2ranger on 2010-02-21
Well, it didn't work for me. I was able to create identical partitions, only bigger, on the new disk. Then I did the dd command with the drives unmounted. It said that it coppied the information. When I plugged it into the server and started it up, I selected the new drive to be used for boot up from the bios and then it just has a black screen with a cursor at the top. Nothing ever loads.

The only other option I can think of is to start all over again and reinstall ubuntu and everything else.

Any other things to try would be appreciated

Thanks

Jason

---

