---
title: "Trying to recover grub with live cd"
date: 2010-03-01
forum: General Help
---

### Post by Chirola on 2010-03-01
Hello

I have already posted this in a old thread, but a member told me it was better to start a new thread with my problem. 

So here is my problem:

I'm trying to restore the grub using a ubuntu 9.10 live cd.
I have two partitions in my computer, and i used the partition that contained Vista to install windows 7. 
Now, i'm trying to restore the grub so that i can also boot ubuntu.

When i do "sudo fdisk -l", the output is:

[B]Disk /dev/sda: 120.0 GB, 120034123776 bytes
138 heads, 12 sectors/track, 141571 cylinders
Units = cylinders of 1656 * 512 = 847872 bytes
Disk identifier: 0x0fb3cfe1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6185       91128    70332416    7  HPFS/NTFS
/dev/sda2           91133      141568    41760967+   f  W95 Ext'd (LBA)
/dev/sda5          132411      141568     7582648+  82  Linux swap / Solaris

[/B]I'm pretty sure that the filesystem created when i've installed ubuntu was extended 3.
I don't recognize "W95 Ext'd (LBA)". Is this a other type of filesystem?

It is possible that i have accidently killed the ubuntu partition when i had windows installed?

I've already tried to use super grub disk, but when i'm in "grub>" and i do: "find /boot/grub/stage1" the output: "Error 15:File not found"

Right now, i'm using the live cd, and when i do "sudo grub", 
i get "sudo: grub: command not found"

I tried to do: "sudo apt-get install grub" 
but i get this
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

I write in the console: "sudo dpkg --configure -a" then " sudo apt-get install grub"
and the output is:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/407kB of archives.
After this operation, 807kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `wireless-crda': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


[/B]Please...help is needed!!

---

### Post by darolu on 2010-03-01
Ubuntu 9.10 uses GRUB 2 now, if your original Ubuntu install was a fresh Karmic one, it has GRUB 2, and to restore it you will need to do what [THIS LINK]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2") say.

But, I see a bigger problem with your fdisk; it has your windows partition, a windows extended partition (the W95 Ext'd (LBA) one) and your SWAP partition only; no Linux partition (where Ubuntu should be).

---

### Post by henners91 on 2010-03-01
Did you install ubuntu inside of windows using Wubi? that could explain the extended partition. If not then i'd have to suddest a fresh ubuntu install of the live CD, next time create a seperate /home partition for files so you don't lose them if this happens again in the future

---

### Post by darolu on 2010-03-01
I haven't used Wubi; does it creates a real Swap partition? It is really weird because the Windows extended partition starts at 91133 (where first partition ends), then the Swap partition which is contained inside the extended one starts at 132411, leaving an empty space between 91133 and 132411 where I suppose the Ubuntu partition is/was; which is the part that confuses me the most, doesn't Wubi simply create a Virtual Machine to run Ubuntu?.

---

### Post by Chirola on 2010-03-01
> **darolu said:**
> Ubuntu 9.10 uses GRUB 2 now, if your original Ubuntu install was a fresh Karmic one, it has GRUB 2, and to restore it you will need to do what [THIS LINK]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") say.

But, I see a bigger problem with your fdisk; it has your windows partition, a windows extended partition (the W95 Ext'd (LBA) one) and your SWAP partition only; no Linux partition (where Ubuntu should be).


My original ubuntu install is 7.10. 

Is it possible that my windows installation had "destrooyed" my extended 3 partition and created the W95 Ext'd (LBA) partition?

---

### Post by Chirola on 2010-03-01
> **henners91 said:**
> Did you install ubuntu inside of windows using Wubi? that could explain the extended partition. If not then i'd have to suddest a fresh ubuntu install of the live CD, next time create a seperate /home partition for files so you don't lose them if this happens again in the future

No, i've installed windows 7, in the Vista partition with the ubuntu already installed.

70GB for windows, and 50 GB for ubuntu.

---

### Post by meierfra. on 2010-03-01
> Is it possible that my windows installation had "destrooyed" my extended 3 partition and created the W95 Ext'd (LBA) partition? 

It looks like Windows messed up your partition table, but I would guess that the  Ubuntu partition itself is  unharmed.  So you should be able to use "testdisk" to recover the correct partition table.

Boot from the Ubuntu  Live CD.
Enable  the universe  repository in  "System->Administration->Software Source"

Open a terminal and type

```

