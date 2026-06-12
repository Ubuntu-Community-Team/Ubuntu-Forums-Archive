---
title: "Dual booting..."
date: 2009-08-24
forum: General Help
---

### Post by SmexyPenguin18 on 2009-08-24
I've been trying to dualboot windows xp and ubuntu on different harddrives for about a momth or so. I tried a bunch a different methods.  I got them working but my one old harddrive is really loud!  I couldn't stand i so i open my computer and cut the red wire going to the noisey harddrive and put a switch on it. Then i put my harddrive with windows xp (quiet one) as master and an empty one (noisey one) as slave.  I put in an ubuntu install disc and installed it onto my noisey one.  My plan was to use grub to dualboot (which i have working) but after i boot to my windows drive turn off the drive with grub on it (noisey one) but windows stays at the boot screen until i switch the noisey drive back on.  So i thought after its done booting i could turn the noisey drive off but after a while my computer freezes.  I can get it to unfreeze by switching the noisey drive on again.  I need to know how i can dualboot windows xp and ubuntu(windows on my quiet drive and ubuntu on my noisey drive) but when i boot to windows be able to keep my ubuntu drive off (noisey drive) off without it freezing.

---

### Post by SmexyPenguin18 on 2009-08-25
bump...  please help me! I'm desperate and don't know what to do now!

---

### Post by P4man on 2009-08-25
Its a TERRIBLE idea to switch a drive on or off like that when the computer is running. You'll send sparks flying everywhere and you'll kill your hardware. Dont touch that switch unless the power is OFF.

For the dual boot, the easiest in your case is to restore the windows boot loader on the windows drive, and use grub on the ubuntu drive. Configure grub to chainload the windows bootloader, so if you boot grub, you'll have the choice. Set your bios to boot from the ubuntu drive first, if its turned off, it will  automatically try the other drive with the windows bootloader to boot windows.

---

### Post by SmexyPenguin18 on 2009-08-25
Oh yea i know but its a crappy computer so i gave it a shot anyway.

I'm a complete newb to grub so could you tell me how i would configure grub to do that?

---

### Post by P4man on 2009-08-25
first, turn your computer OFF. Then turn that ubuntu harddisk off with your suicide switch ;).

Boot from a windows installation cd, enter recovery mode and run "FIXBOOT". see if windows boots without issues.

Turn the PC off, the suicide switch on, pc on, go in to your BIOS, and set the ubuntu drive as first boot device.

Boot it and report what happens. It wont work yet, but I need to know if it boots windows or grub or nothing at all. Have an ubuntu  live CD at hand, we'll need it later.

---

### Post by SmexyPenguin18 on 2009-08-25
Lol
And I don't have the installation cd.  A friend gave the computer to me with windows xp on it already.  What can i do instead?

---

### Post by P4man on 2009-08-25
If you turn off the ubuntu drive, does windows start ? I guess not, but checking anyway.

Your problem is that you need a bootloader to boot windows, and it cant reside on the ubuntu drive, since you want that turned off when you use windows. And, you cant restore the windows bootloader cause you dont have the cd..

Well, I guess you could resize the windows partition and make a boot partition on the windows drive and install grub on that. You'll need to make room, so boot from a live cd, resize the windows partition and make a new small partition on that drive to install grub upon. Depending how many kernels you want to be able to put there, make it 100 Mb or so.  Format it as Ext2. once you've done that, reboot, boot the live cd again, and report the output of:

```
sudo fdisk -l
```

---

### Post by SmexyPenguin18 on 2009-08-25
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe11be11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9701    77923251    7  HPFS/NTFS
/dev/sda2            9702        9726      200812+  83  Linux

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris

