---
title: "Problem connecting Samsung Galaxy Tab 7.7 to Ubuntu 12.04"
date: 2012-07-21
forum: General Help
---

### Post by ridz on 2012-07-21
I am having problems in connecting the Samsung Galaxy Tab 7.7 to an Ubuntu 12.04 Linux based PC via a USB cable. Every time I connect the tablet to Ubuntu, I get a message saying "Unable to mount Android; Error initializing camera: -60: Could not lock the device" The peculiar part is that I get 2 additional windows pop up - one for the tablet itself and the other is the tablet's external SD card - but I cannot browse any files at all - in fact, I cannot carry out any file operations at all.

Searching the web, I found suggestions like making sure that 'mtpfs' and 'mtp-tools' packages are installed - they are but nothing works. The only way I can transfer files between the P6800 and Ubuntu is via Bluetooth - which is very, very slow!

BTW, I did connect up my Acer A500 tablet via USB - and it works just fine. I can transfer files back and forth without any problems. So it's just the Galaxy Tab that is giving me the problem.

Anyone here using the Galaxy Tab 7.7 with Ubuntu 12.04? Do you face the same problems? Any tips?

---

### Post by Ashwin Mane on 2012-07-21
Hi,

I was facing the same problem with my SAMSUNG Tab-2. After updating the O.S. the phone & SD card both are explorable. 

Kind rgds,
Ashwin Mane

---

### Post by alan21276 on 2012-07-21
This seems to be an android issue with it's new implementation of usb connectivity. Older devices worked fine as they mounted the phone/tablet memory on your pc when connected....however rendering the device it self unusable while connected. Now it uses a system which shares the memory while keeping the device active. Unfortunately this results in lower transfer speeds and in some cases connectivity issues.
I had similar problems with my Galaxy S3.

If you are planning on transferring large files then the best option I have found so far is using a drop box account.

Wifi file managers so far have proved too unstable for me....but also worth trying.

---

### Post by techvish81 on 2012-07-21
my galaxy tab 8.9 connects in a similar fashion, i cannot do any file operations in it.
 luckily it supports USB drive,  so i can use it when such need arises.

---

### Post by ridz on 2012-07-22
Thanks for all the replies. It seems that I'm not the only one facing the same problem.

One other thing of note: I am running Android 3.2 (Honeycomb) on the Samsung Galaxy Tab 7.7 while the Acer Iconia Tab A500 is running Android 4.0.3 (Ice Cream Sandwich). Does this make any difference in USB connection? As mentioned previously, I can connect without any problems on the Acer but not on the Samsung.

---

### Post by techvish81 on 2012-07-22
> **ridz said:**
> Thanks for all the replies. It seems that I'm not the only one facing the same problem.

One other thing of note: I am running Android 3.2 (Honeycomb) on the Samsung Galaxy Tab 7.7 while the Acer Iconia Tab A500 is running Android 4.0.3 (Ice Cream Sandwich). Does this make any difference in USB connection? As mentioned previously, I can connect without any problems on the Acer but not on the Samsung.

you are right, i had sony tablet with android 3.2 and it was not connecting as expected.

galaxy tab 730 (8.9) is also android 3.2 honeycomb. and same problem.

---

### Post by alan21276 on 2012-07-22
It does seem to vary between android versions, my galaxy s1 on froyo connects in mass storage mode with no issues, where as the galaxy s3 on ICS doesn't like to play ball.

That is where Android shows it's roots in Linux........always changing and breaking things(for the better of course):P

---

### Post by ridz on 2012-07-23
Well, looks as if using USB to manage files between my Samsung Galaxy Tab 7.7 and Ubuntu 12.04 (and Mint 13, FYI) is totally out of the question - at least until this issue is resolved.

The only way I can move files between the 2 devices at the moment is to:

a) remove SD card from Samsung, plug it into a card reader recognized by Ubuntu 12.04 and move/copy the files

b) use Bluetooth to move/copy files

c) use the Airdroid utility to move/copy files

