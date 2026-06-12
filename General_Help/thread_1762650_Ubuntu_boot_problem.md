---
title: "Ubuntu boot problem"
date: 2011-05-19
forum: General Help
---

### Post by Xiah on 2011-05-19
Afternoon ladies and gents, slight major problem I have.

When I tried to log in a few days ago i got the below error
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69072&stc=1&d=1210141131[/IMG]

After searching around i've got myself a LiveCD to try and fix it because I have files in my /home directory that I can't lose
I've found that it's a memory problem. I've tried "df" in consol and i got the below
filesystem           1k blocks        used          available     use%    mounted on
aufs                    1547816         50808         1497008    4%        /
none                   1539768         236            1539532    1%         /dev
/dev/sr0              228774          228774        0              100%     /cdrom
/dev/loop0           208000          208000        0              100%     /rofs
none                   1547816         0                1547816    0%        /dev/shm
tmpfs                  1547816         0                1547816    0%        /tmp
none                   1547816         60              1547756    1%        /var/run
none                   1547816         0                1547816    0%        /var/lock

I also tried
ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt ubuntu@ubuntu$ sudo mount -o  bind /dev /mnt/dev ubuntu@ubuntu$ sudo mount -o bind /dev/shm  /mnt/dev/shm ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc  ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys ubuntu@ubuntu$ sudo  chroot /mnt root@ubuntu$ su - fezHowever when I try the "su - fez" I get  
-su: cannot create temp file for here-document: no space left on the device

I've done a few sudo apt-get xxx (can't remember the names) since this  problem on this HDD and they download fine, so there must be space  available. 

I've tried plugging the HDD into a second HDD, using the second one as a  master and trying to access /home but there is nothing in it. I'  totally out of idea's, anyone ever heard of this problem before? :neutral:

---

### Post by Rubi1200 on 2011-05-20
Hi,
there could be a couple of possibilities for the error message, so let's start with one thing at a time.

1. boot an Ubuntu LiveCD/USB and choose the option to run memtest. Let it run for a few hours and see if it reports anything

2. a more likely problem could be that the root file-system is full and you need to do some housecleaning to fix this (also from a LiveCD). (By the way, the df command you gave the output for is for the file-system on the LiveCD and not your actual install).
```
sudo mkdir /mnt/temp 
sudo mount /dev/sd**[COLOR=Red]XY[/COLOR]** /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```Replace XY with the actual Ubuntu partition e.g. sda1

Once the last command completes you will be at a root prompt and have full control of your file-system. Please be careful what you type!

Then, run these commands (no sudo required since you have a root promp)t:
```
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install -f
dpkg --configure -a
```At this point, I would exit and reboot to see if this was enough to fix the problem:
```
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```Reboot, taking out the LiveCD, and hopefully the problem is fixed.

If not, post back with an update and we can try some other things.

---

