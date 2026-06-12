---
title: "HDD Failed - Retrieve Files"
date: 2011-03-30
forum: General Help
---

### Post by leo123 on 2011-03-30
How can  a few files be retrieved from an installation of Ubuntu 10.10 where the mouse and keyboard freeze up?

There are two hard drives:
1st hard drive (80GB) where bootloader is installed has Ubuntu 9.04 – After a recent power outage, this hard drive started making a clicking sound every now and then. Therefore I started backing up files. In a couple of days the clicking sound happened more frequently so I shut the computer down.

2nd hard drive (320GB) has an installation of Ubuntu 10.10 that got the best of me because the mouse and keyboard kept freezing up. Ubuntu 10.04 did the same thing and none of the solutions found in these forums solved that issue, so hence 9.04. 

Each time the computer was booted it took longer and longer to get a desktop to load. I was able to boot into 10.10 long enough to copy a few files from 1st HDD (9.04) to 2nd HDD (10.10) and copy those files to an external HDD. 

Unfortunately, 10.10 froze up during the copying with 12 seconds to go. 

Today, when the computer was booted, there was a message about a Primary Disk error or something like that. (I'm guessing that HDD is toast now. I've never had a HDD fail)

Using 10.10 Live CD, I was able to get to a desktop, but couldn't copy the remaining files because of the Permissions on a couple of the files and 10.10 froze up again.

There were error messages of the in the beginning of the “clicking”, but they scrolled so fast and this is some of what it was:

53.30XXX atal.01: Status: {DRDY ERR}
                               Status: {ABRT ?????}

Any guidance on how to retrieve those few files would be greatly appreciated.

If I would have known how to move grub to the HDD with 10.10 on it, I would have, but when I tried that a while ago in a previous installation of 10.10 it didn't work, so I just stuck with the defaults.

---

### Post by seawolf167 on 2011-03-30
Sorry you had a drive fail! Thats never fun!

If the disk has failed, you don't have many options. You can send it in to a company that specializes in drive recovery, but that is *expensive*. If it is only the controller that failed, if you find the *exact same model/id number* controller board you can replace that and it may work.

I'd try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), see if that can recover any partitions or anything. If not, I'd say you still got something good out of this - the importance of backing up files!

---

### Post by leo123 on 2011-03-31
Seawolf, the files that I want to retrieve are not on the disk that failed.

The files are on the HDD w/ Ubuntu 10.10 which doesn't have a bootloader on it. The bootloader was on the disk that failed.

As I also stated, using the LiveCD, I am able to access the files, but there are permission issues on two of the files and 10.10 freezes.

Is there a way to add the bootloader to the disk with 10.10 on it or is there a way to get around the permission issues while using the Live CD?

Thank you

---