sudo apt-get update
sudo apt-get install testdisk
sudo testdisk /dev/sda

```


At the first screen press "Enter" to "Proceed"
At the next screen choose "Intel"
"Analyze",
"Quick search",
Press "Y" or "N" (depending whether you have any partition created by Vista)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let us  know exactly which partitions give you a directory listing.

Hopefully testdisk will find your Ubuntu partition and we will be able to tell you how to recover that partition.

---

### Post by Chirola on 2010-03-01
> **meierfra. said:**
> It looks like Windows messed up your partition table, but I would guess that the  Ubuntu partition itself is  unharmed.  So you should be able to use "testdisk" to recover the correct partition table.

Boot from the Ubuntu  Live CD.
**Enable  the universe  repository in  "System->Administration->Software Source"**



Sorry, i'm really a linux newbie.
Universe repository is the option "Community-maintained Open Source software(universe)" ?

I've selected that option,and then, in the console i wrote what you said: sudo apt-get install testdisk

[B]the output is: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
[/B]
I suppose i did't enable the correct package so that testdisk could be installed.

I sent an image with the window that opens when i do : [B]"System->Administration->Software Source"
[/B]I've selected the option "Community-maintained Open Source software(universe)".

---

### Post by meierfra. on 2010-03-01
```
Community-maintained Open Source software(universe)" ?
```
That's correct. But I forgot to tell you  to run


```
sudo apt-get update
```
to load the new packages.

---

### Post by Chirola on 2010-03-01
> **meierfra. said:**
> It looks like Windows messed up your partition table, but I would guess that the  Ubuntu partition itself is  unharmed.  So you should be able to use "testdisk" to recover the correct partition table.

Boot from the Ubuntu  Live CD.
Enable  the universe  repository in  "System->Administration->Software Source"

Open a terminal and type

```

sudo apt-get update
sudo apt-get install testdisk
sudo testdisk /dev/sda

