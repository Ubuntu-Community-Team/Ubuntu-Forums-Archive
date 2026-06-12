---
title: "Very very slow startup"
date: 2009-09-21
forum: General Help
---

### Post by raptista on 2009-09-21
Hello everybody,
i've installed ubuntu months ago, everything was super ..
but, at these later days,the startup become too slow..i don't know why ! i though it was from the virtualbox wich the last thing installed,i thoug too it was from the disk check every startup..i i still thinking of other thing...
anyway, disk how looks my HD:

[php]
abdo@abdo-laptop:~$ sudo fdisk -l
[sudo] password for abdo: 

Disque /dev/sda: 120.0 Go, 120034123776 octets
240 têtes, 63 secteurs/piste, 15505 cylindres
Unités = cylindres de 15120 * 512 = 7741440 octets
Identifiant de disque : 0x17261725

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1        6772    51196288+   7  HPFS/NTFS
/dev/sda2            6773       15506    66019117+   5  Etendue
/dev/sda5            6773        9356    19526976    b  W95 FAT32
/dev/sda6            9356        9614     1951866   82  Linux swap / Solaris
/dev/sda7            9614       15506    44540181   83  Linux
abdo@abdo-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=95fe18fa-0edc-4cb1-9e76-688cab16aea9 /               ext3    relatime,errors=remount-ro 0       0
# swap was on /dev/sda6 during installation
UUID=fc15e5bd-0139-4d51-8b6c-5c1bd02f85fd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
abdo@abdo-laptop:~$ df -h
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sda7              42G   11G   30G  27% /
tmpfs                 498M     0  498M   0% /lib/init/rw
varrun                498M  228K  498M   1% /var/run
varlock               498M     0  498M   0% /var/lock
udev                  498M  148K  498M   1% /dev
tmpfs                 498M  732K  497M   1% /dev/shm
lrm                   498M  2,2M  496M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda5              19G  1,2G   18G   7% /media/disk
/dev/sda1              49G   12G   38G  24% /media/disk-1

[/php]please i need help :( !

thanks !

---

### Post by scragar on 2009-09-21
You could try booting with nosplash options on for your kernel, that might show you where things are running slow, or maybe install bootchart.

To do the first one just reboot and in the grub menu(press escape if it's hidden by default) press **e** on ubuntu, then **e** again on the line that starts with the word `kernel`, add ```
nosplash
```to the very end and then press enter and **b** to boot it.
To do the latter```
sudo apt-get install bootchart
```After rebooting look for the logs and such in /var/log/bootchart

---

### Post by NoaHall on 2009-09-21
Easiest way is to do "sudo modprobe -r vboxnetadp"
sudo modprobe -r vboxnetflt
sudo modprobe -r vboxdrv 

Then when you want to run VB, do 

sudo modprobe vboxdrv
sudo modprobe vboxnetadp
sudo modprobe vboxnetflt


BTW, that's not php code.

---

### Post by raptista on 2009-09-21
[scragar:]("http://ubuntuforums.org/member.php?u=319899")
i did what u said (1st methode), it's "pauses" at the step "Configuring network interfaces".
how can i prevent it of doing that, or at least let it configure only my ADSL modem ?

NoaHall:
this is the result of all the commands u posted:
```

root@abdo-laptop:/home/abdo# sudo modprobe -r vboxnetflt
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.


```

>  BTW, that's not php code. 	
fine..i know..just harry a little bit !

---

### Post by NoaHall on 2009-09-21
Right, in that case, do "mv /etc/modprobe.d/options /etc/modprobe.d/options.conf" and try again.

---

### Post by raptista on 2009-09-21
```

root@abdo-laptop:/home/abdo# mv /etc/modprobe.d/options /etc/modprobe.d/options.conf
root@abdo-laptop:/home/abdo# sudo modprobe -r vboxnetadp
FATAL: Module vboxnetadp not found.
root@abdo-laptop:/home/abdo# sudo modprobe -r vboxnetflt
root@abdo-laptop:/home/abdo# sudo modprobe -r vboxdrv 
root@abdo-laptop:/home/abdo# sudo modprobe vboxnetadp
FATAL: Module vboxnetadp not found.
root@abdo-laptop:/home/abdo# sudo modprobe vboxnetflt
root@abdo-laptop:/home/abdo# 


```

what does really those commands do plz ?

---

### Post by NoaHall on 2009-09-21
They turn off the vobx modules - which tend to take up quite a bit of bandwidth, and slow down your computer. The second command turns them back on.

---

### Post by raptista on 2009-09-21
Problem solved finally :P

===
Ok. here is the resume: As i think, installing Vbox on my laptop added many lines in my interfaces file:*** "/etc/network/interfaces"***
this is the file before:
```


root@abdo-laptop:/home/abdo# nano /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off


```so i commented all the last lines,
it becomes:
```


root@abdo-laptop:/home/abdo# nano /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

#auto br0
#iface br0 inet dhcp
#bridge_ports eth0
#bridge_fd 9
#bridge_hello 2
#bridge_maxage 12
#bridge_stp off


```i rebooted and baaaam :P
all thanks to NoaHall & scragar .. thanks guys ! that was really helpful :guitar:

---

