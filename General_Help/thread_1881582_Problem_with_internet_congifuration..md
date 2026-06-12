---
title: "Problem with internet congifuration."
date: 2011-11-15
forum: General Help
---

### Post by linux_beg on 2011-11-15
Hey people. I'm new to all this linux thing. I'm trying Lubuntu's latest relase from a USB stick (not confident yet for full instalation), and I'm trying to set up my internet connection first of all (since i'm a beginner, you know how important will be for me to have an internet connection). The problem is that I don't know how! I have a wireless connection on my Windows-XP, and i thought it was going to be easy (you know, it detects all the networks in my enviroment, i select the one for my home and then type the password), but I entered the "network connetion" option, then "wireless" and then i had no clue. 

I read on some forums that it was important to insert the commands sudo iwconfig and sudo lspci, so i did it and the output is below, in that order:

```

lo        no wireless extensions.

eth0      no wireless extensions

```

```

00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
04:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
04:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)

```

I would appreciate some help, because I really want to learn Linux. I have some other issues i found with my keyboard while i was trying the distro, but I will request your help from my lubuntu connection!

Thanks!!!

---

### Post by collisionystm on 2011-11-15
open a terminal

type 

wicd

this should bring up the wireless manager ( i think )

Also try

ifconfig eth1 up
ifconfig wlan0 up

ifconfig -a

do you see a new interface?

---

### Post by linux_beg on 2011-11-15
Man i did all that, but it says nothing new. I tried to install wicd but it failed. I dont know what to do know !

---

### Post by deltacomp on 2011-11-15
Hello, I found this [thread]("http://ubuntuforums.org/showthread.php?p=7207288") and unfortunately there was no fix. 

I would suggest this;

Open this [link]("http://pastebin.com/raw.php?i=RHSv9w8y") and save the file as "wifix" (no quotes) in your home directory or any other folder. 
Open a terminal and cd to that directory,  then type "sudo bash wifix"

The script will attempt to download and install several different drivers. I hope it works, it had worked for me in the past.

---

### Post by linux_beg on 2011-11-15
Dude what a shame, i cant do anything. i cant install programs for help because it requires internet connection, i have to access forum from an ipod to get help... I think this OS should come at least with a built in documentation Inside the system so we, beginners, dont have to be rebooting the pc each minute to see id someone has answered. Im starting to understand why those crappy windows pcs leas rthe market!!!

---

### Post by deltacomp on 2011-11-15
If that doesn't work, it may not, go to this [page]("http://www.viaarena.com/Drivers.aspx?PageID=&OSID=66&CatID=3890"), and find the proper drivers you need. From what I have seen from the LSPCI output you may need 6102 which isn't listed. I would suggest trying a similar one such as 6103. 

If you need help installing the driver let me know.

---

### Post by deltacomp on 2011-11-15
I understand your frustration. To start linux is free, and no one is making a profit selling it to you... Windows dominates most of the market, manufacturers develop products that work with windows to turn a profit. While I do applaud Microsoft and Apple for their genius, I feel that it is not right that people are getting rich through some incredible marketing scheme while there are free solutions out there as well which are not being marketed (cause there is no money to market it).  

Back to the problem at hand. If you have the ability to boot into a working version of windows please download the linux drivers appropriate for your computer and save it to a flash drive or some other form of storage media. Then when you have the linux system up and running please begin the driver installation process. If you need help, there is readme text that should accompany the driver (in the same folder). If you need more help, let me know. 

Also if you need a faster way to check for response, I believe you can go to settings and receive email notifications that someone has responded to your post.

---

### Post by linux_beg on 2011-11-15
I have just downloaded the VT6102. I will reboot the system to install the driver. I read the txt file and the install process it's pure console, so i'll be some time doing that. If i manage to do it in a reasonable time i'll be here again.

---

### Post by deltacomp on 2011-11-15
Ok great, hopefully you can view this on your ipod. it should only be a matter of opening the console and changing the directory to where you saved the driver.  cd "where ever the driver is" then follow the commands given in the text file. Good Luck :)

---

### Post by linux_beg on 2011-11-15
Hello again man. I follow the steps and all went smoothly until i had to compile the source code. I entered the commands and it told me that some route was unvalid and that i had to install the headers for the kernell. I typed the command it told me and then it said that i had to explicitly say which package i wanted to install from a list. I wanted to show you all the messages but i saved the file in a different format and lost it. I can only remember two of the list, and it was something like "linux virtual" and "linux generic". I cant remember anything else and don't know what to do now. Do you have any idea?

---

### Post by deltacomp on 2011-11-16
Hello, ok, well that’s interesting. Unfortunately I am not sure what the message means, I need to see the message in order to to move on. If you can go back in and try it again, this time save the message in a .txt file, save it to a USB and post it back here that would be extremely helpful. 