```At the first screen press "Enter" to "Proceed"
At the next screen choose "Intel"
"Analyze",
**"Quick search",**
Press "Y" or "N" (depending whether you have any partition created by Vista)


First of all i would like to thank you for your help.

Okay. 

When i got to QuickSearch and pressed enter, the follow menu appeared.
(sent an image with the menu).

NTFS, Linux ,Linux(Swap)

In the next step i select the Linux partition?
(is that really the linux partition or the W95 Extd LBA) 

What exactly this testdisk program does?

---

### Post by meierfra. on 2010-03-01
> When i got to QuickSearch and pressed enter, the follow menu appeared.
(sent an image with the menu).

You need to press "enter" one more time to get to the next screen, where you will be able to do the deep search.

> What exactly this testdisk program does? 

The deep search just looks for lost partitions (and does not change anything)

If the deeps search finds the Ubuntu partition, you  can use testdisk to rewrite the partition table. But we will worry about that later.

---

### Post by meierfra. on 2010-03-01
Hang on.

---

### Post by meierfra. on 2010-03-01
Since the Quick search already found the Ubuntu partition, you don't have to do the deep search.  
Just to double check that the Linux partition really is the Ubuntu partition, select the linux  partition. Then press "p".  Post a screen shot. (it should list the  files in the Ubuntu "/"  directory.)

---

### Post by Chirola on 2010-03-01
> **meierfra. said:**
> Since the Quick search already found the Ubuntu partition, you don't have to do the deep search.  
Just to double check that the Linux partition really is the Ubuntu partition, select the linux  partition. Then press "p".  Post a screen shot. (it should list the  files in the Ubuntu "/"  directory.)


This looks bad.

Looks like the ubuntu partition is no more. Is there anything else that could be done?

---

### Post by meierfra. on 2010-03-01
> Is there anything else that could be done? 
Yes. Let's do the deep search.

 Press "esc" to get back to the screen with the quick search results.  Then press "enter"  to continue and then choose "Deep search"

---

### Post by Chirola on 2010-03-01
> **meierfra. said:**
> Yes. Let's do the deep search.

 Press "esc" to get back to the screen with the quick search results.  Then press "enter"  to continue and then choose "Deep search"

I'm doing the deep search right now, it is only at 8%. 
Looks like it will take a will before it's done.
I will keep you posted.

Thanks again for the help;)

---

### Post by Chirola on 2010-03-01
The Deep Search has been concluded.

The output is at the image.

---

### Post by meierfra. on 2010-03-01
Select each of the LINUX partitions and  press "P".  Let us know which one  gives you a directory listing. (press "esc" to get back  to the deep search results).

---

### Post by Chirola on 2010-03-02
Hello once again,

Unfortunatly, last time i had to leave so, i could not finish the Deep search.
So i've got to do all steps once again.
I've boot from live cd, but now , when i do "sudo apt-get update", i get this output
(sent an image). 
It tooks like the packages were not installed, because when i do 

"sudo apt-get install testdisk" i get this output:
[B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  testdisk
0 upgraded, 1 newly installed, 0 to remove and 243 not upgraded.
Need to get 0B/1,547kB of archives.
After this operation, 4,784kB of additional disk space will be used.
Selecting previously deselected package testdisk.
(Reading database ... 45%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `xfonts-base': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/B]
Last time this did not happen.

---

### Post by meierfra. on 2010-03-02
No clue whats going on. Maybe   the download went wrong. I suggest to reboot into the LiveCD and then try again. 


If you still run  into problems:  Download the tar.bz2 file of the newest version from [testdisk ]("http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2")to your Desktop  (on the LiveCD) and install and run it via 

```
cd ~/Desktop
tar -xvf testdisk-*linux*.tar.bz2 
sudo testdisk-*/linux/testdisk_static

```

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> No clue whats going on. Maybe the download went wrong. I suggest to reboot into the LiveCD and then try again. 


If you still run  into problems:  Download the tar.bz2 file of the newest version from [testdisk ]("http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2")to your Desktop  (on the LiveCD) and install and run it via 

```
cd ~/Desktop
tar -xvf testdisk-*linux*.tar.bz2 
sudo testdisk-*/linux/testdisk_static

```

I tried to reboot to live cd and once again, i could not install the packages with 
"sudo apt-get update". Very strange.

I did what you said. i downloaded the testdisk, and unpack it into desktop.

