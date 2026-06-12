---
title: "How can I make a iso image?"
date: 2010-04-14
forum: General Help
---

### Post by keithg67 on 2010-04-14
I want to make a iso image of my current install of ubuntu 9.10 I would like to do this so if i mess something up again I dont have to start all over installing and un-installing things. basically I just want a installable iso image of my current install of 9.10 that is on my netbook now.

Thanks in advance,
Keith

---

### Post by sxmaxchine on 2010-04-14
I have never used it before but you might like to try [this.]("http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22")

---

### Post by Drenriza on 2010-04-14
1. Insert the CD or DVD that you want to make an ISO image of.

2. Open a terminal window.

3. Execute the following command:
cat /dev/scd0 > /home/shamanstears/test.iso


where /dev/scd0 is the device name for your drive (to find this, go to the Main Menu, click on System, mouseover Administration and select System Monitor. Click the File Systems tab. The device name will be listed in the Device column). Also make sure to change the path and iso filename to the desired path and filename.

The disc will begin to spin and the ISO image will start being constructed. Once it has completed, you have an ISO image of your CD. To verify that the image was properly created, mount the ISO file and check the contents.

---

### Post by keithg67 on 2010-04-14
Thanks guys thats exactly what I was looking for.

---