```
I didn't quite understand what you said.  Should i install grub to the partition i just created now?

---

### Post by P4man on 2009-08-25
Yes thats the idea. Try this now:

```
sudo mount /dev/sda2 /boot
sudo grub-install /dev/sda2
```

when that finishes, post the output of:

edit, must be drunk

```
cat /boot/grub/menu.lst
```

to see if it found your windows or not. If there is a windows entry in there, you can test it by powering your ubuntu drive off, and see if grub loads windows.

---

### Post by SmexyPenguin18 on 2009-08-25
This is going to sound really nooby but i mount the sda2 and install grub to it. Then run this: ```
cat /boot/grub/menu.lst
```
i get:```
cat: /boot/grub/menu.lst: No such file or directory
```
What did i do wrong?

---

### Post by P4man on 2009-08-25
its quite possible **I** did something wrong :) I dont install grub on its own partition every day.

can you post output of 

```
mount
```

and

```
ls /boot
```

?
Also, perhaps you can download this little script:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Save it your desktop. Right click it, properties, permissions and check "allow executing".

Then in a terminal, 

> cd Desktop
./boot_info_script032.sh


That will create a file on your desktop called 'RESULTS.txt". Attach that file this post, then I got all the info I could ever need.

I'll be out for a hours though, so maybe someone else can help you out meanwhile..?

---

### Post by SmexyPenguin18 on 2009-08-25
ls /boot:
```
grub  lost+found
```

And for mount it says command not found.  

And I'll be patient if you can't help now.

---

### Post by P4man on 2009-08-25
"mount" has to work, you must have made a typo there. But its ok, the information is also in that text file the script generated.

anyway  it looks like grub is installed on sda2 now, but it points to sdb for stage 2 (menu and stuff). Not sure why it did that, and thats exactly what we dont want :) Perhaps I forgot to ask you to make sda2 bootable :)

run partition editor from the live cd. Right click sda1 and select manage flags, and uncheck the boot flag. do the same for sda2, but set the boot flag. 

Next, to avoid any possible confusion by grub, turn off the machine, "turn off" your sdb (ubuntu) drive, reboot from the cd.

Now  redo these commands:

```
sudo mount /dev/sda2 /boot
sudo grub-install /dev/sda2

```

copy paste the output here.
You wont get a grub menu that lets you boot linux now, but we can add that later if grub at least boots from sda now.

---

### Post by SmexyPenguin18 on 2009-08-25
Here's the output of mount:
```
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
/dev/sda2 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

```
I'll have the other one in a minute.

Edit: Here's the other but i was having problems with my dvd drive so i ran them from on the harddrive.  I don't know if that'll make a difference. (is it needs to be from a live disc i'll just have to get my dvd drive to work.)
```
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda2 as (hd0,1)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

```

---

### Post by SmexyPenguin18 on 2009-08-25
Well guess what?...  all that was pretty much for nothing because i just found out i will be getting a 1 tb drive tommorow.  So i plan just to dualboot fromjust that drive.  Well now i have a another problem.  Ok so when i found out i started trying to undo what i just did. I deleted the ext2 partition on my windows drive and change the flags back to boot on the ntsc parttion on this drive.  I took out the ubuntu drive.  But now when i try to boot from the windows drive it says:
```
 GRUB Loading stage1.5


GRUB loading, please wait ...
Error 21
```

I didn't think there was any thing that had to do with grub on that partition so I'm completly stupted at what to do right now...

---

### Post by P4man on 2009-08-25
lol..
what did you expect would happen when you decided to delete the boot partition and remove the ubuntu drive? What bootloader would boot windows now ?

answer: none. You dont have one. You got remainders of grub on the MBR of your first drive, but that cant boot windows. I tried to give you 2 grubs, so you could boot each drive independently, even with the other drive disconnected.. and now you have none :)

You need to either
- reinstall windows bootloader from a windows cd
- use grub bootloader from the partition you just deleted
- use grub bootloader from the drive you just removed
- use grub from a drive that will arrive tomorrow :)

Whatever you decide, I think im gonna wait for that new drive of yours to arrive :)

---

### Post by SmexyPenguin18 on 2009-08-25
I don't know  i kinda just stopped carring i guess.  Is there anyway i can download the windows installation cd. (is that legal if i have windows already installed?) And just wondering what exactly is error 21?

---

### Post by SmexyPenguin18 on 2009-08-25
Alright i got a windows installation cd and ran the FIXBOOT command but i still get the grub error message.

---

### Post by P4man on 2009-08-26
try FIXMBR then

---

### Post by SmexyPenguin18 on 2009-08-26
Thankyou for all your help!  It went to waist but that was my fault i should have waited.  You were very helpful and friendly!

---