I have concluded the deep search, and i was able to list the files in the linux partition.
I sent you two images, one of then, with the files listed in the linux partition, and a log file generated by testdisk(don't no if will be usefull).

I do i do next?

---

### Post by meierfra. on 2010-03-03
That looks good.

At the screen with the deep search results,  select each of the partitions. Then use the left and right arrow keys to change the symbol in the first column so that it looks like:


```
[COLOR="Red"]P [/COLOR] Fat32
[COLOR="Red"]* [/COLOR] HPFS-NTFS
D  HPFS-NTFS
D  Linux
[COLOR="Red"]L[/COLOR]  Linux
D  Linux
D  LINUX
[COLOR="Red"]L [/COLOR] Linux Swap
D  Linux Swap
```


(So  the Linux partition which gave you the directory listing needs to be marked with an "L")

Then press "enter" to continue. At the new screen choose "write" and confirm the changes when asked.

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> That looks good.

At the screen with the deep search results,  select each of the partitions. Then use the left and right arrow keys to change the symbol in the first column so that it looks like:


```

[COLOR=Red]P [/COLOR] Fat32
[COLOR=Red]* [/COLOR] HPFS-NTFS
D  HPFS-NTFS
D  Linux
[COLOR=Red]L[/COLOR]  Linux
D  Linux
D  LINUX
[COLOR=Red]L [/COLOR] Linux Swap
D  Linux Swap
```
(So  the Linux partition which gave you the directory listing needs to be marked with an "L")

Then press "enter" to continue. At the new screen choose "write" and confirm the changes when asked.

Reboot and see whether you can boot into Ubuntu.

Well i think it is almost done.

I did what you said, and i reboot.
I still can't see the dual boot option because of the "Cannot locate c:\recovery.dat"

This is a classic error.
That is because i still have the recovery partion in the hardrive right ?

Deleting the recovery partion should resolve the problem. What do you think?

Should i delete it, or there is another way to resolve this?

---

### Post by meierfra. on 2010-03-03
Edit: Haven't read you last post yet. Did you already reinstall Grub?

Once you fixed the partition table, you have to reinstall Grub. Reboot into the LiveCD, so that the changes in the partition table become effective.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by meierfra. on 2010-03-03
> I still can't see the dual boot option because of the "Cannot locate c:\recovery.dat"
When does this error occur? What exactly happens during boot up?

To get a better picture of your setup, boot from the LiveCD and then follow these i[nstructions]("http://bootinfoscript.sourceforge.net/") to run the Boot Info Script and post the RESULTS.txt.

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> Edit: Did you already reinstall Grub?

Once you fixed the partition table, you have to reinstall Grub. Reboot into the LiveCD, so that the changes in the partition table become effective.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

No, i did not reinstall Grub.

When i fixed the partition table, i took the live cd out of the drive, and rebooted the system hoping to see grub menu with the dual boot option.

Do i have to do all those steps again with testdisk? Or the changes made by the testdisk are still available after the reboot?

---

### Post by meierfra. on 2010-03-03
> Do i have to do all those steps again with testdisk? Or the changes made by the testdisk are still available after the reboot? 

Those changes were permanent. So you won't have to do them again


I noticed that the recovery partition was not on the original partition table. Had you deleted that recovery partition at some stage? But the recovery partition should not cause any problems.

Anyway, try reinstalling Grub and if that does not help, post the RESULTS.txt (as instructed in my last post).

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> Those changes were permanent. So you won't have to do them again


I noticed that the recovery partition was not on the original partition table. Had you deleted that recovery partition at some stage? But the recovery partition should not cause any problems.

Anyway, try reinstalling Grub and if that does not help, post the RESULTS.txt (as instructed in my last post).

I can't reinstall grub. Have the same problem that i had when i tried to install testdisk.
Can't download the packages with "sudo apt-get upgrade".

Can you give me a link to download, has you did with testdisk ?

One more thing,i sent you an image with the "sudo fdisk -l" output:

It appears that Linux partition is already alive.

But that two lines that say "Partition 1 does not end on cylinder boundary." and
"Partition 2 does not end on cylinder boundary." do not sound very good.
Any problem with that?

---

### Post by meierfra. on 2010-03-03
> But that two lines that say "Partition 1 does not end on cylinder boundary." and
"Partition 2 does not end on cylinder boundary." do not sound very good.


Those are harmless warnings. The partition table seems fine.

> I can't reinstall grub. 
 You are probably using Grub 2 and don't need to have Grub installed. So just try the instructions from post #24.

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> Those are harmless warnings. The partition table seems fine.


 You are probably using Grub 2 and don't need to have Grub installed. So just try the instructions from post #24.

Okay. Already done. The output is:
[B]
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found[/B]

What is the next step?

---

### Post by meierfra. on 2010-03-03
Reboot and see whether you get the Grub menu and can boot into Ubuntu. Once you are in Ubuntu run

```
sudo update-grub
```

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> Those are harmless warnings. The partition table seems fine.


 **You are probably using Grub 2 and don't need to have Grub installed. So just try the instructions from post #24**.

I' m using a ubuntu 9.10 live cd, but the ubuntu installation i have is 7.10.
Ubuntu 7.10 does not use grub2 or does?

Is there any command that i could use in the console that shows the grub version?

If that is relevant to help ofcourse.

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> Reboot and see whether you get the Grub menu and can boot into Ubuntu. Once you are in Ubuntu run

```
sudo update-grub
```


I did the reboot but unfortunatly, i did not get the grub menu.

Instead i get the prompt: "sh:grub>"

EDIT: I did not boot into live cd. I did a normal reboot, without the live cd in the drive.

---

### Post by Chirola on 2010-03-03
> **meierfra. said:**
> When does this error occur? What exactly happens during boot up?

To get a better picture of your setup, boot from the LiveCD and then follow these i[nstructions]("http://bootinfoscript.sourceforge.net/") to run the Boot Info Script and post the RESULTS.txt.

Right now, when i try to boot i go to "sh:grub>" prompt

I uploaded the RESULTS.txt .

Looks like everything is how it is suppose to be.

sda5, boot sector info, there is noting written there. Is that normal?

---

### Post by meierfra. on 2010-03-03
> sda5, boot sector info, there is noting written there. Is that normal? 
Yes, it is.

You actually had Legacy Grub installed and not Grub 2. Try this:


At the "grub>sh" prompt, type

```

set root=(hd0,5)
insmod ext2
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

```


That should boot you into Ubuntu.  In ubuntu, run

```
sudo grub
```
and at the "grub>" prompt

```
root (hd0,4)
setup (hd0)
quit
```

Reboot. You should get the grub menu.  See whether you can boot into Ubuntu and Windows.

---

### Post by Chirola on 2010-03-04
> **meierfra. said:**
> Yes, it is.

You actually had Legacy Grub installed and not Grub 2. Try this:


At the "grub>sh" prompt, type

```

set root=(hd0,5)
insmod ext2
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

```That should boot you into Ubuntu.  In ubuntu, run

```
sudo grub
```and at the "grub>" prompt

```
root (hd0,4)
setup (hd0)
quit
```Reboot. You should get the grub menu.  See whether you can boot into Ubuntu and Windows.


I read this post of yours too late :(

I've tried to recover the grub using super grub disk.
I've selected the option: "Grub =>MBR & !Linux! (1) AUTO"

The grub menu is restored, but when i try to boot into linux, it appears me the follow message: "Error 17: Cannot mount selected partition"

But the most strange thing that happened, is that it appears me Windows Vista in the boot options:confused:

I sent you an image with the output of "sudo fdisk -l"
(it seems diferent from the last one i've showed you) and a txt file with my menu.lst .

I'm currently running ubuntu live cd.

Once again,thanks for your help.

---

### Post by Chirola on 2010-03-04
Okay. My current situarion is:

I boot from live cd, and openned a console.In there a rigtht the follow commands, has you said before.

```

sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```Every time i do this, when i reboot, i get the "sh:grub>" prompt.

In this prompt i write the commands you said:

```

set root=(hd0,5)
insmod ext2
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```This gave me good news. I was able to boot my ubuntu :D .

Now, when i called the grub prompt with "sudo grub", and then:

     Code:
```

root (hd0,4)
setup (hd0)
quit 

```When i rebooted, i was able to see the grub menu, but when i tried to boot ubuntu , the same Error 17 was showed to me.
And it continued to show me "windows vista-loghorn" has a boot option.

Now, i think you were wrong about one thing. i have a recovery partition.

My sda1 is a recovery a partition, and it is mounted in my desktop and says "RECOVERY".
When i double click it, i see in the address bar, /media/sda1 .

Now, if you check my menu.lst file, you can see that when grub tries to boot windows, 
he is trying to boot at (hd0,1),that means he is accessing sda1 right?

---

### Post by meierfra. on 2010-03-04
> root		(hd0,5)
Your grub menu needs to be update.  (Sorry, I forgot to check on that)

Boot into Ubuntu. 

At the Grub menu at boot up select "ubuntu". But do not press "enter". Instead press "e".  At the new screen, press "e" again. Change

root (hd0,5)

to

root (hd0,4)

Press "enter" and then "b" to boot.

Once you are in Ubuntu:

```
gksudo gedit /boot/grub/menu.lst
``` 

Look for the line

# groot=(hd0,5)

change it to

# groot=(hd0,4)

Save and close the file and run

```
sudo update-grub
```

That should  take care  of  the Grub error 17.


> Now, i think you were wrong about one thing. i have a recovery partition.
I know. But you did not have the recovery partition in the partition table when you first posted. (that's all I was saying)

> And it continued to show me "windows vista-loghorn" has a boot option.
Are you able to boot into Vista from the Grub menu?

---

### Post by Chirola on 2010-03-04
if groot = (hd0,4) is responsible for booting linux(sda5) , then groot = (hd0,0) is supposed to 

boot windows(sda2).

Shouldn't i alter that value as well ?

EDIT: Success, i can now boot to ubuntu :D . But i still can't boot windows.

---

### Post by meierfra. on 2010-03-04
> EDIT: Success, i can now boot to ubuntu 
Great.

> But i still can't boot windows. 

The "groot" statement is only for Ubuntu (it's used to automatically generated the "root" statements for all the Ubuntu items on menu.lst

For Vista you only have to look at the  "root line":

title		Windows Vista/Longhorn (loader)
[COLOR="Red"]root		(hd0,1)[/COLOR]
savedefault
makeactive
chainloader	+1

 Grub starts counting at zero. (hd0,1) means second partition on the first hard drive. So   this is correct.

But try this:

```
title		Windows Vista/Longhorn (loader)
rootnoverify (hd0,1)
chainloader	+1
```

although I doubt it will make a difference.

If you are still not able to boot Vista, let me know exactly what happens after you choose Vista at the Grub menu.

---

### Post by Chirola on 2010-03-04
> **meierfra. said:**
> Great.



The "groot" statement is only for Ubuntu (it's used to automatically generated the "root" statements for all the Ubuntu items on menu.lst

For Vista you only have to look at the  "root line":

title        Windows Vista/Longhorn (loader)
[COLOR=Red]root        (hd0,1)[/COLOR]
savedefault
makeactive
chainloader    +1

 Grub starts counting at zero. (hd0,1) means second partition on the first hard drive. So   this is correct.

But try this:

```
title        Windows Vista/Longhorn (loader)
rootnoverify (hd0,1)
chainloader    +1
```although I doubt it will make a difference.

If you are still not able to boot Vista, let me know exactly what happens after you choose Vista at the Grub menu.


I have already tested and did not work. I have windows 7 installed, and not Vista.Does that make any diference?
The name of Vista only apears because it was already written in the menu.lst .

What happens when i try to boot windows is the message "cannot find c:\RECOVERY.DAT" .

After i've selected windows in the grub menu,appears the same old loading that is equal when i had windows vista installed.
First appears a loading bar with the text "windows is loading files",then another loading with the text "Microsoft corporation...bla bla bla", and at last , the message of "recovery.dat".


I think windows will be booted if i disable/unmount/delete the recovery partition.What do you think?

---

### Post by meierfra. on 2010-03-04
Did you ever successfully boot into Window 7?

I'm asking since I noticed that your partition table at the time of your first post was even more messed up than I had realized:

> 138 heads, 12 sectors/track, 141571 cylinders
Almost all partition tables use 255  heads and 63 sector/track.

---

### Post by Chirola on 2010-03-05
> **meierfra. said:**
> 
[B]
Did you ever successfully boot into Window 7?[/B]




Yes. When i did my first post, Windows 7 was the only thing that worked.

After the testdisk and grub installation, it stoped from booting.

> 
I'm asking since I noticed that your partition table at the time of your first post was even more messed up than I had realized:

Almost all partition tables use 255  heads and 63 sector/track.


Okay, but now thanks to you, it's fixed:D
See for your self.

Now, to boot windows, all is needed is to delete the recovery partition.

Can you give me a "sudo comand" for that?

One thing,if i delete recovery, sda2 remains windows,and sda5 remains linux?
Or all that will be changed?

---

### Post by meierfra. on 2010-03-05
You might be able to fix your problem without having to delete the recovery partition:


Boot from  your Windows 7  DVD. If you do not have one, you can download  a repair CD  from  [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

At the first screen select your favorite language.
At the second screen choose "Repair your Computer".
On the  next screen select   "Use recovery tools ..."  and click on "Next".

Choose "Command Prompt" at the next screen.
At the command prompt type:

```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
```This will list the drive letters for all  the 'NTFS' and 'Fat' partitions on your computer.  Determine the drive letter for your Win 7 partition and for  the CDrom drive.  Type

```
 exit
``` to exit the ``diskpart'' prompt.


Then type:

```
bootsect  /nt60  C:
```

but replace "C:" by the drive letter of the Win 7 partition.

If you get a unknown command message try

```
E:\boot\bootsect.exe /nt60  C:
```

where "E:"  needs to be replaced by  the drive letter of the CD drive and "C:" by the drive letter of the Win 7 partition.  Although the actually path for "bootsect.exe" might depend on the CD you are using.


**If fixing the boot sector of the Win 7 partition did not solve your problem:**

You can delete the Recovery partition from the partition table via:

```
sudo fdisk /dev/sda
```
and then press:

d
1
w

This deletes /dev/sda1. Win 7 will still be /dev/sda2 and Ubuntu  /dev/sda5.

---

### Post by Chirola on 2010-03-06
> **meierfra. said:**
> You might be able to fix your problem without having to delete the recovery partition:


Boot from  your Windows 7  DVD. If you do not have one, you can download  a repair CD  from  [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

At the first screen select your favorite language.
At the second screen choose "Repair your Computer".
On the  next screen select   "Use recovery tools ..."  and click on "Next".

Choose "Command Prompt" at the next screen.
At the command prompt type:

```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
```This will list the drive letters for all  the 'NTFS' and 'Fat' partitions on your computer.  Determine the drive letter for your Win 7 partition and for  the CDrom drive.  Type

```
 exit
``` to exit the ``diskpart'' prompt.


Then type:

```
bootsect  /nt60  C:
```but replace "C:" by the drive letter of the Win 7 partition.

If you get a unknown command message try

```
E:\boot\bootsect.exe /nt60  C:
```where "E:"  needs to be replaced by  the drive letter of the CD drive and "C:" by the drive letter of the Win 7 partition.  Although the actually path for "bootsect.exe" might depend on the CD you are using.


**If fixing the boot sector of the Win 7 partition did not solve your problem:**

You can delete the Recovery partition from the partition table via:

```
sudo fdisk /dev/sda
```and then press:

d
1
w

This deletes /dev/sda1. Win 7 will still be /dev/sda2 and Ubuntu  /dev/sda5.

Well...finally it is done!!!:D

Windows 7 and ubuntu dual boot finally alive and kicking!!

Thank you very much for your help!!

---

### Post by meierfra. on 2010-03-06
> Well...finally it is done!!

Great. Did you fix the  boot sector?  Or did you delete the recovery partition?

---

### Post by Chirola on 2010-03-06
> **meierfra. said:**
> Great. Did you fix the  boot sector?  Or did you delete the recovery partition?

I've deleted the recovery partition.

I've burn a cd with the iso you gave me but i could't boot from it.

So i just decided to delete the partition. 
If i decide to format the computer one day, the recovery partition will be back .

Once again, thanks for the help;)

---

### Post by deboh on 2010-03-25
I have just installed windows 7 and as it would do my grub is wiped out, yes i can recover with a livecd.
I only did an update from ubuntu 8.10 to 9.04 and to 9.10 i did not use a 9.10 livecd for the instal.

How is it possible for me to recover my grub for 9.10 using a 8.10 live cd i have?

thanks

---