### Post by seawolf167 on 2011-04-01
Sorry I read that wrong - if you take a look [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"), you there are instructions for reinstalling GRUB2 on whichever device you want it on. Its pretty simple using a LiveCD.

Once you get GRUB2 restored and are able to boot to your Ubuntu partition see if the permission errors are still occuring, if so, report back with the specific error please.

---

### Post by leo123 on 2011-04-02
Seawolf, thank you for your reply.

If grub was never on the HDD with Ubuntu 10.10, can it still be installed to that HDD?

---

### Post by dcstar on 2011-04-02
> **leo123 said:**
> 
.......
Is there a way to add the bootloader to the disk with 10.10 on it **or is there a way to get around the permission issues while using the Live CD**?


```
man sudo
```

---

### Post by leo123 on 2011-04-03
What is man sudo?

---

### Post by newbuntuxx on 2011-04-03
Boot from the ubuntu live CD. 

Anything in code must be run in the terminal. The terminal can be opened by going to: Applications - Accessories - Terminal

Install testdisk:

```
sudo apt-get install testdisk
```

Now, you need to create a directory to store all of the recovered files, so use terminal like this:

```

cd ~
mkdir lostfiles
cd lostfiles

```

Now, use the file browser to mount the partitions

Then run:

```
sudo photorec
```

This will show you a list of all your mounted disk/cd similar to this:

```

Disk /dev/sdb - 160 GB / 149 GiB (RO) - ATA ST3160812AS

```

- Now, use the arrows to select the partition that you need to recover and click on proceed.
- Select Intel and hit enter
- On the next screen select file Opt
- Make sure that all the options have an X in them. You can put an X using the space bar
- Then click b to save the settings
- Then click Q to go back
- Now select search
- It will ask you for the partition type, select other
- It will then ask you the following: Do you want to save recovered files in /home/yourname/lostfiles ? [Y/N] Click Y
- and it will start the backup process
- The recovered files will be placed in different directories in /home/yourname/dvdbackup/recup_dir
- Please note that the file names will be changed, and directory structure will be lost. But the files will be recovered nonetheless (if you are lucky)
- Once the recovery process is done, you will get a similar output to this:
```
Xxx files saved in /home/yourname/lostfiles/recup_dir directory.
Recovery completed.
xx: xx recovered

```

- Select quit and hit enter. Quit again and enter
- You can now open the file browser and browse to that directory: Click on the Places menu - Home Folder, and find lostfiles, double click it and you should hopefully find something there.

---

### Post by seawolf167 on 2011-04-04
> **leo123 said:**
> What is man sudo?
dcstar is saying that the permissions error could be solved by running the command/program/etc. with super-user/root account privileges. 

```
man sudo
```

would give you the manual page for the command *sudo*

The command *sudo* is used to accomplish that without having to actually log in as root.

Example 1: run a command in a terminal

```
sudo *commandname*
```Example 2: open a GUI program

```
gksu *programname*
```You can open nautilus this way to browse to other directories

```
gksu nautilus
```

---

### Post by leo123 on 2011-04-11
Thank you to everyone for their replies.

Using the 10.10 LiveCD and running the *sudo* command, I was able to backup the remaining couple of files. It took several tries and switching to an old  Microsoft Mouse and Compaq keyboard which still froze up.

Logitech keyboard and mouse just keep freezing up with 10.04 & 10.10 no matter what has been tried to solve this issue.

Seawolf, the GRUB2 directions you pointed to specifically require LiveCD 9.10 or later to be used. Unfortunately, I had problems with 9.10, 10.04, & 10.10 when each was released and that's why I'm still using 9.04. 

Right now, I am using the 9.04 LiveCD and am relieved because it's not freezing up. :D

Anyway, 9.04 & 10.10 are on the 320GB HDD. **Is there a way to add GRUB to this HDD?** Until 11.04 comes out or I get a new system, I want to continue to use 9.04.

This is the result of *sudo fdisk -l*.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a4112

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1459    11719386   83  Linux
/dev/sda2            1460        6114    37391257    5  Extended
/dev/sda3            6115        7573    11717632   83  Linux
/dev/sda4            7573       10126    20507648   83  Linux
/dev/sda5            1460        2224     6144831   82  Linux swap / Solaris
/dev/sda6            2225        6114    31246393+  83  Linux

Not too confident about reinstalling and keeping the 9.04 install the way it is.

At this point, I'm ready to pull out the 1 yr old MBP that's been collecting dust and give that a try, but I like Linux better.

Can GRUB be installed to the 320GB HDD that has 9.04 & 10.10 on it, but no bootloader?

Thank you

---

### Post by seawolf167 on 2011-04-11
GRUB can be installed anywhere you'd like. From a LiveCD, follow [these]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") instructions to reinstall GRUB2. Then point it to one of your / partitions, reboot and run

```
sudo update-grub
```

To find your other install

---

### Post by leo123 on 2011-04-11
Seawolf, thank you.

What am I missing?

ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: /dev/sda already mounted or /mnt busy
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /mnt/boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/dev/sda
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

---

### Post by seawolf167 on 2011-04-11
> **leo123 said:**
> Seawolf, thank you.

What am I missing?

ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: /dev/sda already mounted or /mnt busy
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /mnt/boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda**1**
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

See the bold "1" above (note the space that is needed between /mnt & /dev/sda**1**); also check to ensure you are specifying the correct device - easiest way is to mount like you did above, then do a quick browse of the mounted partition, it should be your / partition

---

### Post by leo123 on 2011-04-11
Seawolf, thank you. Before I saw your post, I realized the space was missing. Not sure, but I think I used "sda."

After rebooting, I went into the BIOS to see if I could change the boot order of the disks, but wasn't able to.

On second reboot, I got the "Primary Slave Hard Disk Error" message and I selected "Press F1 to Resume" and GUESS WHAT? IT WORKED :) Well sort of. The boot menu was there and I was able to select 9.04 and for a couple of seconds, an error message displayed a few lines of 1.968321 atal ..., but the log in screen did come up. Once I logged in, I did run *sudo update-grub*.

I think I need to unhook the drive that failed which is the IDE Primary Slave. The 320GB HDD is SATA1.

That's a project for another day, hopefully soon. I'll have to research it.

For now, this system is staying up and running!!! 

Seawolf, thank you for your patience, assistance, and getting me over this hump!!!

---

### Post by seawolf167 on 2011-04-11
Glad it worked!

Couple things you may want to do:

[LIST=1]
[*]Backup with [Clonezilla]("http://www.clonezilla.org") :P
[*]Check the SMART status of the fail[ed][ing] drive with *[smartmontools]("http://sourceforge.net/apps/trac/smartmontools/wiki")*
[*]Check that your 10.10 install is/will showing up in the GRUB2 boot menu using the below steps
[/LIST]
Open a terminal, type

```
gedit /boot/grub/grub.cfg
```

Do not edit this file! Scroll down and look for a menu entry for your other Ubuntu install. That way you can tell if you'll have the option of booting into 10.10 on restart, if it isn't there, you'll have to do some GRUB2 tweaking to get it setup

---

### Post by leo123 on 2011-04-11
Seawolf,

Thank you. I will definitely look at Clonezilla & smartmontools.

The grub.cfg file doesn't exist. Kubuntu 8.10 was the only other option on the boot menu, which I haven't used in a while. Even though 10.10 doesn't show up on the boot menu, I can access the files. The mouse and keyboard would always freeze up and none of the "solutions" I tried would correct that issue, so I've just stuck with what works for me.

Maybe my system is too old because, 9.10, 10.04, & 10.10 had issues that I wasn't able to solve after much research and trying different solutions.

Hopefully, I'll have better luck with 11.04 on this system.

I can't thank you enough, because I was really at a loss of what to do next to get back up and running.

---

### Post by seawolf167 on 2011-04-11
Not a problem - glad you got it working again!

---

