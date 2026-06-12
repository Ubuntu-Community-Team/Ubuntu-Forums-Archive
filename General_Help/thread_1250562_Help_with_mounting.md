---
title: "Help with mounting"
date: 2009-08-26
forum: General Help
---

### Post by emaxxx29 on 2009-08-26
I am so frustrated!
For some reason I cannot mount/access my harddrive at all. When I plug in my mp3 player to the computer it doesnt mount! 

it says this in both cases:
"You are not privileged to mount *DeviceName* "

PLEASE PLEASE PLEASE HELP ME BECAUSE I AM SO FRUSTRATED!

---

### Post by P4man on 2009-08-26
.. and does your user account have the permissions to mount devices?
Go to system > administration > users and groups

unlock it

check if in privilidges "access external storages" is enabled.

---

### Post by emaxxx29 on 2009-08-26
> **P4man said:**
> .. and does your user account have the permissions to mount devices?
Go to system > administration > users and groups

unlock it

check if in privilidges "access external storages" is enabled.

i actually just read a tutorial online that said to do exactly that, unfortunately it didnt help.

---

### Post by NoaHall on 2009-08-26
Try using "sudo mount" in the terminal. Or launch "sudo nautilus" and then mount from the GUI

---

### Post by P4man on 2009-08-26
> **NoaHall said:**
>  Or launch "sudo nautilus" 

NONONONO. Dont run nautilus with sudo! If  you need nautilus (or any graphical program) with root permissions use

[SIZE="7"]**gk**sudo[/SIZE]

!

For many apps sudo will not give problems, but its a bad habbit. nautilus is probably THE app you have to use gksudo or you will render your machine unbootable sooner or later messing up permissions.

---

### Post by emaxxx29 on 2009-08-26
could you guys please give me more details? im kind of new to this...

---

### Post by P4man on 2009-08-26
open a terminal: applications > accessories > terminal
type: 

```
sudo mount
```
(enter password if asked, and enter)

copy paste the output here so we can have a look.

---

### Post by NoaHall on 2009-08-26
Well it's never given me any problems.

Open the Terminal 
type "gksudo nautilus" and then try mounting from there

---

### Post by emaxxx29 on 2009-08-26
> **P4man said:**
> open a terminal: applications > accessories > terminal
type: 

```
sudo mount
```
(enter password if asked, and enter)

copy paste the output here so we can have a look.

eitan@eitan-laptop:~$ sudo mount
[sudo] password for eitan: 
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
eitan@eitan-laptop:~$

---

### Post by NoaHall on 2009-08-26
Just to confirm, /dev/sda5 is your main drive?

---

### Post by emaxxx29 on 2009-08-26
> **NoaHall said:**
> Just to confirm, /dev/sda5 is your main drive?

that's the thing - i have no idea.

---

### Post by NoaHall on 2009-08-26
Okay then. I'm guessing it is. Now do
"sudo mount /dev/sda5" and post what you get.

---

### Post by emaxxx29 on 2009-08-26
> **NoaHall said:**
> Okay then. I'm guessing it is. Now do
"sudo mount /dev/sda5" and post what you get.

eitan@eitan-laptop:~$ sudo mount /dev/sda5
mount: /dev/sda5 already mounted or / busy
mount: according to mtab, /dev/sda5 is already mounted on /

---

### Post by NoaHall on 2009-08-26
So yeah, it's your main. Hm, it's not detecting other drives. Now do "cat /etc/fstab" and post, and then "cat /etc/mtab" and post what you get.

---

### Post by emaxxx29 on 2009-08-26
> **NoaHall said:**
> So yeah, it's your main. Hm, it's not detecting other drives. Now do "cat /etc/fstab" and post, and then "cat /etc/mtab" and post what you get.


eitan@eitan-laptop:~$ cat /etc/fstab

proc /proc proc defaults 0 0
UUID=d6b7aa7b-ed22-4a7b-8bfd-a30bda7fb638 / ext3 relatime,errors=remount-ro 0 1
UUID=4ff35d76-20df-44fa-9eb7-0a83bcb21c3c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/WINDOWS\040PARTITION ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sda2 /media/New\040Volume ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sda3 /media/HP_RECOVERY ntfs-3g defaults,locale=en_CA.UTF-8 0 0
eitan@eitan-laptop:~$ cat /etc/mtab
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
eitan@eitan-laptop:~$ 



ps. my mp3 is not inserted.

---

### Post by NoaHall on 2009-08-26
Okay, what do you want to mount? 

To mount Windows do "sudo mount /dev/sda1"
To mount New do "sudo mount /dev/sda2"

To find your mp3, do the same, and then find the mp3 in fstab and then sudo mount, and see what you get.

---

### Post by emaxxx29 on 2009-08-26
> **NoaHall said:**
> Okay, what do you want to mount? 

To mount Windows do "sudo mount /dev/sda1"
To mount New do "sudo mount /dev/sda2"

To find your mp3, do the same, and then find the mp3 in fstab and then sudo mount, and see what you get.

i did the first 2 u told me and got this:
eitan@eitan-laptop:~$ sudo mount /dev/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
eitan@eitan-laptop:~$ sudo mount /dev/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/New Volume -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/New Volume ntfs-3g force 0 0
eitan@eitan-laptop:~$ 


All i want is for everything to be automatically mounted without all the headache

---

### Post by NoaHall on 2009-08-26
It sounds like what ever you have on the New partion didn't close down properly - so it can't be accessed. Try shutting it down properly and try again.

---

### Post by emaxxx29 on 2009-08-26
> **NoaHall said:**
> It sounds like what ever you have on the New partion didn't close down properly - so it can't be accessed. Try shutting it down properly and try again.

how do i shut it down though?

---

### Post by NoaHall on 2009-08-26
Depends what you've got on it. If it's one you use in Windows or another OS, boot into the other OS and preform a shut down without forcing it ( ie, don't force a unexpected reboot by pressing the external button on the case) After mounting it in that OS, I mean.

---

### Post by emaxxx29 on 2009-08-26
> **NoaHall said:**
> Depends what you've got on it. If it's one you use in Windows or another OS, boot into the other OS and preform a shut down without forcing it ( ie, don't force a unexpected reboot by pressing the external button on the case) After mounting it in that OS, I mean.

sure ill try that and ill write back.
Thanks a lot so far :)

---

### Post by NoaHall on 2009-08-26
> **emaxxx29 said:**
> sure ill try that and ill write back.
Thanks a lot so far :)

No problem ;) If all else fails, try using "sudo apt-get install ntfsprogs" which will give you extra tools to work with ntfs disks.

---

