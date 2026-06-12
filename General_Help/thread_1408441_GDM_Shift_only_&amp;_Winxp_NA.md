---
title: "GDM Shift only &amp; Winxp NA"
date: 2010-02-16
forum: General Help
---

### Post by sandman3838 on 2010-02-16
Hello Meierfra.

As you suggested here is the Subscription.
Originally I was going to re-set it my self using the information from here but I stopped because I was afraid of doing more damage.

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


Here is the Email that I sent to you:
**************************************** 

Can you help I did something I should not have. Sometime back I Changed the Splash screen unfortunately I didn't like the new one. I'm now using the default Splash but somewhere along the way I copied in the wrong script.

My Issues are:

1. The Grub MENU can only be displayed if I hold down the SHIFT key.

2. While using the SHIFT key everything is there just as we left except Winxp?

The Web page that I was using for reference is here.

[http://ubuntu-ky.ubuntuforums.org/sh....php?t=1333683](http://ubuntu-ky.ubuntuforums.org/sh....php?t=1333683)

The sections I was reading and using was in the first sections between :

Changing XSplash Background
and the start of
GDM and Network Connectivity

If you would rather I startup a Case/Subcription for this just let me know?

After this with it being almost back to the defaults settings, I'm leaving this stuff alone.

********** 
Another note:  Its not on there now but I did have Start-up Manager installed even though its capabilities were limited.

Could this be a solution:
[http://james.revillini.com/2010/01/08/solved-ubuntu-startup-manager-killed-my-windows-partition-entry-in-grub2/](http://james.revillini.com/2010/01/08/solved-ubuntu-startup-manager-killed-my-windows-partition-entry-in-grub2/)

or this?

[http://newyork.ubuntuforums.org/showthread.php?t=1319672&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1319672&page=2)

Finally I have attached a new boot_info_script054  file!

---

### Post by sandman3838 on 2010-02-16
Don't you wish Ubuntu opened up with this Splash:

[http://www.youtube.com/watch?v=ROEhFAgbHxE&feature=related](http://www.youtube.com/watch?v=ROEhFAgbHxE&feature=related)

---

### Post by sandman3838 on 2010-02-16
Here is another site that I found for for recover of the default GRUB.
[http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)


If you have a live CD, using it boot into a live session and follow the following steps (don't skip any unless you are know you are doing).

1) Open a terminal (Applications->accessories->terminal) and run this command

    [ubuntu]$ sudo fdisk -l

2) The above command will list out the partition table of your hard disk. After identifying your linux installed partition. Run this command, I will use the partition as /dev/sda1 you will have to replace it with yours.

    [ubuntu]$ sudo mount /dev/sda1 /mnt

3) If you have /boot on a different partition other then you need to mount it too. After identifying your /boot partition run this command (i am assuming it to be /dev/sda2)

    [ubuntu]$ sudo mount /dev/sda2 /mnt/boot

4) Now, mount the rest of the devices

    [ubuntu]$ sudo mount --bind /dev /mnt/dev/

5) Now, using chroot we will be allowed to run commands considering a specified root directory.

    [ubuntu]$ sudo chroot /mnt

Now, we will be chrooted as root considering /mnt as the root directory. So, from now we won't need sudo to execute commands as root

6) If you need to make some changes to /etc/default/grub, open the file in your favourite editor ( i will use vim)

    [root]$ vi /etc/default/grub

7) Make whatever changes you want to make and run update-grub to create the configuration file.

    [shredder12]$ sudo update-grub

In case you don't want to use this command or the reader doesn't use Ubuntu then you can use this alternate command to update grub(this will the default command for all grub2 installations).

    [root]$ grub-mkconfig -o /boot/grub/grub.cfg

8) If you want to install grub2 to MBR run this command.

    [root]$ grub-install /dev/sda

If you want to install it to some partition then use that partition name instead of /dev/sda e.g. /dev/sda1 for the second partition etc. Or if you want to install grub2 on another drive then you may use that name e.g. /dev/sdb for an external hard disk. 

You will have to resolve the names using fdisk -l command. (be careful while doing that)

9) If you faced some error while installing grub2 then you may want to run it with --recheck attribute.

    [root]$ grub-install --recheck /dev/sda

10) Once you are done with this either press Ctrl-D to exit chroot or type exit.

11) And then umount the partition you have mounted starting from /dev

---

### Post by meierfra. on 2010-02-16
> Sometime back I Changed the Splash screen unfortunately I didn't like the new one. I'm now using the default Splash but somewhere along the way I copied in the wrong script.
I don't think your problem has been caused by changing the splash screen.

Grub is installed correctly (so you don't need to reinstall grub) but "update-grub" does not seem to able to detect Windows.

Did you had any kernel or grub updates?  When you run the boot info script the last time, "dmraid" was no  install. But now the scripts detected some /dev/mapper devices, so  you must of dmraid install.  
So somehow "dmraid" got installed in the last couple of days. That might even be the cause of your problems.

Are you  still  able to boot into Windows by  setting the bios to boot from the Windows drive?

Could you post the output of

```
type dmraid
sudo blkid /dev/sda
sudo blkid -p /dev/sda
sudo blkid /dev/sdc
sudo blkid -p /dev/sdc
```

Then see what happens if you update your grub menu:

```
sudo update-grub
```

Did it detect Windows?


If not, let's see what happens if you create a custom item:


```
gksudo gedit /etc/grub.d/40_custom 
```

Add the following to the end of the file

menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 50600787600772d0
	drivemap -s (hd0) ${root}
	chainloader +1
}

