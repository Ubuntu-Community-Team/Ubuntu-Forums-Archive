---
title: "Recover /home after wrong format"
date: 2012-04-03
forum: General Help
---

### Post by paapereira on 2012-04-03
Last night, while installing Ubuntu from a live usb stick, I wrongly chose ext3 instead of ext4 as the partition for my /home partition in /dev/sdb1.

By doing this the format option was selected. But I only realize that when I saw that the partition was being formated in the installer.

I didn't reboot the machine yet and I'm still in a usb live usb stick.

Is there a way to recover my ext4 partition? :(

Any help is appreciated. Really depressed about this..


Thanks in advance.

---

### Post by sudodus on 2012-04-03
> **paapereira said:**
> Last night, while installing Ubuntu from a live usb stick, I wrongly chose ext3 instead of ext4 as the partition for my /home partition in /dev/sdb1.

By doing this the format option was selected. But I only realize that when I saw that the partition was being formated in the installer.

I didn't reboot the machine yet and I'm still in a usb live usb stick.

Is there a way to recover my ext4 partition? :(

Any help is appreciated. Really depressed about this..


Thanks in advance.
I don't understand your problem.

- Are you overwriting (or afraid to overwrite) something valuable, private data or an old and well configured operating system?

- Are you installing your /home in the wrong place, but there is nothing there now?

- Are you also installing your new system / where you have your /home with all your private files and configurations? So that you have swapped the location of / and /home?

- Or were you simply selecting the file system ext3 instead of ext4 for the /home partition in the correct device? I think it is a good alternative to have ext3 for the /home.

---

### Post by paapereira on 2012-04-03
> **sudodus said:**
> I don't understand your problem.

- Are you overwriting (or afraid to overwrite) something valuable, private data or an old and well configured operating system?

- Are you installing your /home in the wrong place, but there is nothing there now?

- Are you also installing your new system / where you have your /home with all your private files and configurations? So that you have swapped the location of / and /home?

- Or were you simply selecting the file system ext3 instead of ext4 for the /home partition in the correct device? I think it is a good alternative to have ext3 for the /home.

Thanks for your reply. Really appreciate it.

To clarify my situation:
- I have a SSD drive (/dev/sda) where my / partition is -> ext4
- I have a HHD drive (/dev/sdb) where I have the swap (/dev/sdb1) and my /home (/dev/sdb5) -> ext4.

I was installing Ubuntu 11.10 from a live usb stick. I entered the live session and started the installation from there.

My goal was to format the / partition and mount the /home partition without formatting.

Accidentally I chose ext3 instead of ext4 for /home causing the partition to be formatted.

All my data is there and my hope is that there's a way to recover my files. 

Since the installer formatted the partition, I imagine there is data lost, but I'd to recover as much as possible, ideally(!) remount as ext4 and my /home is magically there.

Answering your questions:

> **sudodus said:**
> 
- Are you overwriting (or afraid to overwrite) something valuable, private data or an old and well configured operating system?


My /home was overwritten by the installer. Haven't reboot the system yet. Still on the live session.

> **sudodus said:**
> 
- Are you installing your /home in the wrong place, but there is nothing there now?


Correct place, but formatted with ext3 instead of the original ext4.

> **sudodus said:**
> 
- Are you also installing your new system / where you have your /home with all your private files and configurations? So that you have swapped the location of / and /home?


/ is in another drive.

> **sudodus said:**
> 
- Or were you simply selecting the file system ext3 instead of ext4 for the /home partition in the correct device? I think it is a good alternative to have ext3 for the /home.


Yes. I selected ext3 instead of the original ext4 and formatted.


Again thanks for the reply.

---

### Post by sudodus on 2012-04-03
Now the big question is if you really started the formatting or if you have only 'put formatting on the to-do list'. Let us hope it is only on the to-do list.

If you formatted the drive, if it was some kind of quick format, the file system table is wiped, but the file data are still there. Otherwise the file data should be wiped.

I think it is hard to know the real situation without using some kind of analyzing and/or repair tool.

Try Testdisk and Photorec! You find them on the internet in several versions. You should run them booted from another drive, for example a CD or USB drive. So either you boot from your Ubuntu install drive and 'test Ubuntu'. When it is running you can install testdisk
```
sudo apt-get install testdisk
```
or you can download the iso file of one of the repair CDs with Testdisk and PhotoRec.

---

### Post by paapereira on 2012-04-03
It must have been formatted because Ubuntu installation ended...

I'll try testdisk to change ext3 to ext4 and try to rebuild the filesystem. Don't know if it will work because of the installation... :(

Not at home right now, so I'll try at night.

Many thanks for your help.

---

### Post by sudodus on 2012-04-03
Good luck and come back if you need more help. If I won't be around there will be others that can help you.

---

### Post by winh8r on 2012-04-03
It might be of some help to you to read the TestDisk wiki which is here:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

If you are unsure about any of the steps, ask a question** before** you proceed.


Hope this helps you.

---

### Post by paapereira on 2012-04-03
> **winh8r said:**
> It might be of some help to you to read the TestDisk wiki which is here:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

If you are unsure about any of the steps, ask a question** before** you proceed.


Hope this helps you.

Thanks. 

I'm at work right now, but I'm guessing that in testdisk I will see the ext3 partition with the newly installed /home.

Then I'll try the Deeper Search and hope to see the ext4 partition and list the files there. 
If that's my /home then I will change the status to Logical and write the partition table.

After this, still in the usb live session, I'll try and mount the device:
sudo mount /dev/sdb5 /mnt

Hopefully I can the copy my files to an external hard drive.

Am I thinking right? 


You guys rock! Thanks for the help.

---

### Post by ventrical on 2012-04-03
> **paapereira said:**
> Thanks for your reply. Really appreciate it.

To clarify my situation:
- I have a SSD drive (/dev/sda) where my / partition is -> ext4
- I have a HHD drive (/dev/sdb) where I have the swap (/dev/sdb1) and my /home (/dev/sdb5) -> ext4.

I was installing Ubuntu 11.10 from a live usb stick. I entered the live session and started the installation from there.
.

I'm all for helping others but this is beta testing for Precise Pangolin 12.04.

---

### Post by philinux on 2012-04-03
Moved to General Help.

---

### Post by paapereira on 2012-04-03
Sorry for the misplaced post.

My ordeal started with the installation of 12.04. After a kernel update my machine didn't boot so I reinstalled 11.10.

And here I am with my data gone :(

---

### Post by philinux on 2012-04-03
> **paapereira said:**
> Sorry for the misplaced post.

My ordeal started with the installation of 12.04. After a kernel update my machine didn't boot so I reinstalled 11.10.

And here I am with my data gone :(

Good luck with testdisk and photorec. Photorec could recover your files.

Search these forums for photorec and research how to use it.

---

