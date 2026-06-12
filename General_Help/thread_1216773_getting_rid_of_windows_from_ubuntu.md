---
title: "getting rid of windows from ubuntu"
date: 2009-07-18
forum: General Help
---

### Post by zebuben on 2009-07-18
:confused:so, i installed ubuntu using windows xp, and now that i am in ubuntu i need to know how to make ubuntu my only os. ialready have all the files i want to keep backed up on an external hard drive. please and thankyou! it is currwntley runnung whee when i restart my computer i can chose between windows or linux, but i want windows completley gone

---

### Post by Tman5293 on 2009-07-18
Use gparted to delete the windows partiton.

---

### Post by zebuben on 2009-07-18
i am way new to computers, could i get a step by step? i admit to being a noob. but whateve

---

### Post by naklinaam on 2009-07-18
If you already have everything backed up, I would simply reinstall.

Deleting the windows partition is one option, but it will probable not remove the "dual boot menu" asking you to select which os to boot into etc.

If you do not want to reinstall (though I think that is the cleanest option) just delete the windows partition as already suggested and then search this forum for ways to remove edit the boot menu.

One advantage I see with fresh install is you probably have a better idea of how you want to partition yor disks etc.
I for example reinstalled ubuntu recently for a couple of reasons but used the opportunity to move my home folde rto a separate partion altogether. So now I am able to boot into2 different versions of ubuntu from the menu but still share the same home folder. 

Also if you were to upgrade later to reinstall later because you just crashed something and the only way to recover was a reinstall, you home folder would still be intact.

---

### Post by naklinaam on 2009-07-18
> **zebuben said:**
> i am way new to computers, could i get a step by step? i admit to being a noob. but whateve


to use gparted to delete a partition:
if you are comfortable with terminal use the following code```
sudo apt-get install gparted
```
Alternatively, navigate to 
Applications > Add/Remove... and search for gparted.
Click on the checkbox against Gnome partition editor and click apply.

To use the partition editor:
navigate to
System > Administration > Partiion editor.

one guide I found on the net on gparted is at [http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/]("http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/"). I have not used this guide or even read through it thoroughly but it seems to be detailed with screen shots etc.
Read through it and ask questions on the forum if you haveany before deleting your partition.

**Changes to the partitions are usually not "undoable"**

---

### Post by ajgreeny on 2009-07-18
> **zebuben said:**
> :confused:so, i installed ubuntu using windows xp, and now that i am in ubuntu i need to know how to make ubuntu my only os. ialready have all the files i want to keep backed up on an external hard drive. please and thankyou! it is currwntley runnung whee when i restart my computer i can chose between windows or linux, but i want windows completley gone
Did you use the wubi install, or did you make separate partitions for ubuntu?  If you put the disk in when running windows and went from there, you will have ubuntu running within your windows partition, so if you get rid of the windows partition, you will also lose ubuntu.

I think you shoud probably make sure your backups are fully up to date then boot to the ubuntu Live CD, double click on the install icon, and when you get to stage 4, partitioning, choose to use the whole disk.  If you have more than one disk, make sure you get the correct one.  Answer the questions in the next stages and then in about 20 minutes you can reboot into your new fresh ubuntu.

Welcome to the community!

---

### Post by zebuben on 2009-07-18
alright i have gp open, but how do i know which drive to partition?

---

### Post by naklinaam on 2009-07-18
> **zebuben said:**
> alright i have gp open, but how do i know which drive to partition?

Windows should normally be on your C Drive.

Just look for the drive with the lowest name alphabetically (sda or hda or something like that, while D Drive should be sdb)

The next question woul be which partition to delete? (sda1 or sda2 ...etc)
Again,
Windows would normally by NTFS while linux should be ext3 or something like that.

An additional data point I would look at to be doubly sure is the partition size.

So if you know how big your Windows partition is and if it kind of matchs the "NTFS" partition, you can safely assume that is the partition you need to work with.

---

### Post by zebuben on 2009-07-18
uhm good point, i downloaded it form the web and it is currentley running off my windows desktop, i think...   so how do i do this if it is not a cd? i am using a an eee pc  without cd drive.

---

### Post by zebuben on 2009-07-18
alright, this is getting complicated... i know nothing about computers.... pinball anyone? lol so, instead of partitioning... can i reinstall ubuntu from ubuntu when having dual os's? or would i have to dowload that huge file again?or can i use an external drive to reload? i have acopy of ubuntu on my external, but it wont seem to open..... BAHH!

---

### Post by ajgreeny on 2009-07-18
> **zebuben said:**
> uhm good point, i downloaded it form the web and it is currentley running off my windows desktop, i think...   so how do i do this if it is not a cd? i am using a an eee pc  without cd drive.
Now you have completely baffled me.
I'm afraid I don't really know what you mean by the comment that you are "running this off my windows desktop".  Can you explain exactly what you have done so far.