save the file and run


```
sudo update-grub
```

Reboot and see whether you can boot XP from the Grub menu.

---

### Post by sandman3838 on 2010-02-16
Hello

I did as you asked and here is the info you asked for.
I'll be right back after the reboot.

kevin@Larry:~$ type dmraid
dmraid is /sbin/dmraid

kevin@Larry:~$ sudo blkid /dev/sda
[sudo] password for kevin: 
/dev/sda: TYPE="nvidia_raid_member" 

kevin@Larry:~$ sudo blkid -p /dev/sda
/dev/sda: VERSION="100" TYPE="nvidia_raid_member" USAGE="raid" 

kevin@Larry:~$ sudo blkid /dev/sdc
/dev/sdc: TYPE="nvidia_raid_member" 
kevin@Larry:~$ sudo blkid -p /dev/sdc
/dev/sdc: VERSION="100" TYPE="nvidia_raid_member" USAGE="raid" 

kevin@Larry:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-19-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-17-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-17-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

kevin@Larry:~$ gksudo gedit /etc/grub.d/40_custom

kevin@Larry:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-19-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-17-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-17-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
kevin@Larry:~$

---

### Post by sandman3838 on 2010-02-16
Back again!

Great news Winxp is there now.
However I'm not too sure if I like holding down the shift key down to make the GRUB menu display.

Is there a way to make the GRUB menu just stop until I select the OS I want?  Better what would I type in terminal for each of the three options>

1.  Just to make it stop.

2.  To make it go straight through using the SHIFT Command.

3.  To give the Grub menu a 20 sec delay.

Each option has its own advantage and disadvantage I can't make my mind up.

---

### Post by meierfra. on 2010-02-16
I don't like the solution with the custom menu,since it's  a work around  and not a fix.  I'm pretty sure that your problem is caused by the mysterious ""nvidia_raid_member".  One probably could use "dmraid" to delete those traces of raid.  But I'm not very   experienced with raid and I'm afraid that  might cause more harm than good. One also could  uninstall "dmraid", but since I don't know why it was installed in the first place,  that might break things.

So I guess  we stick with  "custom menu"  for now. I'll do some research on   the subject and might be able to suggest a better solution some time in the future.

> 1. Just to make it stop. 
```
gksudo gedit /etc/default/grub
```

Change

GRUB_TIMEOUT=?

to 

GRUB_TIMEOUT=-1

Save the file and run "sudo update-grub"

> 2. To make it go straight through using the SHIFT Command.

 Is that what you mean:

If you don't press  "SHIFT" during boot up, it stops at the GRUB menu.
If you press "SHIFT"  during boot, it boots straight into Ubuntu?

Can be done, but requires some tweaking.  I'll think about the best way to do it.


> 3. To give the Grub menu a 20 sec delay.


Do you mean  "Displays the Grub menu  for 20 second" and then boot Ubuntu? Then do

```
gksudo gedit /etc/default/grub
```

Change

GRUB_TIMEOUT=?

to 

GRUB_TIMEOUT=20

and

GRUB_HIDDEN_TIMEOUT=0

to 

#GRUB_HIDDEN_TIMEOUT=0


Save the file and run "sudo update-grub"


But if you mean

"Hide the Grub menu, but display a countdown for 20 second and then boot Ubuntu" 

then do

```
gksudo gedit /etc/default/grub
```

Change


GRUB_HIDDEN_TIMEOUT=0

to 

GRUB_HIDDEN_TIMEOUT=20

and 

GRUB_HIDDEN_TIMEOUT_QUIET=true

to

GRUB_HIDDEN_TIMEOUT_QUIET=false

Save the file and run "sudo update-grub"

---

### Post by meierfra. on 2010-02-16
> 2. To make it go straight through using the SHIFT Command. 

```
gksudo gedit /etc/grub.d/30_os-prober
```
Change


```
 if keystatus; then                                
    if keystatus --shift then;
       set timeout=-1
    else                     
      set timeout=0 
  fi
```

do

```
 if keystatus; then                                
    if keystatus --shift then;
       set timeout=[COLOR="Red"]0[/COLOR]
    else                     
      set timeout=[COLOR="Red"]-1[/COLOR]
  fi
```

Save the file and run

```
sudo update-grub
```

---

### Post by sandman3838 on 2010-02-16
Sorry for the delay My sister showed up!

From you previous statment above>

This got the GRUB menu to halt and let me select the correct OS.

Change

GRUB_TIMEOUT=?

to

GRUB_TIMEOUT=-1

Save the file and run "sudo update-grub"


************* 

Do you still want me to do the what you place in your last posting?

---

### Post by meierfra. on 2010-02-16
> Do you still want me to do the what you place in your last posting? 

Doesn't matter.  You just have to make up your mind  which of the three options from post #6 you would like to use.

The last instructions  are for for option 2).

---

### Post by sandman3838 on 2010-02-16
Im good with just having it stop!

It doesn't bug me at all!

While the system boots up I can get a cup of coffee and when I'm back in my chair I can select which OS I want?

I'm good if you are?

---

### Post by meierfra. on 2010-02-16
> I'm good if you are?
I'm good,too.

---

### Post by sandman3838 on 2010-02-16
Cool Man!  Again, thank you - thank you, for your help.

---

