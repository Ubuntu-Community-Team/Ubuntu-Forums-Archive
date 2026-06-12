---
title: "Eee PC Ubuntu help"
date: 2010-06-14
forum: General Help
---

### Post by jasoncyrus on 2010-06-14
Ok, I'm totally new and was told to come here by people on my regular forum for help.


Recently my  brother upgraded my eee pc to the latest version of ubuntu desktop (i  dont know why he did desktop but the last version of desktop was working  fine on it)
 But today it went nuts on me and I now get this error after the  initial white screen to get into the bios.
 its a black screen with
 error: hd 0,1 ead error
 Grub Rescue:
 I dont know what to do, I've tried loading ubuntu netbook OS from a  memory stick but niether the ISO nor the universal usb installer.
 how can I fix this? or at the very least get it to boot from usb so i  can format the whole thing.


Es I am new to this, Yes you will have to explain things and NO I have *NO IDEA* what I am doing so please be patient.

---

### Post by mike555 on 2010-06-14
sounds like your grub bootloader is messed up ........ probably should have done a clean install ......... you should read about fixing grub ... but it is very confusing .....  I would just reinstall (a clean install) , you will loose everything on your computer in that partition , so back up your documents, pictures, etc.first , maybe with a live CD and a thumbdrive ..

you might need to borrow an external cd player ..

---

### Post by jasoncyrus on 2010-06-15
Theres nothing on it that needs backed up, so I planned to do a clean install but I cant get it to recognise my USB stick. I set the boot order as removable device first but still no luck. Tried it with just the iso file on it and then tried it using the univeral usb creator tool from the ubuntu site and that didnt work either.

Will see if I can find an old dvd drive and the usb connector cable for it. Damn eee pcs for not having a built in cd/dvd drive>.>

---