Items (a) is too 'fussy' and takes too much time to move/copy a few files. Item (b) is too s...l...o...w. Finally item (c) takes time to connect - but once connected the move/copy process is fairly fast. So it looks as if Airdroid is the winner here. Any comments? Have I missed any other solutions?

---

### Post by alan21276 on 2012-07-24
> **ridz said:**
> Well, looks as if using USB to manage files between my Samsung Galaxy Tab 7.7 and Ubuntu 12.04 (and Mint 13, FYI) is totally out of the question - at least until this issue is resolved.

The only way I can move files between the 2 devices at the moment is to:

a) remove SD card from Samsung, plug it into a card reader recognized by Ubuntu 12.04 and move/copy the files

b) use Bluetooth to move/copy files

c) use the Airdroid utility to move/copy files

Items (a) is too 'fussy' and takes too much time to move/copy a few files. Item (b) is too s...l...o...w. Finally item (c) takes time to connect - but once connected the move/copy process is fairly fast. So it looks as if Airdroid is the winner here. Any comments? Have I missed any other solutions?

a) agreed
b) agreed
c) works not too bad with small files but I've found it tends to give connection errors when transferring larger ones i.e. large movie files

---

### Post by alan21276 on 2012-07-24
There is supposedly a way to force mass storage mode (used on older android) but it requires you to root your device first, which I'm not too keen on doing to a brand new device due to invalidating the warranty.......
I'm looking at using kies through wine but usb support isn't great.

---

