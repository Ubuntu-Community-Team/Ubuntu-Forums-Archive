---
title: "Recover Data from quick formatted DVD-RW and +RW.....Please help!!!"
date: 2011-03-26
forum: General Help
---

### Post by kaisar89 on 2011-03-26
Hi everyone.

can someone help please. I am new to ubuntu. 

heres the situation. i was on windows 7 32 bit, computer was running slow with viruses and full hard drive so i installed ubuntu 10.10 32 bit as i believe it to be more secure. Before installing Ubuntu OS I made a backup DVD-RW data disk, it had my brothers holiday pics when he went turkey and morroco. once i installed ubuntu i needed a DVD-RW and quick formatted the wrong disk.

[SIZE=4]is it possible to recover the data? [/SIZE]ive read somewhere that the data is possibly can be recover. 

Please help, hes going to kill me. :(

---

### Post by kaisar89 on 2011-03-26
Bump, 29 views no reply.:(

please help.

---

### Post by linuxuser12345 on 2011-03-26
I have heard of a program for Microsoft Windows that recovers old data, called Recuva. Why don't you look it up and try it on somebody's computer. I hope for the best! :)

Also, try reading about Data Recovery on Wikipedia: [http://en.wikipedia.org/wiki/Data_recovery](http://en.wikipedia.org/wiki/Data_recovery)
[http://en.wikipedia.org/wiki/Undelete](http://en.wikipedia.org/wiki/Undelete)

---

### Post by linuxuser12345 on 2011-03-26
Hey! I just found a program that might work! It is called PhotoRec. You can give it a try!
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

You can also go to the Ubuntu Software Center, and download and install the "Partition Scanner and Disk Recovery Tool". This might work, also

---

### Post by newbuntuxx on 2011-03-26
Yes it is possible.

Install testdisk:

```
sudo apt-get install testdisk
```

Before you run testdisk, you must first backup an image of the DVD, in case your DVD gets damaged. To do so, you will need to insert your DVD into the drive. Then make sure that it is unmounted like this:

```
sudo umount /dev/cdrom
```

Now, you need to use the dd command to create backup image of the DVD like this:

```
sudo dd if=/dev/cdrom of=~/backup.img bs=512 conv=notrunc,noerror
```

This will create a raw image file backup of your DVD. The raw image file will be placed in your home directory, which is located in (/home/yourname/). The file is called "backup.img". It is important that you keep that file and not delete it until all pictures are recovered. Your DVD can not be mounted when this is happening. Once the back-up image is created, you can now start the recovery process.

Mount the cdrom again like this:

```
sudo mount /dev/cdrom
```

Now, you need to create a directory to store all of the recovered files, so use terminal like this:

```

cd ~
mkdir dvdbackup
cd dvdbackup

```

Then run:

```
sudo photorec
```

This will show you a list of all your mounted disk/cd similar to this:

```
Disk /dev/sdb - 160 GB / 149 GiB (RO) - ATA ST3160812AS
Disk /dev/sr0 - 654 MB / 624 MiB (RO) - HL-DT-ST DVDRAM GE20LU10
```

- Now, use the arrows to select the DVD/CD rom (/dev/sdr0 normally) and click on proceed.
- Select Intel and hit enter
- On the next screen select file Opt
- Make sure that all the options have an X in them. You can put an X using the space bar
- Then click b to save the settings
- Then click Q to go back
- Now select search
- It will ask you for the partition type, select other
- It will then ask you the following: Do you want to save recovered files in /home/yourname/dvdbackup ? [Y/N] Click Y
- and it will start the backup process
- The recovered files will be placed in different directories in /home/yourname/dvdbackup/recup_dir
- Please note that the file names will be changed, and directory structure will be lost. But the files will be recovered nonetheless
- Once the recovery process is done, you will get a similar output to this:
```
191 files saved in /home/yourname/dvdbackup/recup_dir directory.
Recovery completed.
jpg: 191 recovered

```
Of course, your output will be different. 

- Select quit and hit enter. Quit again and enter
- You can now open the file browser and browse to that directory: Click on the Places menu - Home Folder, and find dvdbackup, double click it and you should hopefully find all of your brother's pictures there.



let me know how things go..

---

### Post by newbuntuxx on 2011-03-26
Quick question: Did you just format or did you also write new DATA to the DVD?

---

### Post by kaisar89 on 2011-03-26
> **newbuntuxx said:**
> Quick question: Did you just format or did you also write new DATA to the DVD?


Sorry for late reply, i did a quick format, so hopefully the data can be recovered.
Thanks for the help so far. Any further help much appreciated. 

By far the best forum. surprised by the amount of replies, other forum you get 1 reply if your lucky.:KS

---

### Post by kaisar89 on 2011-03-26
> **newbuntuxx said:**
> Yes it is possible.

Install testdisk:

```
sudo apt-get install testdisk
```Before you run testdisk, you must first backup an image of the DVD, in case your DVD gets damaged. To do so, you will need to insert your DVD into the drive. Then make sure that it is unmounted like this:

```
sudo umount /dev/cdrom
```Now, you need to use the dd command to create backup image of the DVD like this:

```
sudo dd if=/dev/cdrom of=~/backup.img bs=512 conv=notrunc,noerror
```This will create a raw image file backup of your DVD. The raw image file will be placed in your home directory, which is located in (/home/yourname/). The file is called "backup.img". It is important that you keep that file and not delete it until all pictures are recovered. Your DVD can not be mounted when this is happening. Once the back-up image is created, you can now start the recovery process.

Mount the cdrom again like this:

```
sudo mount /dev/cdrom
```Now, you need to create a directory to store all of the recovered files, so use terminal like this:

```

cd ~
mkdir dvdbackup
cd dvdbackup

```Then run:

```
sudo photorec
```This will show you a list of all your mounted disk/cd similar to this:

```
Disk /dev/sdb - 160 GB / 149 GiB (RO) - ATA ST3160812AS
Disk /dev/sr0 - 654 MB / 624 MiB (RO) - HL-DT-ST DVDRAM GE20LU10
```- Now, use the arrows to select the DVD/CD rom (/dev/sdr0 normally) and click on proceed.
- Select Intel and hit enter
- On the next screen select file Opt
- Make sure that all the options have an X in them. You can put an X using the space bar
- Then click b to save the settings
- Then click Q to go back
- Now select search
- It will ask you for the partition type, select other
- It will then ask you the following: Do you want to save recovered files in /home/yourname/dvdbackup ? [Y/N] Click Y
- and it will start the backup process
- The recovered files will be placed in different directories in /home/yourname/dvdbackup/recup_dir
- Please note that the file names will be changed, and directory structure will be lost. But the files will be recovered nonetheless
- Once the recovery process is done, you will get a similar output to this:
```
191 files saved in /home/yourname/dvdbackup/recup_dir directory.
Recovery completed.
jpg: 191 recovered

```Of course, your output will be different. 

- Select quit and hit enter. Quit again and enter
- You can now open the file browser and browse to that directory: Click on the Places menu - Home Folder, and find dvdbackup, double click it and you should hopefully find all of your brother's pictures there.



let me know how things go..

sorry for lame questions, 

but where do i download 'testdisk' from? 
And where do i enter these codes?

---

### Post by newbuntuxx on 2011-03-26
Generally speaking on this forum, whenever you see commands quoted in the code tag, it means that they are to be used in the terminal (command line). To open the terminal, click on Applications - Accessories - Terminal.

The command:

```
sudo apt-get install testdisk
```

Will download and install testdisk for you. You run that command in terminal of course.

PS.
There are no lame questions. If you don't know what a command does or where to use it, feel free to ask.

---

### Post by newbuntuxx on 2011-03-27
Since you are not too familiar with the way programs are downloaded and installed on Ubuntu, I think I should give you a small introduction. 

Unlike in Windows, where you must visit many different sites and locations on the Internet in order to download the software that you want, in Ubuntu, everything is found in one place: The repositories (this is true for 99% of the software). 

This is because almost all of the software in the linux world and the ubuntu world is open-source/free. So, the care takers of the Ubuntu distribution group all that software in one place and make it available to download and install using the apt program (its a package management tool).

Anyways, read this for more information:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by kaisar89 on 2011-03-30
> **newbuntuxx said:**
> Yes it is possible.

Install testdisk:

```
sudo apt-get install testdisk
```Before you run testdisk, you must first backup an image of the DVD, in case your DVD gets damaged. To do so, you will need to insert your DVD into the drive. Then make sure that it is unmounted like this:

```
sudo umount /dev/cdrom
```Now, you need to use the dd command to create backup image of the DVD like this:

```
sudo dd if=/dev/cdrom of=~/backup.img bs=512 conv=notrunc,noerror
```This will create a raw image file backup of your DVD. The raw image file will be placed in your home directory, which is located in (/home/yourname/). The file is called "backup.img". It is important that you keep that file and not delete it until all pictures are recovered. Your DVD can not be mounted when this is happening. Once the back-up image is created, you can now start the recovery process.


Hi, Im currently following the tutorial you gave me, im not to sure if im carrying out the process correctly. So far its taken 2 hours to make an images in my home directory and still going. should this happen or have i done something wrong? 

0+0 records in 
0+0 records out
0 bytes (0 B) copied **[COLOR=Red]7405.22 s,[/COLOR]** 0.0 k/Bs
dd: reading '/dev/cdrom': input/output error

Same script is continuing with number increasing each time. What is happening? Could someone please explain.

Thank You..

---

### Post by newbuntuxx on 2011-04-01
Sorry for the late reply.

This is most likely because we got the device name wrong. I want you to put a regular Cd/DVD in your drive (something that contains data). Then browse to the CD/DVD using the file browser.

Then open terminal and run:

```
mount
```

That command will list all your mounted file systems. Copy and paste the output here. 

Most likely your device name is: /dev/sr0, but we'll be able to tell from the output of mount.

---

