---
title: "missing root partition"
date: 2010-07-02
forum: General Help
---

### Post by tropdoug on 2010-07-02
Thsi is really wierd. I have a desktop with two hard drives. sda is supposed to have the oS on it, and sdb /home a music partition and a photograph partition. When I went into gparted to do something I found that sda apparantly is not even formatted and sdb does not have any OS on it. That is bizarre becuase obviously the puter is sowrking. This is what I get from blkid ```
/dev/sda5: LABEL="OS" UUID="68d7e3bc-5092-4858-819e-361f36a031cf" TYPE="ext4" 
/dev/sda6: LABEL="Opt" UUID="f229d6f0-b52a-4ba3-ad1a-05c076b4df6b" TYPE="ext4" 
/dev/sda7: UUID="0da8def9-7f75-4d03-8789-f88454df0204" TYPE="swap" 
/dev/sdb1: LABEL="Music" UUID="6875d601-79d5-4418-9876-2e8a12e6e31f" TYPE="ext3" 
/dev/sdb2: LABEL="PhotoPart" UUID="4778f442-6b61-42f2-b30e-07e1abe837c4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: LABEL="MyFiles" UUID="ad53d4bf-562e-47de-8ff4-4cdfb50d01b1" TYPE="ext4" 

```

have a look at the two screen shots. 

Things seem to be okay but now I am wondering where my OS is actually loaded, and do I have maybe a developing HD problem?

---

### Post by Rubi1200 on 2010-07-02
Hi,
offtopic: didn't you recently have a HDD die on you?

Anyway, if you have an Ubuntu CD I suggest you boot the computer with it and go to live mode and then click on the link at the bottom of my post. Follow the instructions there and post the results back here so someone can take a look and advise you.

---

### Post by dino99 on 2010-07-02
> **tropdoug said:**
> Thsi is really wierd. I have a desktop with two hard drives. sda is supposed to have the oS on it, and sdb /home a music partition and a photograph partition. When I went into gparted to do something I found that sda apparantly is not even formatted and sdb does not have any OS on it. That is bizarre becuase obviously the puter is sowrking. This is what I get from blkid ```
/dev/sda5: LABEL="OS" UUID="68d7e3bc-5092-4858-819e-361f36a031cf" TYPE="ext4" 
/dev/sda6: LABEL="Opt" UUID="f229d6f0-b52a-4ba3-ad1a-05c076b4df6b" TYPE="ext4" 
/dev/sda7: UUID="0da8def9-7f75-4d03-8789-f88454df0204" TYPE="swap" 
/dev/sdb1: LABEL="Music" UUID="6875d601-79d5-4418-9876-2e8a12e6e31f" TYPE="ext3" 
/dev/sdb2: LABEL="PhotoPart" UUID="4778f442-6b61-42f2-b30e-07e1abe837c4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: LABEL="MyFiles" UUID="ad53d4bf-562e-47de-8ff4-4cdfb50d01b1" TYPE="ext4" 

```

have a look at the two screen shots. 

Things seem to be okay but now I am wondering where my OS is actually loaded, and do I have maybe a developing HD problem?

/sda5 is where your OS is, check the uuid with fstab
Gparted show a problem with sda, the question is: which of the sda partition or gparted have a problem ?

you can first force a fsck on reboot:
sudo shutdown -r now

or check the sda booting on partedmagic for example

---

### Post by tropdoug on 2010-07-02
Yes I did - and you helped me there too, thanks :-) that was in the laptop -- now with new 160Gig HDD all is up and running well with it. 

This is the desktop, and as I said it's weird because the system is running fine, yet according to GParted there aint a system on here. ??

---

### Post by oldfred on 2010-07-02
Gparted seems to be finicky. I had a windows partition and it would not show the drive. After I ran checkdisk then it came right up.

If you have other partition issues:
Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by tropdoug on 2010-07-06
Well it seems that this thread [http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html) was indeed what was wrong with my partitions. But I also had an issue because the main partition did not start on a cylinder boundary. When I followed all the steps it could not actually fix it. and neither could the program he mentions in there. 

So after trying and not getting a result the final solution was to wipe it and clean install, being very careful about how I split the drive up. So I guess the issue is solved but not in the way I would have hoped for. Anyway there doesn't seem to be a clear reason, so I hope I don't see it again
Thanks for the help everyone.

---

