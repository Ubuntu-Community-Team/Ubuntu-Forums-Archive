---
title: "fstab iscsi and auto mount"
date: 2012-08-16
forum: General Help
---

### Post by Nikolai D. on 2012-08-16
Hello everyone on the forum of my fav. OS :D
I have installed FOG server on Ubuntu 10.04 LTS some time ago and connected it to the iscsi storage.
Now every time i reboot the server first i get this message "Disk drive for /images is not ready yet or not present". And the second thing is i always have to do "mount /dev/sdb1 /mnt/iscsi" and "mount -a" after a reboot to get FOG working.
I have followed QNAP [http://web.qnap.com/pro_application.asp?ap_id=135](http://web.qnap.com/pro_application.asp?ap_id=135) and FOG [http://www.fogproject.org/wiki/index.php/Adding_Storage_to_a_FOG_Server](http://www.fogproject.org/wiki/index.php/Adding_Storage_to_a_FOG_Server) explanation to get FOG working.
But is would really like to solve those two little things so it just works. :)
I have already found out that u can put some line in /etc/fstab to auto mount things. But since every character u put in there can make it work or dont work. And i dont yet know exactly what every character means i still need some assistance. :) But i am learning and willing to learn more. Since i figured how to install FOG anyway already. :) So if you wish to give me some link where i can find useful info to figure out those issues. That would be also cool. :)
Also here is my fstab if u would like to see it:
root@V-FOGUNTU:~# vim /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1629e183-fd39-4909-98ff-e2326895885e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=94c397a8-791b-43ad-87ca-5405df0e91d8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Fogimages share on v-deneb
//192.168.1.7/FogImages        /media/fogimages cifs   credentials=/etc/fogpw,defaults 0       0
#now this is self added by NDO to add storage to Images as described on FOG wiki
UUID=9633bc60-3d02-4c56-ae73-2c032482f03d       /images         ext3 defaults 0 0
~
~
                                                                                   1,1           All

p.s. Maybe its time to keep me busy with LPIC once in a while. ;)

Thanks in advance,
Any advice is appreciated,
Nikolai

---

### Post by Nikolai D. on 2012-08-20
Hi there again :)

I have been googling around today. And found here
[https://groups.google.com/forum/?fromgroups#!topic/open-iscsi/5X0d195dSKQ](https://groups.google.com/forum/?fromgroups#!topic/open-iscsi/5X0d195dSKQ)[1-25]
interesting explanation about iscsi and auto-mounting with fstab.
Figuring/thinking/googling it further in a meanwhile.
Was wondering what the parameters in this command were?
iscsiadm -m node -T iqn.com.domain:target -p 10.0.0.1 -o update -n
node.conn[0].startup -v automatic

thx,
Nikolai

---

### Post by Nikolai D. on 2012-08-21
Hi there guys and girls,
using right target name that i have in the command above (iscsiadm -m node -T iqn.com.domain:target -p 10.0.0.1 -o update -n
node.conn[0].startup -v automatic) and/or adding '_netdev' parameter in fstab solved it for me.
tyvm :)

---

