---
title: "Install OS"
date: 2012-01-28
forum: General Help
---

### Post by HOUSEE on 2012-01-28
So, I want to install Ubuntu as my main OS and Windows as my second. Can anyone advise me how to do this?

---

### Post by blackhex666 on 2012-01-28
> **HOUSEE said:**
> So, I want to install Ubuntu as my main OS and Windows as my second. Can anyone advise me how to do this?

Sure first have Windows installed this will make youre life a lot easier next download ubuntu and install it use the option Install Alongside or somthing like that.This will install grub2 and from my last fight with dualboot ubuntu was main OS

---

### Post by benpack101 on 2012-01-28
I would go ahead and follow the directions on the [ubuntu page]("http://www.ubuntu.com/download/ubuntu/download")

I would suggest burning the iso to a cd (if you have a drive) or a usb (thats what I have always done).

You can either choose to install alongside, or manually decide the size of each partition (I always do that).

---

### Post by CC Inc on 2012-01-28
Yes, it is alot easier to have windows installed first, but it is possible to have it second. Just look at the link posted above.

---

### Post by HOUSEE on 2012-01-29
So, i-m trying to install ubuntu but im having trouble. Which option should I choose from this menu?

[IMG]http://img846.imageshack.us/img846/6208/screenshotat20120129182.png


I have 2 partitions, one with 262 GB where Windows 7 is installed and other with 488 GB, where I want to install ubuntu. If I choose the option Something else I come across with this

[IMG]http://img99.imageshack.us/img99/6208/screenshotat20120129182.png

By selecting the partition I want to install ubuntu, which is the one with 488 GB, selected on orange, I get an error No root file system is defined. Can anyone help me with this? I ve been looking on ubuntu s support page but I cant figure it out. I want to install ubuntu on that partition to dual boot with windows 7, installed on the other partition.

Thanks for any help.

---

### Post by Mark Phelps on 2012-01-29
Since you're using Win7, it would be best NOT to use the Ubuntu installer side-by-side option to shrink the Win7 OS partition.  Win7 is very finicky about changes being made to its filesystem from "outside" -- and doing this can result in filesystem corruption, rendering your Win7 OS unbootable.

Better approach is to do the following:
1) Boot into Win7 and use the Disk Management tool to shrink the OS partition.
2) Reboot into Win7 a couple of times to allow the filesystem to make any need adjustments.
3) Use the Backup feature in Win7 to create and burn a Win7 Repair CD.  This will prove invaluable later should you need to repair the Win7 Boot Loader from the dual-boot setup.

Also, if you want to be SURE that your Win7 setup is restorable, then do the following:
1) Download and install the FREE version of Macrium Reflect (MR)
2) Using MR, image off your Win7 setup to an external drive.
3) Use the MR option to create and burn a Linux Boot CD
NOW, you have the means to completely restore Win7, should you accidentally overwrite it during the dual-boot setup.

---

### Post by HOUSEE on 2012-01-29
Why do I have to shrink windows 7 partition? I have a Windows DVD that I can use as a recovery disk, I assume. 

I don't know anything about the MR. What I want to know is what I have to do to proceed with the instalation.

---

### Post by benpack101 on 2012-01-29
I believe what you must do is go to the "device for boot loader instalation" and change that to the correct partition.

Make sure you follow the directions regarding the mount point and all.

I'm a big fan of Lifehacker, [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

But I'm sure there are many other how-to guides out there.

---

