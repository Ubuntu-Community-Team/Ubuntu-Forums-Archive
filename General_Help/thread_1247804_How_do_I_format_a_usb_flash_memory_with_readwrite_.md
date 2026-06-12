---
title: "How do I format a usb flash memory with read/write permissions?"
date: 2009-08-23
forum: General Help
---

### Post by tomasrey88 on 2009-08-23
Hi,

I want to reformat a USB Flash memory in FAT32 format with read/write permissions. How would I do it? I tried to do so and failed miserably. The USB Flash would only read, but not write. I've given up trying to make it read/writable. So, I'm going to reformat it, correctly this time. I have my data backed-up, so I can do this. 

What I did last time (the wrong way) was use GParted to reformat it as a primary partition, FAT32, rounded to cylinders. Then, I just plugged it into my computer and started using it. However, this didn't work and resulted in a week long unsuccessful attempt to fix it: [http://ubuntuforums.org/showthread.php?t=1242310](http://ubuntuforums.org/showthread.php?t=1242310) . 
Another poster said to give it permissions at the beginning when you first mount it. However, this is impossible to do since the computer immediatly recognizes the USB Flash and automatically mounts it. 

[B]Please tell me how to format a USB Flash memory with read/write permissions. 

[/B]Thanks,
:P

---

### Post by scouser73 on 2009-08-23
Firstly you'll need **GParted**, go to **Synaptic Package Manager**, search for **GParted**, install it.  Once installed go to **System** > **Administration** and select **Partition Editor**.

Insert the USB Flash drive, use the drop down menu on the top right of the screen to find the USB Flash drive, click **Partition** at the top of the screen, scroll to **Unmount**, then click **Device**, click **Create Partitiion Table** and run though the options that suit the filesystem that you want to install.  Once you've done that click **Apply** for the changes to take affect.

Now you need to go to Terminal and enter this command **gksudo nautilus** this will open up as Root, navigate your way to the USB Flash drive and then right click, select **Properties** then **Permissions**, click the drop down menu, scroll to your name and select then do the same for the **Group** drop down menu.

You will now have full read & write permissions for the USB flash drive.

---

### Post by mike555 on 2009-08-23
also they have USB thumbdrives that have a tiny switch for read/write to read only ...like these...   [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141486](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141486)   ... very good if you need to use then on someone else's computer so you don't get viruses from their computer .....

---

### Post by skyjacker on 2009-08-23
You need to have a "persistant file in the usb.  Go to this link - it gives you every thing you need.  [HTML]http://www.pendrivelinux.com/category/flashdrive-installs-using-linux/[/HTML]

---

### Post by loomsen on 2009-08-23
Hello.

You need to add a line to your /etc/fstab to define defaults for FAT32 devices. This could look something like

```

#DEVICE     MNT-POINT    FS-TYPE      OPTIONS
/dev/usb  /mnt/usb        vfat       rw,user  0 0

```

This would grant permissions to all users to (un-)mount $DEVICE with given $OPTIONS at given $MNT-POINT

Just stumbled upon...

gconf-editor

browse to 
system &#8594; storage &#8594; default_options &#8594; vfat

and add your options there

---

### Post by tomasrey88 on 2009-08-23
[http://ubuntuforums.org/showthread.php?t=1242310](http://ubuntuforums.org/showthread.php?t=1242310)
I applied all of scouser73 's advice AND the advice from the kind posters in the above thread and it worked. 

Thanks.

---

