---
title: "Problem with ubuntu 11.04"
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
ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys ubuntu@ubuntu$ sudo chroot /mnt root@ubuntu$ su - fezHowever when I try the "su - fez" I get 
-su: cannot create temp file for here-document: no space left on the device

I've done a few sudo apt-get xxx (can't remember the names) since this problem on this HDD and they download fine, so there must be space available. 

I've tried plugging the HDD into a second HDD, using the second one as a master and trying to access /home but there is nothing in it. I' totally out of idea's, anyone ever heard of this problem before? :|

---

