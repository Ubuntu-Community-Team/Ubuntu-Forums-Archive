---
title: "Deletion of Windows; Partitions Help"
date: 2012-05-30
forum: General Help
---

### Post by TheKingOfComputers on 2012-05-30
Ok, so I have installed Ubuntu 11.10 (about to upgrade to 12.04) and I would like to know how to delete Windows. I used Wubi to dual-boot Ubuntu and Windows Vista. My system is running EXTREMELY slow despite all my efforts to make it faster (virus scanning, high-performance setting, etc) and I have come to the conclusion that it is because Windows is using up all my memory. Almost 70 gb. is being used up by an operating system which I will no longer be using.

THE MAIN QUESTION: How do I delete the Windows partitions on my laptop and divvy my new-found memory to Ubuntu?

Additional info:
Windows Vista dual boot via Wubi with Ubuntu 11.10 installed
Intel Celeron chip
Almost 4 years old (cant afford new computer yet :()

Dont worry about me backing up things because there is nothing on Windows I wont be able to recover on Ubuntu.

---

### Post by kanikilu on 2012-05-30
Someone correct me if I'm wrong, but I think if you used wubi to install Ubuntu, you can't just delete or recover the space that Windows is taking. This is because with wubi, Ubuntu is on the same partition as Windows, so of course deleting that partition, will also remove Ubuntu...

A quick search brings up one option to move a wubi install to a "real" partition. I've never done it, but it looks somewhat advanced:

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Personally, I'd just back up my data (in a perfect world, important data is already backed up) and start with a fresh install of Precise.

---

### Post by VE6EFR on 2012-05-30
Even though I am a beginner with Ubuntu and there may be an easier way of doing things that I am not aware of, I agree with kanikilu. I would backup the data I wanted to keep and then reinstall Ubuntu from the live install CD selecting the option to replace windows.

Someone with more experience may come along and give a better way of doing things so you may want to hold off a little before you start.

---

### Post by ytkuser12 on 2012-05-30
i'm new but i just did this i booted with a live usb stick and did a install and told ubuntu what i wanted to do it took all of about 30 min maybe less and i was done. relatively painless and my old pc runs better as well. may i also offer a suggestion if your use to windows the fonts differences may cause some eye strain you can install MS cor fonts from this command in terminal sudo apt-get install msttcorefonts. you can change themes and font from installing advanced setting from ubuntu software center. just a head up for yeah.

---

### Post by TheKingOfComputers on 2012-05-30
Ok I will try moving the partition because I dont want to spend another 4 hrs like my first install trying to create a new partition then keep updating until 12.04 because the wubi from Ubuntu page keeps giving error. Plus I dont have live cd.

---

### Post by VE6EFR on 2012-05-30
Here is a step by step guide that will help you to create a live CD

[http://www.ubuntu.com/download/help/burn-a-cd-on-ubuntu](http://www.ubuntu.com/download/help/burn-a-cd-on-ubuntu)

Or if you would prefer to install via a USB stick

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

---

### Post by deadflowr on 2012-05-30
If you are truly thinking of completely wiping out your windows install, then the best way would be to download the latest ubuntu iso image from ubuntu.com and burn it to a cd. Then when you install choose the option to install over everything. This option will set the whole disk as one giant partition and wipe out windows.
However, if you want to configure your own partitioning scheme, choose "something else". Hopefully, you'll have read up on this.
A full wipe/install is probably the best option for you at this point, as messing around with making partitions can be more in need of detailed attention.

---

### Post by ytkuser12 on 2012-05-30
> **deadflowr said:**
> If you are truly thinking of completely wiping out your windows install, then the best way would be to download the latest ubuntu iso image from ubuntu.com and burn it to a cd. Then when you install choose the option to install over everything. This option will set the whole disk as one giant partition and wipe out windows.
However, if you want to configure your own partitioning scheme, choose "something else". Hopefully, you'll have read up on this.
A full wipe/install is probably the best option for you at this point, as messing around with making partitions can be more in need of detailed attention.

I agree i messed up the first time i tried to unpartition windows and had to re-install from scratch, doing it from scratch is the best option.

---

### Post by TheKingOfComputers on 2012-05-31
I used your suggestion Deadflower, and Windows Vista is officially gone. I downloaded the iso image (which took 4 hours -_- ) and wiped it. Thank you.
I definitely like Ubuntu 12.04 far better than Windows. Good choice I made.

---

### Post by ytkuser12 on 2012-05-31
glad you like ubuntu i turned my old pc into my ubuntu box,my new computer for gaming comes today :).

---