---

### Post by zebuben on 2009-07-18
:?

---

### Post by zebuben on 2009-07-18
i downloaded ubuntu from the web, using windows xp. and installed it, and now i am stuck on how to completley switch over to ubuntu. i saved the ubuntu file to my windows desktop, but when i booted i went to ubuntu, and here i am?

---

### Post by zebuben on 2009-07-18
ps, what are these beans and coffe things? kinda like respect?

---

### Post by hibliss on 2009-07-18
Ok, if it is running from Windows, I assume you mean you installed with Wubi installer and there is an option to uninstall Ubuntu from the add/remove programs in Windows.

If this is the case, you cannot remove Windows without killing Ubuntu, because it does not have its own partition.

There is a way to move a Wubi install to its own partition, but my advice is to do a standard install, especially if you are getting rid of Windows.

On the Eee, there are 3 partitions by default. An OS partition for Windows, a Quick Boot Partition, and a factory retore partition for Windows to recover it.

My advice is to get the Ubuntu ISO and use the USB startup disc creator (because the Eee has no optical drive). This is available in System>Administration>USB Startup disc creator (from within Ubuntu).

This will create a bootable USB drive. Now you need to get in to your bios to disable quick boot, which can be done by rapidly pressing F2 after you power the computer on.

In the Bios, disable quick boot and save the changes, then when the machine restarts keep hitting esc ket until it asks what you want to boot from (the USB drive with Ubuntu needs to be plugged in of course).

Boot from that USB that you created with the Ubuntu LiveCD, and install on the entire partition with the recommended install.

---

### Post by zebuben on 2009-07-18
ok, so i ended up having to stop, becuas ea virus completley messed up my web connection, now i am back to sqaure one, i am saving the ubuntu program to my external hard drive, (back on windows xp, i uninstalled ubuntu) so how do i make it a bootable file?

---

### Post by cooper77z on 2009-07-18
I used to have a Windows XP system untill it took a big dump. So I actually had to reformat my entire hardrive with fedora. Then I started trying the different distros of ubuntu. I finally settled on 8.04.2 Server with gnome. Do you have a broadband connection and the ability to burn iso images onto a DVD?

If you don't you can just goe to the bookstore and buy Linux for dummies because it comes with a cd including multiple linux distros.

---

### Post by hibliss on 2009-07-18
> **zebuben said:**
> ok, so i ended up having to stop, becuas ea virus completley messed up my web connection, now i am back to sqaure one, i am saving the ubuntu program to my external hard drive, (back on windows xp, i uninstalled ubuntu) so how do i make it a bootable file?

Do you have the Ubuntu LiveCD ISO from the main page?

If so follow my instructions above for creating a Bootable USB LiveCD.

If you are in XP, you can use **[Unetbootin]("http://unetbootin.sourceforge.net/")** to create the LiveUSB to boot from, then follow my instructions above for getting in to your bios and changing the boot settings.

---

### Post by cooper77z on 2009-07-18
Are you suggesting that Windows impedes a Linux install, or is it just operator error?

---

### Post by hibliss on 2009-07-18
> **cooper77z said:**
> I used to have a Windows XP system untill it took a big dump. So I actually had to reformat my entire hardrive with fedora. Then I started trying the different distros of ubuntu. I finally settled on 8.04.2 Server with gnome. Do you have a broadband connection and the ability to burn iso images onto a DVD?

If you don't you can just goe to the bookstore and buy Linux for dummies because it comes with a cd including multiple linux distros.

Read the thread, he is using a Netbook with no optical drive.

---

### Post by cooper77z on 2009-07-18
I did read the thread. I got lost with the cli stuff and I figured other people would get confused too. Seriously, the more erroneous stuff I type into the terminal, the more out of wack my system gets. He said that he backed up his files so I don't really know what you mean.

---

### Post by hibliss on 2009-07-18
You suggested he burn the image to a DVD, he has no DVD drive (optical drive).

---

### Post by cooper77z on 2009-07-18
Oh, sorry. I didn't understand what I was reading. With no optical drive then I would suggest either buying a dvd/cd player or an SD card with an image.

---

### Post by hibliss on 2009-07-18
I made the suggestion to boot from USB (which is how I installed on my Eee).

---

### Post by cooper77z on 2009-07-19
Cool, when you installed via usb were you able to instruct intel to boot from the usb device?

---

### Post by hibliss on 2009-07-19
USB or SD will generally work on new machines, as long as there is an option in the BIOS to boot from removable storage it will work.

---

