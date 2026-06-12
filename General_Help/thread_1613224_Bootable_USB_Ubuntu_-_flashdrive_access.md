---
title: "Bootable USB Ubuntu - flashdrive access"
date: 2010-11-04
forum: General Help
---

### Post by gozo45 on 2010-11-04
Hi,

I'm using Ubuntu 10.10 installed on USB. My problem is, that when I want to access USB flashdrive from which is Ubuntu running I can only see it mounted as cd-rom. So I cannot write to any documents I have on flashdrive.

I found this post [http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/](http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/) but it's working only for Ubuntu 9.10

Could please someone step by step explain how to do this.

Thank you.

Peter

---

### Post by viralmeme on 2010-11-04
> **gozo45 said:**
> when I want to access USB flashdrive from which is Ubuntu running I can only see it mounted as cd-rom. So I cannot write to any documents I have on flashdrive

Assuming you are using the usb-creator, boot from a live CD and install to the USB, delete the file casper-rw, resize the FAT partition down to about 600MB and create two new ext2 partitions in the remaining space, label them home-rw and casper-rw. When you boot from the USB any changes will be stored there.

---

### Post by gozo45 on 2010-11-05
Thank you viralmeme,

how big should be these partitions?
I'am using 8GB flashdrive with 3GB casper file, so cesper-rw partition should have 3GB but how big should be home-rw? 

Thank you.

---

### Post by viralmeme on 2010-11-06
> **gozo45 said:**
> how big should be these partitions?

Resize the FAT partition down to about 600MB, then allocate the remaining as you see fit. Any new software installations will occupy casper-rw, so you could make this about 6GB, the remaining to home-rw. I only use home for config files so mine isn't that big. Here's mine on a 4GB device.

/dev/sdb1             566M  /cdrom
/dev/sdb3            1008M  /home
/dev/sdb2             2.2G  /media/casper-rw

---

### Post by gozo45 on 2010-11-06
OK, I was not clear, my fault. In your Example there is also 600 MB part which will be visible as CD-Rom in Ubuntu. What I want is to have around 3GB from 8GB flashdrive just for Ubutnu (programs, config etc.) and other 5 GB should be normal FAT accessible from Ubuntu and also from Windows. Problem is that Ubuntu always see this part as CD-Rom so I cannot for example edit one document from Windows or from Ubuntu.

---

### Post by efflandt on 2010-11-06
If you boot to a live/install iso usb, don't you find your 8 GB flash drive itself in **Places**?  From that you should be able to access the FAT32 part of it that is not being used by the iso and casper-rw.

---

### Post by gozo45 on 2010-11-09
No, It's mounted as CD-Rom so I have no chance to write anything to it.

---

### Post by gozo45 on 2010-11-11
Please, help somebody this is exactly same issue as is solved here  [http://www.pendrivelinux.com/sharing...e-and-windows/]("http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/") but i need similar guide for Ubuntu 10.10

---

