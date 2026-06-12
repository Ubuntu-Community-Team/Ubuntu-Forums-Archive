---
title: "Auto-mount of partition"
date: 2009-11-19
forum: General Help
---

### Post by Orbaneqtrx5 on 2009-11-19
i have 3 partitions on my HD and i want to know if i can have one of my partitions always mounted as a desktop shortcut instead of having to mount it each and every time to use it as a media server. thankyou

---

### Post by PrarieD0G on 2009-11-19
[s]You'll want to get the ntfs-3g drivers. Search the package manager to download it. Then run ntfs-3g app that comes with it, and that should get everything set up for you so that your partitions will automount on boot. An icon will also be placed on the desktop for each mounted partition.

This is all of course assuming the partitions you want to mount are in the NTFS format...[/s]

Nevermind, I misunderstood what you were asking. My bad.

---

### Post by mechro on 2009-11-19
Install **pysdm** via Synaptic. Once installed you'll find it in the Menu as **System > Administration > Storage Device Manager**.

You can use this tool to configure the partition you want automounted at boot-up.

---

### Post by ajgreeny on 2009-11-19
You'll need ntfs-config as well.  That's the package that lets you configure the mounting of the ntfs partitions with ntfs-3g.

If they are formatted as some other file system you will need to add a line to /etc/fstab to do this. 

Here are some appropriate lines for the situation, just change the device name of the partition to suit your machine, and don't forget to make the mount point directory first with ```
sudo mkdir /media/directoryname
```Automount linux partition. Add line to /etc/fstab:-
/dev/sdb1 /media/directoryname ext3 defaults, relatime 0 1

Automount fat32 windows. Add line to /etc/fstab:-
/dev/sdb1 /media/directoryname vfat defaults,user,dmask=027,fmask=137 0 0

Automount ntfs windows. Add line to /etc/fstab:-
/dev/sda1 /media/directoryname ntfs nls=utf8,umask=0222 0 0
or
/dev/sda2 /media/directoryname ntfs-3g defaults,locale=en_US.utf8 0 0

---

### Post by amaz1ng on 2009-11-19
When I did the same thing just two days ago, a google search of "automount partition ntfs ubuntu 9.10" sent me here: [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

I recommend following those instructions, they worked beautifully for me.

---

### Post by rpaskudniak on 2009-11-19
Folks,

The pysdm utility appears in the System->Administration menu as "Storage Device Manager". (I edited the menu to preface it with PYsdm.)  In any case..

When I open the app and select my Windows partition on /dev/sda1, it warns me that
> /dev/sdb1 hasn't been configured. Configure it now?
I click [Cancel] because I don't know what this configuration entails.  Documentation on pysdm is awful scanty - the man page is a joke.

Oh, BTY, it almost escaped my notice that it complained about /dev/sd**[SIZE="3"]b[/SIZE]**1 when I selected /dev/sd**[SIZE="3"]a[/SIZE]**1.  It does not issue this warning when I select my /boot or /home partitions but does complain when I select the swap partition, /dev/sda2: > [/dev/sdc1 hasn't been configured]
That's insane! sdc1 is my flash memory stick!  Nothing to do with my swap partition!

So, to return tp my main question: What does the system do to the device (AKA partition) when it "configures" it.  Is it merely making an entry in a list (like /etc/fstab) or is it really planning something more sinister?  (Sir, are your intentions honorable? >;-)  ) THe next question is: Will it configure the device I selected or the one it mysteriously complained about?

Questions! Questions!  SIGHHhhh...

---

### Post by mechro on 2009-11-20
@ rpaskudniak

PySDM's default "configure" is to set a simple device automount entry in fstab... even then you have to click an "Apply" button. There are all sorts of bells and whistles you can add if required, and you can easily remove the fstab entry if required. Just go ahead with the "Configure it now" thingy.. it won't hurt. :D

---

### Post by Elcid247 on 2009-11-22
pysdm messes with fstab which is quite a mess.

i did 2 tutorials about this,

[old 1]("http://o-saad.blogspot.com/2009/10/automount-in-karmic.html")

[new 1]("http://o-saad.blogspot.com/2009/11/better-automount-rules-in-karmic.html")

and search is ur best friend :D

---

### Post by awiesner on 2009-11-22
Hi I tried using pysdm to configure the settings to auto mount my partitions. I think I must have really messed something up with it because now it won't boot. attached is a picture of the error message I am getting. Is there any way to fix this?

---

### Post by mechro on 2009-11-23
> **awiesner said:**
> Hi I tried using pysdm to configure the settings to auto mount my partitions. I think I must have really messed something up with it because now it won't boot. attached is a picture of the error message I am getting. Is there any way to fix this?

You'll need to restore your original fstab file. Pysdm should have made a back-up...

If you're on the LiveCD open a Terminal and do **gksudo nautilus**

Either from Places or Computer go to your Ubuntu installation. It might be labelled disk or disk-1 or something else... you'll have to figure that out yourself.
Then go into the **etc** folder. In there should be **fstab** and hopefully **fstab.BAK**

Copy and paste both of these as copies in case you still have problems and you need to reconstruct fstab. Delete the **fstab** file and rename **fstab.BAK** as **fstab**

Reboot your Ubuntu installation

---

### Post by awiesner on 2009-11-25
> **mechro said:**
> You'll need to restore your original fstab file. Pysdm should have made a back-up...

If you're on the LiveCD open a Terminal and do **gksudo nautilus**

Either from Places or Computer go to your Ubuntu installation. It might be labelled disk or disk-1 or something else... you'll have to figure that out yourself.
Then go into the **etc** folder. In there should be **fstab** and hopefully **fstab.BAK**

Copy and paste both of these as copies in case you still have problems and you need to reconstruct fstab. Delete the **fstab** file and rename **fstab.BAK** as **fstab**

Reboot your Ubuntu installation
thanks, but I couldn't not find a fstab.bak file. below are the contents of the fstab file
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

---

### Post by Arup on 2009-11-25
Go to system>administration>disk utility and select the partiion and selct bootable. It would be auto mounted next time you boot.

---

### Post by mechro on 2009-11-25
> **awiesner said:**
> thanks, but I couldn't not find a fstab.bak file. below are the contents of the fstab file
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

That looks like your LiveCD's fstab, not your Ubuntu hard drive installation's fstab.

Did you identify whether your Ubuntu installation is **disk** or **disk-1** or similar? Is it even there?

---

### Post by awiesner on 2009-11-25
> **Arup said:**
> Go to system>administration>disk utility and select the partiion and selct bootable. It would be auto mounted next time you boot.

I did this but now get the error message attached below

> **mechro said:**
> That looks like your LiveCD's fstab, not your Ubuntu hard drive installation's fstab.

Did you identify whether your Ubuntu installation is **disk** or **disk-1** or similar? Is it even there?
I'll check this later. I need to go home for the holiday. but could you possibly elaborate or point me to where to find how I can identify whether my installation is disk or disk-1?

thanks

---

### Post by mechro on 2009-11-25
On the LiveCD, when you did gksudo nautilus, wasn't there a list of stuff in the panel on the left hand side? Change the panel to list Places if it's not already doing that.

Unless things have changed significantly in 9.10 your Ubuntu installation should be disk or disk-1 or similar.

---

### Post by awiesner on 2009-11-27
alright I deleted the fstab file and changed the fstab.bak file to fstab (after backing them up). it still won't boot, the new error message that I am getting is attached below

---

### Post by mechro on 2009-11-27
Can you post the contents of those fstab back ups?

---

### Post by awiesner on 2009-11-27
> **mechro said:**
> Can you post the contents of those fstab back ups?
fstab
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                          0  0  
# Entry for /dev/sda6 :
UUID=85992e34-6551-4287-92f5-9a4699fe1e3d  /               ext4         users                             0  1  
# Entry for /dev/sda5 :
UUID=27ddd852-60ab-4cff-9c28-c9c9c86f3a95  none            swap         sw                                0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8             0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8          0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,users,umask=000  0  0  

```fstab.bak
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                          0  0  
# Entry for /dev/sda6 :
UUID=85992e34-6551-4287-92f5-9a4699fe1e3d  /               ext4         users                             0  1  
# Entry for /dev/sda5 :
UUID=27ddd852-60ab-4cff-9c28-c9c9c86f3a95  none            swap         sw                                0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8             0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8          0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,users,umask=000  0  0  

