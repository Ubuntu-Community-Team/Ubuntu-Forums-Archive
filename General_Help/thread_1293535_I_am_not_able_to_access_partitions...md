---
title: "I am not able to access partitions.."
date: 2009-10-17
forum: General Help
---

### Post by aprashanth on 2009-10-17
My problem is this I am not able to access.. 
The partitions,.. how can I do that....

The  error That is being displayed is

Unable to mount the volume 'New Volume'.

How to I mount the device.. 
please help...

---

### Post by rudi009 on 2009-10-17
isn't there any option to see details??if yes please post.

---

### Post by aprashanth on 2009-10-17
There is a detail option.. But i am not able to copy it..
I have even taken a screen shot but unable to paste those here..
It says.. unclean shutdown.. and many more things..

Is this information enough

---

### Post by rudi009 on 2009-10-17
tried restart???
are you on duel boot?is windows on hibernate??
upload the screenshot to some photo sharing website and paste link.simple!

---

### Post by danwood76 on 2009-10-17
Are you trying to mount an NTFS partition (windows)
I would assume yes.

Boot up windows and mount the volume then shutdown and you will be able to mount it in Ubuntu.

This is because the ntfs-3g driver wont mount an ntfs partition if it hasnt been shutdown due to data loss.

---

### Post by aprashanth on 2009-10-17
yes I have a dual boot.. and the windows is not in hibernation mode..


This the link for the screen shot.. which I have taken of the details.. 
[http://www.flickr.com/photos/43662653@N02/4019174130/](http://www.flickr.com/photos/43662653@N02/4019174130/)

---

### Post by aprashanth on 2009-10-17
[IMG]http://http://www.flickr.com/photos/43662653@N02/4019174130/[/IMG]

---

### Post by rudi009 on 2009-10-17
> **aprashanth said:**
> yes I have a dual boot.. and the windows is not in hibernation mode..


This the link for the screen shot.. which I have taken of the details.. 
[http://www.flickr.com/photos/43662653@N02/4019174130/](http://www.flickr.com/photos/43662653@N02/4019174130/)

very helpful link................did you try it??lol!!!

---

### Post by danwood76 on 2009-10-17
Have you tried mounting the drive in winblows (if its a hard disk it should do this automagically) and then rebooting into Ubuntu?
This will solve the error you describe.

---

### Post by aprashanth on 2009-10-17
Try what... restarting.. I did,, but that did not work..

---

### Post by aprashanth on 2009-10-17
> **danwood76 said:**
> Have you tried mounting the drive in winblows (if its a hard disk it should do this automagically) and then rebooting into Ubuntu?
This will solve the error you describe.
I know that..But I am not able to access windows...

---

### Post by danwood76 on 2009-10-17
Well you can force the partition to load.

To work out what partition we require can you post the output of the following command in the terminal?

```

sudo fdisk -l

```
Also if you can tell us the size of the partition that might also help if you have a few.

---

### Post by HNS-I on 2009-10-17
Can you open up a terminal and run mount -t ntfs /dev/sd(?) /mnt ( i hope you know which drive it is).
If you get an error try with -f for force.
You can copy paste the text from the terminal.

---

### Post by aprashanth on 2009-10-19
> **danwood76 said:**
> Well you can force the partition to load.

To work out what partition we require can you post the output of the following command in the terminal?

```

sudo fdisk -l

```
Also if you can tell us the size of the partition that might also help if you have a few.
tsrinu@tsrinu-desktop:~$ sudo fdisk -l
[sudo] password for tsrinu: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37fcb925

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        7052    36162315    7  HPFS/NTFS
/dev/sda3            7053        9729    21503002+   5  Extended
/dev/sda5            7053        9612    20563168+  83  Linux
/dev/sda6            9613        9729      939771   82  Linux swap / Solaris
tsrinu@tsrinu-desktop:~$ 


this is the output of the command..

---

### Post by aprashanth on 2009-10-19
> **HNS-I said:**
> Can you open up a terminal and run mount -t ntfs /dev/sd(?) /mnt ( i hope you know which drive it is).
If you get an error try with -f for force.
You can copy paste the text from the terminal.
Bro,

 I tried the command  mount -t ntfs /dev/sda1 /mnt

I have got this error.,.
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /mnt ntfs-3g force 0 0
root@tsrinu-desktop:/home/tsrinu# mount -t ntfs /dev/sda2 /mnt
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt ntfs-3g force 0 0


finally I tried to force option..

root@tsrinu-desktop:/home/tsrinu# mount -t ntfs /dev/sda1 /mnt -o force
$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.


Now ecen the icon indicating the drive has disappered.. what will happen to the data.. will all that be lost..Is there is any chance that I access my data again..

---

### Post by danwood76 on 2009-10-19
It will be mounted to /mnt
Its much cleaner if you mount it to a /media directory as Gnome will pick that up.

To do this:

```

sudo umount /dev/sda1
sudo mkdir /media/win
sudo mount -t ntfs-3g /dev/sda1 /media/win

```

The partition will then be visible in gnomes places, also not there is no need to force the second time as the log has already been reset.

---

### Post by aprashanth on 2009-10-19
> **danwood76 said:**
> It will be mounted to /mnt
Its much cleaner if you mount it to a /media directory as Gnome will pick that up.

To do this:

```

sudo umount /dev/sda1
sudo mkdir /media/win
sudo mount -t ntfs-3g /dev/sda1 /media/win

```

The partition will then be visible in gnomes places, also not there is no need to force the second time as the log has already been reset.
I am getting an error message again and its this...

root@tsrinu-desktop:/home/tsrinu# sudo mount -t ntfs-3g /dev/sda1 /media/win
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/win -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/win ntfs-3g force 0 0
root@tsrinu-desktop:/home/tsrinu#

---

### Post by danwood76 on 2009-10-19
Well force it again.
I notice you are using the root shell, this means you dont need to use sudo.

so now
```

mount -t ntfs-3g /dev/sda1 /media/win -o force

```

Also please put anything you dump from the terminal in code tags as it makes it a lot easier to read.

---

### Post by aprashanth on 2009-10-19
> **danwood76 said:**
> Well force it again.
I notice you are using the root shell, this means you dont need to use sudo.

so now
```

mount -t ntfs-3g /dev/sda1 /media/win -o force

```

Also please put anything you dump from the terminal in code tags as it makes it a lot easier to read.
Thanks a lot it worked.. ..
it would be of great help if you say me where the code tag is..

---

### Post by danwood76 on 2009-10-19
Basically you end the code section with [/code] and start it with [code]
I think if you select the required text and click the # in the advanced editor it does the same thing.

---

### Post by aprashanth on 2009-10-19
> **danwood76 said:**
> Basically you end the code section with [/code] and start it with [code]
I think if you select the required text and click the # in the advanced editor it does the same thing.
Thanks a lot...

---