In the meantime I will search google and attempt to find a similar situation with a solution. Have you tried the script in my earlier post?

---

### Post by linux_beg on 2011-11-16
Okay, look, heres the log:

```

ubuntu@ubuntu:~$ cd temp
ubuntu@ubuntu:~/temp$ tar xvf linuxfet.tar
Makefile
linux.txt
linuxfet.c
linuxfet.h
ubuntu@ubuntu:~/temp$ make install
The program 'make' is currently not installed.  You can install it by typing:
sudo apt-get install make
ubuntu@ubuntu:~/temp$ sudo apt-get install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  make-doc
The following NEW packages will be installed:
  make
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/116 kB of archives.
After this operation, 319 kB of additional disk space will be used.
Selecting previously deselected package make.
(Reading database ... 120902 files and directories currently installed.)
Unpacking make (from .../make_3.81-8.1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up make (3.81-8.1ubuntu1) ...
ubuntu@ubuntu:~/temp$ make install
***  Clean up older object files  ***
rm -f core *.o *~

*****  Sorry, the kernel header files path /usr/src/linux/include doesn't exist.
*****  We can't compile this driver successfully without it.
*****  Please install kernel header files before you compile this driver.

```

I also tried the following:

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
ubuntu@ubuntu:~$ sudo apt-get install linux-headers-3.0.0-12
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-12 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And from this point i am completly lost!!!

---

### Post by linux_beg on 2011-11-16
Oh and by the way, how should I save the script? I saved it in .txt, typed "sudo bash wifix" and it returned something like "wifix is not a folder" or something like that.

---

### Post by deltacomp on 2011-11-16
> **linux_beg said:**
> Oh and by the way, how should I save the script? I saved it in .txt, typed "sudo bash wifix" and it returned something like "wifix is not a folder" or something like that.

Save the script as a .php

---

### Post by deltacomp on 2011-11-16
> **linux_beg said:**
> Okay, look, heres the log:

```

ubuntu@ubuntu:~$ cd temp
ubuntu@ubuntu:~/temp$ tar xvf linuxfet.tar
Makefile
linux.txt
linuxfet.c
linuxfet.h
ubuntu@ubuntu:~/temp$ make install
The program 'make' is currently not installed.  You can install it by typing:
sudo apt-get install make
ubuntu@ubuntu:~/temp$ sudo apt-get install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  make-doc
The following NEW packages will be installed:
  make
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/116 kB of archives.
After this operation, 319 kB of additional disk space will be used.
Selecting previously deselected package make.
(Reading database ... 120902 files and directories currently installed.)
Unpacking make (from .../make_3.81-8.1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up make (3.81-8.1ubuntu1) ...
ubuntu@ubuntu:~/temp$ make install
***  Clean up older object files  ***
rm -f core *.o *~

*****  Sorry, the kernel header files path /usr/src/linux/include doesn't exist.
*****  We can't compile this driver successfully without it.
*****  Please install kernel header files before you compile this driver.

```I also tried the following:

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
ubuntu@ubuntu:~$ sudo apt-get install linux-headers-3.0.0-12
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-12 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```And from this point i am completly lost!!!

Ok, lets try this. From the start, I think you need to configure the file, then make, then sudo make install

for example;
CD into temp or where ever your file is. 
Then CD into the drivers folder. 
Now
./configure
make
sudo make install

If that doesn't work, then I am also lost. Let me know how it works.

---

### Post by linux_beg on 2011-11-16
Nothing man.

```

ubuntu@ubuntu:~/temp$ dir
linux2.txt  linuxfet.c	linuxfet.h  linuxfet.tar  linux.txt  Makefile
ubuntu@ubuntu:~/temp$ ./configure
bash: ./configure: No such file or directory
ubuntu@ubuntu:~/temp$ /configure
bash: /configure: No such file or directory
ubuntu@ubuntu:~/temp$ configure
configure: command not found
ubuntu@ubuntu:~/temp$ config_data_
No command 'config_data_' found, did you mean:
 Command 'config_data' from package 'perl' (main)
 Command 'config_data' from package 'libmodule-build-perl' (main)
config_data_: command not found