```thanks

---

### Post by mechro on 2009-11-27
Are you sure pysdm did anything? Those files have been generated by ntfs-config which is a different tool, unless you've used ntfs-config in the past and then used pysdm.

I'm not sure about the entry for / (root). In your current fstab file try changing it to...

```
# Entry for /dev/sda6 :
UUID=85992e34-6551-4287-92f5-9a4699fe1e3d  /    ext4    relatime,errors=remount-ro     0  1  
```

---

### Post by Muskegman on 2009-11-27
[http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/](http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/)


I found this site very imformative

---

### Post by stinkeye on 2009-11-27
> **Muskegman said:**
> [http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/](http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/)


I found this site very imformative
Thanks Muskegman, worked for me to auto-mount an internal ext3 partition.

---

### Post by rpaskudniak on 2009-11-29
Mechro,
Thanks for the reassurance.  Indeed, it seems to have done no harm by clicking on OK.  However, it did mount the wrong partition, /dev/sd[SIZE="2"]b[/SIZE]1 rather than the selected /dev/sda1.  I have submitted bug [[COLOR="Blue"]490046[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/pysdm/+bug/490046") to see if someone can do something about this silliness.  In the meantime, patient fellow that I am, I kept hunting around and followed the link supplied by ajgreeny to [[[COLOR="Blue"]HowTo: Automount NTFS Drives[/COLOR]]("http://ubuntuforums.org/showthread.php?t=785263")].  That seems to have worked.

Of course, I won't be certain of the harmlessness of the selection or the success of ntfs-config (ajgreeny's method) until I reboot.  When I achive the desired success I will consider this issue almost solved.

... Almost?  Well, ntfs-config is not without its little wart: I was unable to get it to display the partitions on /dev/sdb and there are a couple of partitions on that device I want always mounted when I boot ubuntu.  Yes, I could do it by editing /etc/fstab manually but there's so much room for errors that way. I'd like to do it the Ubuntu way, if possible.

Advice on ntfs-config, anyone?  When I installed ntfs-config, there was another package available, mountmanager.  I did not install that; I'd rather first hear advice on ntfs-config.

Thanks much!

---

### Post by mechro on 2009-11-30
> **rpaskudniak said:**
> Mechro,
Thanks for the reassurance.  Indeed, it seems to have done no harm by clicking on OK.  However, it did mount the wrong partition, /dev/sd[SIZE="2"]b[/SIZE]1 rather than the selected /dev/sda1.  I have submitted bug [[COLOR="Blue"]490046[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/pysdm/+bug/490046") to see if someone can do something about this silliness.


I've just checked this on my system and got the same error. It is indeed silly... I think I'll go back to manually editing fstab. :icon_frown:

---

### Post by jamesisin on 2009-11-30
Since this has not yet been marked as Solved, I thought I'd throw my two cents down.

First of all, you say that you are going to use this as a share from your Ubuntu system and that you'd like to do things "the Ubuntu way".  In that case I recommend formatting the drive with ext3 (or 4) and running a Samba share.  Samba can share an ext3 drive with any system, because Samba acts as a liaison between the client and the host.

Second, here is my tutorial on adding drives to an Ubuntu system:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

---

### Post by rpaskudniak on 2009-11-30
James,
I think there has been a bit of a misunderstanding here.  While I am indeed interested in adding additional ext3 partitions to fstab, my immediate interest was adding my Windows AKA ntfs partition - the Windows boot partition - to be automatically mounted so that my Windows documents should be accessible to everyone when I boot Ubuntu.  Ext3 was not part of this equation.

Also, in my (currently) limited understanding of Samba, it seems to be a Unix/Linux daemon to allow Windows/Mac clients to read files from a Linux file server across a network. My situation is reading ntfs files from Windows partition while running Linux.  I don't see how Samba would help me here.  

BTW, this is the the entry ntfs-config created for me in fstab:
> [FONT="Courier New"][SIZE="2"]/dev/sda1  /media/Win-System  ntfs-3g      defaults,locale=en_US.UTF-8    0  0 [/SIZE][/FONT]

pysdm was failing in this regard, since, as I have pointed out, it was missing my sda1 partition, diverting to the sdb drive.  Hence, ntfs-config got be over that hump.

But now that we are on the subject, I will add some fat to the fire.  There is another Windows partition I want automounted, this time on the second drive, specifically /dev/sdb2.

Here, ntfs-config failed me, as I feared it would: It would not even recognize that there is another drive/partition I might want to mount. Going back to pysdm, which had fixated on the /dev/sdb drive, it did mount sdb2 for me, making this entry in fstab.  This succeeded, basically, but it assigned the mount-directory name as /dev/sdb2 - the same as the file system name.  That won't do; I want it in under /media, the same as the first ntfs volume.

I gave in and did it manually.  I manually created /media/Media and edited fstab to comment out the entry created by pysdm and enter this change:
> [FONT="Courier New"][SIZE="2"]#/dev/sdb2 /media/sdb2        ntfs nls=iso8859-1,umask=000,gid=users,owner,uid=root  0  0  
/dev/sdb2   /media/Media       ntfs nls=iso8859-1,umask=000,gid=users,owner,uid=root  0  0[/SIZE][/FONT]
BTW, with my current level on knowledge of all things Ubuntu, I would not have been able to formulate the options, not with a dozen readings of the man page.  What ***does*** [FONT="Courier New"][COLOR="Red"]nls=iso8859-1[/COLOR][/FONT] mean anyway?

As for the other ext3 partitions on /dev/sdb, now that I see that pysdm seems up to the task (due to ***its*** choice of mount directory) I guess I will be manually automounting those as well.

[SIZE="1"]Actually, since one of them is an extended volume intended for an Informix database server, I will probably be using raw volumes in subpartitions.  But let's wail until I post a _new_ thread about that before y'all jump on me with Linus's view on raw volumes and the probable lack of need for them.[/SIZE]

BTW, this was successfully mounted as desired at reboot time.

[LIST]
[*]Bottom line 1: ntfs-config was good for one-shot. I usually drink more than that in one sitting. ;)
[*]Bottom Line 2: pysdm appears too buggy for general use.
[/LIST]

---

### Post by jamesisin on 2009-11-30
Sorry, I misunderstood the direction in which you were trying to share.

Things are looking good in your fstab.  I would suggest using UUID's instead of /dev paths (I just ran into some problems with that).  You can get a device's UUID easily enough:

sudo tune2fs -l /dev/sda2 | grep UUID

(Substitute sda2 with the device in which you are interested.)

Has this change in fstab solved the problem?

---