### Post by Auberg on 2012-07-25
Hi I am running “FTP Server” Android app, on my Samsung Galaxy Tab 8.9 
and from my Filezilla on my ubuntu i write what the ftp-app is telling me
[ftp://192.168.X.Z:2221](ftp://192.168.X.Z:2221) and the  user/ pw that it provide

hope it helps

---

### Post by alan21276 on 2012-07-25
> **Auberg said:**
> Hi I am running “FTP Server” Android app, on my Samsung Galaxy Tab 8.9 
and from my Filezilla on my ubuntu i write what the ftp-app is telling me
[ftp://192.168.X.Z:2221](ftp://192.168.X.Z:2221) and the  user/ pw that it provide

hope it helps

What are the transfer speeds like?
How does is cope with large files?

---

### Post by Auberg on 2012-07-25
A mp4 file at 182mg  -> 4 min 20 sec 
3 gig 388 files no errors,,....

I would like to use USB,  untill then FTP !...


The 4 min is wrong sorry.   I did send again just to see and  at 2.6mg/sek it took 72 sek

---

### Post by ridz on 2012-07-25
> **Auberg said:**
> Hi I am running “FTP Server” Android app, on my Samsung Galaxy Tab 8.9 
and from my Filezilla on my ubuntu i write what the ftp-app is telling me
[ftp://192.168.X.Z:2221](ftp://192.168.X.Z:2221) and the  user/ pw that it provide

hope it helps

Thank you for this tip - file transfers are indeed faster using this method. Airdroid sometimes falter but the ftp server does not!:P

---

### Post by aa4bb on 2012-08-06
Add my thanks, Auberg. This was just what I needed to copy my music collection from Ubuntu laptop to my new Galaxy Tab 2 10.1.

---

### Post by leroim8 on 2012-11-05
i just reboot my phone connected with mu ubuntu and it,s detected

---

### Post by csevcik on 2012-11-20
There is one way to transfer data between ONE Samsung Android device and U 12.04 LTS. This is UbuntuOne, the Ubuntu cloud service, just download the free UbuntuOne app for the Samasung device (I have not been able to install it in TWO Samsung devices) and install your free (5 Gb) UbuntuOne cloud account. I did that in my Samsung Galaxy Tab 2 and can share files from the tablet to my UbuntuOne cloud. Photos and music are tranfered automatically.

Chech the rest in the UbuntuOne info.

---

### Post by foxy123 on 2012-12-08
I've got a similar problem with S3 and videos. If I use PTP camera mode I can see only photos but not videos. In MTP mode I cannot see anything in the DCIM folder. Interestingly enough I have 12.10 on my other laptop and I can see and move video files from there. I guess it's got a newer version of PTP library.

---

### Post by techvish81 on 2012-12-08
'airdroid' is a very good android app which can be used in such situations for easy big files transfers

---

### Post by raulceuta on 2013-01-12
I suggest you another way to skip (but not solve) the problem:

1º Create a virtual machine with Windows O.S. and enable the USB devices.
2º Connect the tablet and Windows will recognize it.
3º Copy the files from the tablet to the virtual machine.
4º Share a Ubuntu folder with the virtual machine and enable other users to create and remove files from it.
5º Copy the files from the virtual machine to the shared folder.

Now you have the files in your Ubuntu system.

---

### Post by timgood on 2013-01-13
Have you tried gmtp? It is a graphical android file transfer system which works well on my Samsung Galaxy Tab and my Nexus 4 phone.

```
sudo apt-get install gmtp
```

Hope this helps.

---

### Post by 3rdalbum on 2013-01-13
My father bought a Nexus 7 and ran into the same problem.

I tried the HOWTOs about setting up FUSE, udev and MTP and couldn't get it to work. Even if it did work, it was pretty inconvenient for my father to have to run terminal commands to mount the device.

I installed an FTP server on the tablet and created a Bookmark in Nautilus, and now it's a piece of cake for him to transfer files from Ubuntu to the Nexus 7.

---

### Post by Untold on 2013-01-13
For the Samsung there is an app called Kies Air.  It allows you to manage files from your web browser via wifi connection.  You can also change your transfer protocol from MTP to PTP.  It is not perfect.  Under other distros I was trying it only allowed you to view the camera folder on the device.  I just plugged in a Samsung Galaxy Express to my computer running ICS and at first it to would not mount the camera. However when I changed it to PTP everything loaded up and I was able to view the folders in nautilus and transfer a file. The only other drawback was that I could not get the phone to read in Midnight Commander or Calibre for books and better management.

---

### Post by linfidel on 2013-02-10
> **Untold said:**
> For the Samsung there is an app called Kies Air.  It allows you to manage files from your web browser via wifi connection.  You can also change your transfer protocol from MTP to PTP.  It is not perfect.  Under other distros I was trying it only allowed you to view the camera folder on the device.  I just plugged in a Samsung Galaxy Express to my computer running ICS and at first it to would not mount the camera. However when I changed it to PTP everything loaded up and I was able to view the folders in nautilus and transfer a file. The only other drawback was that I could not get the phone to read in Midnight Commander or Calibre for books and better management.
Interesting about Calibre - it's the only thing that seems to have no problem with my Galaxy Tab 2 with Jelly Bean.

go-mtpfs worked well with my 32-bit Ubuntu 12.04, but not as well with 64-bit, so far.

I've used the ftp server, and it works the best for me, mainly because it creates directories, which most of the network file managers don't seem to do.

FWIW, I believe it was Android ICS that started the MTP connection instead of USB mass storage, so it allows the phone to work while connected.  The problem was that mounting the main partition would disable use of it by the phone.  It would be nice if tablets without phone had a choice, though.

---

### Post by Robynsveil on 2013-02-25
I wasn't even using the Toshiba Thrive - when connecting to 12.04 - to transfer files, but rather as part of developing Android apps using Basic4Android, which - for the price - is a pretty decent app, particularly considering what it delivers and that it allows you to develop in a language already familiar to you. I run it in Win7/VirtualBox for the time being and am able to connect just fine, albeit with Wireless. When I form the USB connection, that message for the camera comes up and two icons appear on the desktop, which I ignore.

And use gMTP, which works a treat! :)

ETA: I do start gmtp from the terminal and did get this message - no idea if this might provide clues to anyone:
> gmtp
Device 0 (VID=0930 and PID=7100) is a Toshiba Thrive AT100/AT105.
Android device detected, assigning default bug flags

** (gMTP:2829): CRITICAL **: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
I was able to copy files and delete files on the Thrive, regardless.

---

