---
title: "access to hard-disk"
date: 2009-11-19
forum: General Help
---

### Post by banjoman on 2009-11-19
my laptop has 2 partitions, windows and linux (at present Mandriva),

the mandriva has crashed and I am going to take the opportunity to try out ubuntu, installing this over the linux partition

however...

there are some files I want to transfer from the linux partition before I re-install

for some reason I cannot get a Mandriva Live CD to start up, so am using a Ubuntu Live CD with only problem, I cannot access my folders on the linux partition, I just get an error message saying I do not have correct permissions

how can I get into these folders?

---

### Post by matrik22 on 2009-11-19
A simple search would have solved your problem. "mount linux partitions in windows"

---

### Post by bodhi.zazen on 2009-11-19
You can access the files when you boot the Ubuntu live CD. From there you can copy the files to your windows partition or a removable flash drive if you prefer.

---

### Post by banjoman on 2009-11-20
I have performed a simple search, but none of the messages seem to answer my specific problems

I have recently transfered from using windows and am used to GUI, but can use commands in a terminal window if I am provided with simple instructions(!)

I do not understand the advice from bodhi.zazen, need more specific instructions I am afraid

thanks

---

### Post by Locutus_of_Borg on 2009-11-20
access them as root

in ubuntu live cd, become root in terminal by entering 'sudo su'

then mount whatever you want to copy and also mount wherever you want to copy them to

then cp -r /mnt/mandriva/files_to_backup /mnt/windows/backed_up_files

etc

---

### Post by bodhi.zazen on 2009-11-20
> **banjoman said:**
> I have performed a simple search, but none of the messages seem to answer my specific problems

I have recently transfered from using windows and am used to GUI, but can use commands in a terminal window if I am provided with simple instructions(!)

I do not understand the advice from bodhi.zazen, need more specific instructions I am afraid

thanks

What part do you need help with ?

Put the ubuntu CD in the CD drive bay.

Reboot.

Mount your Mandriva partition.

Do you not know how to mount your partitions ?

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

```
sudo mkdir /media/mandriva
sudo mkdir /media/windows

sudo mount /dev/sdab /media/windows
sudo mount /dev/sdxy /media/mandriva
```

sdab = your wnidows partition, most likely /dev/sda1
sdxy = mandriva partition, most likely either /dev/sda2 or /dev/sda5

Copy to the files to back up location.

Do you now know how to copy files ?

Either copy with sudo cp -R /media/mandriva/files_to_copy /media/windows/location_to_copy_to


or use nautilus to drag and drop

```
gksu nautilus
```

---

### Post by banjoman on 2009-11-20
many thanks to authors of the above 2 posts, I have now copied the files I wanted and you have shown me how to do this both through a GUI and commands

---

