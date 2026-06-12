---
title: "Installation Help"
date: 2006-03-24
forum: General Help
---

### Post by new2linux2009 on 2006-03-24
Hi, I'm trying to install dual boot for Windows XP professional and Ubuntu Breezy Badger v. 5.10.  Also, I created a 10 GB partition on a 40 GB hard drive with Partition Magic and I was wondering how to install Ubuntu on this partition.  The only instructions I could find created a new partition, but I am all ready one step ahead of the game...](*,)  PLEASE guide me through the install...I would reallly like to start using Ubuntu today...I am sick of windows...:-D ...but will need it for school because I go to a Laptop school

---

### Post by KansasJoe on 2006-03-24
when you get to the partitioner then select manually edit partition tables and select the one you've got set aside and set it for /    then make a swap partition and you're good to go.....may also want a /home but that's up to you

---

### Post by PhoenixP3K on 2006-03-24
Well, if you already partitionned your disc. It's going to be easy.
Put the install CD in. Then reboot the computer. At one point you'll get to partition disk. Now you be carefull and ask Ubuntu to install on the 10GB partition you created earlier. It will format it to ext3 and will create a swap partition as well.
This might help : [http://www.pcmech.com/show/os/903/](http://www.pcmech.com/show/os/903/)

---

### Post by akshaysrinivasan on 2006-03-25
so you must be already having windows and partition magic.taht makes things altogether more easier.now boot into windows xp and create a new partition witha size of about 500MB and format it with linux swap.Format the 10 GB partition in ext3,this makes it easier to recognise the partition when you start setup.now reboot the computerand install ubuntu with the 10 GB partition as /(root partition)

---