```

---

### Post by deltacomp on 2011-11-16
Ok, let me be more specific.

If the drivers folder is in the temp folder. CD to temp folder, then cd into the drivers folder. 

cd /tmp/folderwithdrivers

I am pretty sure there has to be another folder which has all the driver files in it. If you are not sure, find the drivers folder and right click on it, rename it, copy the name (include everything) then paste it into the terminal. 

You have to make sure you are in the drivers folder (not the folder the drivers folder is in) before you run the commands. 

Once you are in the proper folder which contains the make files, type 

./configure
make
sudo make install

---

### Post by linux_beg on 2011-11-16
But what drivers, the system drivers, located on a route like /usr/src/linux-generic 3.xxxx, or the drivers I have just downloaded for my specific problem?

---

### Post by deltacomp on 2011-11-16
> **linux_beg said:**
> But what drivers, the system drivers, located on a route like /usr/src/linux-generic 3.xxxx, or the drivers I have just downloaded for my specific problem?

The drivers you downloaded and saved to the USB drive or other storage device.

---

### Post by deltacomp on 2011-11-16
> **deltacomp said:**
> If that doesn't work, it may not, go to this [page]("http://www.viaarena.com/Drivers.aspx?PageID=&OSID=66&CatID=3890"), and find the proper drivers you need. From what I have seen from the LSPCI output you may need 6102 which isn't listed. I would suggest trying a similar one such as 6103. 

If you need help installing the driver let me know.

Follow the link "page"  and save the drivers you need, then transfer them to your ubuntu home folder. Then cd into the driver folder, type;
./configure
make
sudo make install

:P

---

### Post by linux_beg on 2011-11-16
Man but the drivers were inside temp. I mean, the source code for the drivers are in a .tar. I un-tar them and then they are in temp. There is no other folder. I think you might want to take a look to the instruction that come with the drivers, because I have just found something I hadn't seen:

```

Make sure the link file /usr/src/linux (or /usr/src/linux-2.4) is linked
to correctly kernel sources directory (eg: if you run 'uname -r', it appears "2.4.2-2", then the link file must be linked to /usr/src/linux-2.4.2 directory, or you will fail in compiling), and make sure there are kernel header files in /usr/src/linux/include directory (or /usr/src/linux-2.4/include), we need kernel header files in compling.

```

In fact, that link file is incorrect. There is no folder named just 'linux' inside 'src'. There are two folders called "linux-generic 3.xxxx" and the other has a similar name. Should I change the name of the link? and, how?

Just one more thing, here ([http://uploading.com/files/7439b83a/linux.txt/](http://uploading.com/files/7439b83a/linux.txt/) and [http://uploading.com/files/cm1f993d/linuxfet.tar/](http://uploading.com/files/cm1f993d/linuxfet.tar/)) I uploaded the drivers and the instructions. If you could take a look it may help. I know i'm abusing of your time but youre the only person that is helping me.

---

### Post by deltacomp on 2011-11-16
I see, I just left my place and my comp. I'll have to get back to you in a bit. Please don't worry about my time, I'm just happy to help. 

Do not rename the kernel files! That will most likely cause more problems than fix. One thing I would like you to try is go to the tar file, right click on it and open it with archive manager. Untar the file in your home directory. Then see if there is a folder with the driver in it. If not follow the readme file. I'll get back to you soon.

---

### Post by linux_beg on 2011-11-16
Nope, there isn't any other folder. I followed the instructions once again and I get stuck in the same point, when i try to compile the source code. It says that the path is unvalid "/usr/src/linux/include" and it needsthe headers. The path is indeed unvalid (no such 'linux'folder exists). But there is a folder within 'src' called 'linux-generic 3.xxxx' and inside that folder there is one called 'Include' which does contain the headers. For what i can understand, problem would be solved if we could change the path from "/usr/src/linux/include" to "/usr/src/linux-generic 3.xxxx/include", but I don't know how to do it :(

---

### Post by deltacomp on 2011-11-16
> **linux_beg said:**
> Man but the drivers were inside temp. I mean, the source code for the drivers are in a .tar. I un-tar them and then they are in temp. There is no other folder. I think you might want to take a look to the instruction that come with the drivers, because I have just found something I hadn't seen:

```

Make sure the link file /usr/src/linux (or /usr/src/linux-2.4) is linked
to correctly kernel sources directory (eg: if you run 'uname -r', it appears "2.4.2-2", then the link file must be linked to /usr/src/linux-2.4.2 directory, or you will fail in compiling), and make sure there are kernel header files in /usr/src/linux/include directory (or /usr/src/linux-2.4/include), we need kernel header files in compling.

```In fact, that link file is incorrect. There is no folder named just 'linux' inside 'src'. There are two folders called "linux-generic 3.xxxx" and the other has a similar name. Should I change the name of the link? and, how?

Just one more thing, here ([http://uploading.com/files/7439b83a/linux.txt/](http://uploading.com/files/7439b83a/linux.txt/) and [http://uploading.com/files/cm1f993d/linuxfet.tar/](http://uploading.com/files/cm1f993d/linuxfet.tar/)) I uploaded the drivers and the instructions. If you could take a look it may help. I know i'm abusing of your time but youre the only person that is helping me.

Ok, I am back, I think you are on to something, and I apologize, I have been leading you down the wrong path. I have since downloaded the files and unzipped and will attempt to reconfigure the files so that they point in the correct direction.

---

