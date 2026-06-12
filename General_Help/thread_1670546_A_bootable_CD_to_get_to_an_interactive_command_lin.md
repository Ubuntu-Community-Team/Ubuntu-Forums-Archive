---
title: "A bootable CD to get to an interactive command line?"
date: 2011-01-19
forum: General Help
---

### Post by mahela007 on 2011-01-19
As I have posted here ([http://ubuntuforums.org/showthread.php?t=1661110](http://ubuntuforums.org/showthread.php?t=1661110)), my laptop powered down during an update because I forgot to plug it into the mains power. Anyway, after going through the thread I referred to above, I learned that I must chroot into the existing installation and patch it up. I can do this using a live CD but unfortunately, I gave my most recent live CDs away and the Live CDs I have left don't recognize the file system on the current Ubuntu installation. (If I remember correctly, the current [broken] installation is 10.04).
Downloading a new live CD is a bit difficult as internet speeds over here aren't very fast. I was wondering if there is another alternative bootable CD that I could use to get a interactive command line which I can use to "chroot".
Thanks

---

### Post by amsterdamharu on 2011-01-19
You might give tinycore linux a go. That's only 10MB but after you boot it you have to install bash.

And because it runs out of memory you have to install it every time you reboot. I advice installing seamonkey as well so you can go to the Internet and look up stuff without rebooting. (just leave tinycore active)

Then open up a terminal and post the output of the following command:

```
sudo fdisk -l
```Then we can check to see what to mount and where to chroot to, by the way chroot is change root. Not change root user but change root directory so after that command you'll be using the files from your Ubuntu install instead of tinycore.

There might be some problem because tinycore uses different environment variables but we'll cross that bridge when we get there.

---

### Post by mahela007 on 2011-01-19
thanks for the quick reply. I'll post back in a few hours after I get familiar with Tiny core...

---

### Post by amsterdamharu on 2011-01-19
To find out for sure where your ubuntu is installed enter the following commands in a terminal (black computer screen icon)
```
sudo mount /dev/sda7 /mnt
cat /etc/fstab
```After we found out for sure where your Ubuntu is installed we can do the following
If you got tinycore working you can click on the desktop choose "system tools" -> "appbrowser" click connect then next to search type bash and press enter, click in the found items on bash.tcz and click go
Repeat with seamonkey and install seamonkey (this might take a while)
Now you can start up seamonkey (new icon will appear in the icon bar below) and go to this page.
If anything goes wrong just post whatever was wrong here.
Click on the black sceen icon (terminal) and type the following commands:
```
sudo bash
sudo mount /mnt /dev/sda7
cp /etc/resolv.conf /mnt/etc/
mount --bind /dev/ /mnt/dev
chroot /mnt
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C
dbus-uuidgen > /var/lib/dbus/machine-id
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
# (left out apt-get clean because it'll delete all the already downloaded packages and your internet is slow)
apt-get update
apt-get upgrade
dpkg --configure -a
exit
umount /mnt/dev/pts
umount /mnt/sys
umount /mnt/proc
umount /mnt/dev
umount /mnt
exit
```

---

### Post by mahela007 on 2011-01-20
> **amsterdamharu said:**
> You might give tinycore linux a go. That's only 10MB but after you boot it you have to install bash.

And because it runs out of memory you have to install it every time you reboot. I advice installing seamonkey as well so you can go to the Internet and look up stuff without rebooting. (just leave tinycore active)

Then open up a terminal and post the output of the following command:

```
sudo fdisk -l
```Then we can check to see what to mount and where to chroot to, by the way chroot is change root. Not change root user but change root directory so after that command you'll be using the files from your Ubuntu install instead of tinycore.

There might be some problem because tinycore uses different environment variables but we'll cross that bridge when we get there.
 I got TinyCore running. 
```
 sudo fdisk -l
``` shows that linux is on /dev/sda6 and the swap is on /dev/sda7

EDIT: 
Why do I have to install bash? (It's just another ternimal client right? Can't I use the terminal already in Tiny core? I have no problem installing it but I would like to know the reason for doing so. ;-). Also, I would really appreciate it if you could explain what the commands in post #4 do..

---

### Post by amsterdamharu on 2011-01-20
It might work without bash, you can try to run the commands without installing anything really.

If you found your system on sda6 then replace sda7 with sda6.

---

### Post by mahela007 on 2011-01-20
how is bash different from what's already on Tinycore?

---

### Post by mahela007 on 2011-01-20
duplicate

---

### Post by mahela007 on 2011-01-20
after command #3, I get a warning that a file is about to be overwritten. Should I select "yes"?

---

### Post by amsterdamharu on 2011-01-20
Yes, you can overwrite resolf.conf

---

### Post by mahela007 on 2011-01-21
ok.. I selected overwrite and proceeded with all your commands. They worked without any problems and apparently the updates were downloaded and applied properly. However, now Ubuntu won't boot.. ;-)
The message shown after the computer fails to boot is as follows.
```
WARNING bootdevice may be renamed. Try root=/deve/sda6
Gave up waiting for root device. COmmon problems:
-root ards (cat /proc/dmcline)
   - Check rootdelay
    -Chech root
  MIssing modules (cat /proc/modules: ls /dev)
ALTERT! /dev/hda6 does not exist. Dropping to a shell.!

``` ( I typed that out manually. There may be typos)
According to bash on tiny core linux, my Ubuntu installation is on hda6.. not sda6. (note the h and not s).

EDIT: Running sudo fdisk -l on an old Ubuntu live CD (8.10) shows that linux is on /dev/sda6 whereas the same command on tiny core says linux is on /dev/hda6...

---

### Post by amsterdamharu on 2011-01-21
If you boot up you'd see a menu where you can choose Ubuntu and Ubuntu restore. If not press the down arrow key when you start up.

Select the top one (usually Ubuntu with the highest kernel) now press e to edit it and check where it says: root=/dev/sda6

It might have changed to root=/dev/hda6 but you can edit it to /dev/sda6 and boot or try /dev/sda7 if you might think it's there.

---

### Post by mahela007 on 2011-01-21
Yup.. some success at last. It said 'root=/dev/hda6' in two places and I changed both. Ubuntu started up and input worked! However, the changes made to that boot entry don't seem to be permanent. I tried looking in /etc/default/grub. It doesn't seem to list what I need.

---

### Post by amsterdamharu on 2011-01-21
When you started Ubuntu run the following command:
```
sudo update-grub
```

That would take care of things I guess.

---

### Post by mahela007 on 2011-01-21
Well, I didn't get the change to do that. After playing around (but not editing) the grub conf file, it starts up properly now. The file reads 'root = hd0,6'. Thanks for all your help. I love to have my Ubuntu back !! 
PS: Any idea why tiny core said Ubuntu was on hda6?

---

### Post by amsterdamharu on 2011-01-21
Not sure why it's using hda, for scsi and sata sda should be used but maybe the init scripts in tinycore handle it differently or there is some stuff missing so it won't pick it up.

---

### Post by mahela007 on 2011-01-21
ah.. well.. thanks again for all your help. Marking thread as solved.

---