### Post by r-mo on 2010-06-15
Just copying the iso onto the usb drive won't work, you'll need to use the usb creator.  Instructions in Step 2 @ [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

When you boot the eee pc press Esc at the initial white screen then a box should pop up allowing you to boot from whatever devices are connected.

Hope this helps

---

### Post by jasoncyrus on 2010-06-15
> **r-mo said:**
> Just copying the iso onto the usb drive won't work, you'll need to use the usb creator.  Instructions in Step 2 @ [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

When you boot the eee pc press Esc at the initial white screen then a box should pop up allowing you to boot from whatever devices are connected.

Hope this helps

Ah! Fantastic, thank you very much :D now I can do a clean install ^_^

---

### Post by jasoncyrus on 2010-06-15
Ok so much for easy clean install.

When trying to install using the erase the entire drive option, it states that it cant create ext4 on the partition.

I have no idea how to fix this, can someone walk me through it?

---

### Post by jasoncyrus on 2010-06-15
i tried the "continue anyway option" but is now giving me the error

UBI migrationassisten with exit code 141. further information may be found in /var/log/syslog

Even trying to install it beside the old system isnt working, even though the installer says there isnt an OS on there.

I dont know what to do :(

---

### Post by bazzal1941 on 2010-06-15
It might be interesting to know what happens if you try ext2.

---

### Post by jasoncyrus on 2010-06-15
ok how do i do that?

I tried deleted the partitions through the disk utility tool while running the OS off the usb stick but I'm also getting stopped by 

"Error calling fsync (2) on dev/sda input/output error"

It's a solid state drive if that helps at all?

Sorry I'm really new at this an need to be walked through it coz in all honesty I dont know what I'm doing =/

---

### Post by r-mo on 2010-06-15
I hate to jump to this conclusion too quickly but are there any odd sounding clicking noises from the hard drive?  I could well be wrong but the fact you had read errors at boot before and now you can't create a partition point in the direction of a hard drive failure :(

---

### Post by jasoncyrus on 2010-06-15
> **r-mo said:**
> I hate to jump to this conclusion too quickly but are there any odd sounding clicking noises from the hard drive?  I could well be wrong but the fact you had read errors at boot before and now you can't create a partition point in the direction of a hard drive failure :(

its an SSD not an HDD so it doesnt make any noises at all, its basically a giant flash drive.

---

### Post by r-mo on 2010-06-15
oops, it's an ssd there won't be any clicking then ;) Still the input/output error points in the direction of hardware failure again.  Try opening a terminal (Accessories->terminal) type the command
```
sudo fdisk -lu
``` 
and copy/paste the output

---

### Post by jasoncyrus on 2010-06-15
ok will do that, will have to type it here since I dont yet know how to get it to access my wireless network. (Why is do I ALWAYS get errors that are a pain in the *** when i least need them)

Disk /dev/sda: 4034MB, 4034838528 bytes
225heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units=sectors of 1*512 = 512 bytes
Sector size (logical/physical):512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesnt contain a valid partition table

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units=sectors of 1*512 = 512 bytes
Sector size (logical/physical):512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk identifier: 0x8ec18ec1

Device Boot     start    end            blocks          Id   system
/dev/sdb1        63       31519529   15759733+   83  Linux

Disk /dev/sdc: 16.1 GB, 16053960192 bytes
16 heads, 32 sectors/track, 61240 cylinders, total 31355391 sectors
Units = sectors of 1*512 = 512 bytes
Sector size (logical/physical):512 bytes/512 bytes
 I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk Identifier 0x000427fe

Device Boot         Start   End             Blocks          ID   System
/dev/sdc1   *        32      31355390    15677679+   c     W95 FAT32  (LBA)

---

### Post by bazzal1941 on 2010-06-15
I think r-mo may have a point but in the meantime I'll make up a usb stick to see if I can help you further.

I don't think you mentioned which model eee you had.

---

### Post by jasoncyrus on 2010-06-15
> **bazzal1941 said:**
> I think r-mo may have a point but in the meantime I'll make up a usb stick to see if I can help you further.

I don't think you mentioned which model eee you had.


Umm its the 20GB model, 7.5inch?

---

### Post by bazzal1941 on 2010-06-15
It sounds like you have a 901 which is a 4gb + 16gb. I am willing to try and shepherd you through an install but I do not wish to do jump across what r-mo is trying. Lets see what comes out of that.

---

### Post by jasoncyrus on 2010-06-15
> **bazzal1941 said:**
> It sounds like you have a 901 which is a 4gb + 16gb. I am willing to try and shepherd you through an install but I do not wish to do jump across what r-mo is trying. Lets see what comes out of that.

yeah thats the model i have. I'd be up for your guidance :) Just hitting walls of errors on my own atm.

---

### Post by bazzal1941 on 2010-06-15
OK I'm assuming your installing some version of Ubuntu 10.04.

First of all (you may have said this) when  you boot from the usb do you get as far as the Ubuntu opening screen with the install icon.

---

### Post by jasoncyrus on 2010-06-15
> **bazzal1941 said:**
> OK I'm assuming your installing some version of Ubuntu 10.04.

First of all (you may have said this) when  you boot from the usb do you get as far as the Ubuntu opening screen with the install icon.

when I boot from the USB it loads all the way to the Installer boot menu

It can also go as far as the desktop (totally running off the USB stick)

---

### Post by bazzal1941 on 2010-06-15
1. There will be an icon *Install Ubuntu* or something similar. Go for it.

2. Then you go through steps 1 to 3 and get to the *Prepare Disk Space* screen.

3. Just some background you have a 4G drive and a 16G drive. What we are going to try and do is put the system on the 4G drive and the home directory on the 16G drive. That way if in the future you want to upgrade or try a different distro you can do so without disturbing your user data and settings.

4. If you look at where it says *Erase and use the entire disk* you will see in the greyed out box it uses the 4G drive. It would put the system and home on the same drive and you would soon run out of space and wonder why it isn't using the 16G.

5. Select *Specify partitions manually* -> *Forward*

6. I am not sure exactly what you will see. It should be something like:

[INDENT]*/dev/sda*[/INDENT]
[INDENT][INDENT]*/dev/sda1 ext? .......*[/INDENT][/INDENT]
[INDENT][INDENT]*/dev/sda5 swap .......*[/INDENT][/INDENT]
[INDENT]*/dev/sdb*[/INDENT]
[INDENT][INDENT]*/dev/sdb1 ext? .......*[/INDENT][/INDENT]

7. Before we go any further let me know what you display.

---

### Post by jasoncyrus on 2010-06-15
> **bazzal1941 said:**
> 1. There will be an icon *Install Ubuntu* or something similar. Go for it.

2. Then you go through steps 1 to 3 and get to the *Prepare Disk Space* screen.

3. Just some background you have a 4G drive and a 16G drive. What we are going to try and do is put the system on the 4G drive and the home directory on the 16G drive. That way if in the future you want to upgrade or try a different distro you can do so without disturbing your user data and settings.

4. If you look at where it says *Erase and use the entire disk* you will see in the greyed out box it uses the 4G drive. It would put the system and home on the same drive and you would soon run out of space and wonder why it isn't using the 16G.

5. Select *Specify partitions manually* -> *Forward*

6. I am not sure exactly what you will see. It should be something like:[INDENT]*/dev/sda*[/INDENT][INDENT][INDENT]*/dev/sda1 ext? .......*[/INDENT][/INDENT][INDENT][INDENT]*/dev/sda5 swap .......*[/INDENT][/INDENT][INDENT]*/dev/sdb*[/INDENT][INDENT][INDENT]*/dev/sdb1 ext? .......*[/INDENT][/INDENT]7. Before we go any further let me know what you display.


Ok doing that now, will give you a step by step just to be sure

Using ubuntu netbook version 10.4 or something

chose Install to a hard disk, chose english, UK time, UK keyboard layout

hmmm 

Erase and use the entire disk, selected 4GB ATA ASUS-PHISON OB S

and

Select partitions manually (advanced)

are on the same page, do i still pick the latter?

With the latter chosen i get

/dev/sda
/dev/sdb
  /dev/sdb1  ext3

EDIT: It USED to say this at the start but then i attempted to delete the partitions and it kept saying there was no root structure after i placed in new partition details

[INDENT]*/dev/sda*[/INDENT][INDENT][INDENT]*/dev/sda1  ext? .......*[/INDENT][/INDENT][INDENT][INDENT]*/dev/sda5  swap .......*[/INDENT][/INDENT][INDENT]*/dev/sdb*[/INDENT][INDENT][INDENT][I]/dev/sdb1  ext? .......
[/I][/INDENT][/INDENT]

---

### Post by bazzal1941 on 2010-06-15
OK thats good, your in the right place and it sounded as if you were almost there. The thing about ubuntu is it is not going to make decisions about what to put on a partition. You have the choice.

OK let me get to where you are

1. So after you deleted the partitions you should see something like:

[INDENT]*/dev/sda*[/INDENT]
[INDENT][INDENT]*free space ... 4043 MB*[/INDENT][/INDENT]
[INDENT]*/dev/sdb*[/INDENT]
[INDENT][INDENT]*free space ... 16139 MB*[/INDENT][/INDENT]

If you do not, deleting partitions should get you to this state.
If not let me know what you see.

2. Select the second line *free space*

3. The *Add* button should become active and the create partition window should appear.

4. Enter

*Type for the new partition* -> Primary
*New partition size* -> 3800
*Location for new partition* -> Beginning
*Use as* -> Ext2
*Mount point* -> /

-> *OK*

5. Now select line 3 *free space* -> *Add*

6. Back at the create partition window

*Type for the new partition* -> Logical
*New partition size* -> 234
*Location for new partition* -> Beginning
*Use as* -> Swap area
*Mount point* -> greyed out

-> *OK*

7.  Now select line 6 *free space* -> *Add*

8. Back at the create partition window

*Type for the new partition* -> Primary
*New partition size* -> 16139
*Location for new partition* -> Beginning
*Use as* -> Ext 2
*Mount point* -> /home

-> *OK*

9. It should look like:

[INDENT]*/dev/sda*[/INDENT]
[INDENT][INDENT]*/dev/sda1 ext2 / 3798 MB unknown (format is ticked)*[/INDENT][/INDENT]
[INDENT][INDENT]*/dev/sda5 swap    232 MB unknown *[/INDENT][/INDENT]
[INDENT]*/dev/sdb*[/INDENT]
[INDENT][INDENT]*/dev/sdb1 ext2 /home 16137 MB unknown MB*[/INDENT][/INDENT]

10. If it is like this you are good to go, if not get back to me.

There may be some delay in my replying because I am off to my local to watch Brazil v North Korean, although I am neither Brazilian or Korean. Just a football fan.

---

### Post by jasoncyrus on 2010-06-15
It worked to about half way then I got this error

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

I'm going to try it with a different memory stick

starting to look more and more like toasted SSD :(

---

### Post by bazzal1941 on 2010-06-15
Half-time

Next time you set up the partitions, tick the format box for /dev/sdb. It might tell us something.

---

### Post by jasoncyrus on 2010-06-15
do I do anything on the advanced option on the ready to install screen?

---

### Post by jasoncyrus on 2010-06-15
Dangit, got to 93% and got

"Executing grub-install /dev/sda failed"

This is a fatal error"

:mad:

I then got a window that said Bootloader install failed.

It wont install on sda or sda1 :(

EDIT: Wont install on sdb or sdb1 either @_@

And when I tried to reinstall it for a billionth time...it now gives an ext2 file system creation failure error in partition #1 of SCSI2 (0.0.0)(sda)

---

### Post by bazzal1941 on 2010-06-15
I am sorry I cannot help. I notice there are quite a few forums addressing this particular error. I will have a look and see if I find anything.

---

### Post by jasoncyrus on 2010-06-15
We almost got there, thanks for our help so far =)

---

### Post by jasoncyrus on 2010-06-15
IT WORKS! Id on know how i fixed it xD I chose to install it along side any existing OS, via running the OS from the card and it worked!

woohoo! thanks for all the help! I *really* needed it and you helped me solve my problem! <3

oh i know what i did, I installed it on the 16gb part:)

EDIT: Redoing the install using your method but just with the 16GB drive. if it works then it means the 4GB drive is toasted, which is ok tbh. 4 gigs lost is better than buying a whole new laptop

Indeed it has worked! Hurray!

So all in all was a toasted drive.

---

