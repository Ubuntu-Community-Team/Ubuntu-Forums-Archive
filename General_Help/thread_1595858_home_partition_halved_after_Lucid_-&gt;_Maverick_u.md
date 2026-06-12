---
title: "/home partition halved after Lucid -&gt; Maverick upgrade."
date: 2010-10-13
forum: General Help
---

### Post by Lisiano on 2010-10-13
Ubuntu is great! I love it! Only issue i had with it was nVidia HDMI playback but that wasnt hard to solve. Ive been using ubuntu since Karmic and except for the HDMI i had no problems.
On the 10.10.10 i upgraded to Maverick from the terminal with "do-release-upgrade". I noticed that command while i was at a friends house SSH'ing back home. When i came back i ran the command and took me a few hours to upgrade.
And to my suprise i encountered 3 problems (Karmic -> Lucid = Zero)...
1) I cant use a few PPA's at the moment but its livable with.
2) Compiz broken but i can wait. Maybe might compile it myself if i get tired of Metacity.
3) My /home partition got halved.
The first 2... Just inconvenience.
The 3rd... I got 900GB's allocated to my /home so im missing quite a lot of space. I do remember the system reporting before that i had 900GB's but now it just says 485GB's.
Heres what fdisk and df report
```
lisiano@Lisiano-Ubuntu:~$ sudo fdisk -l /dev/sda
[sudo] password for lisiano: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x146d213d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         783     6289416   82  Linux swap / Solaris
/dev/sda2             784      110202   878906250   83  Linux
/dev/sda3          110202      121602    91566081    5  Extended
/dev/sda5          110202      121602    91566080   83  Linux
lisiano@Lisiano-Ubuntu:~$ 
```
```
lisiano@Lisiano-Ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             90128544  14177916  71372324  17% /
none                   3020940       328   3020612   1% /dev
none                   3063916      3076   3060840   1% /dev/shm
none                   3063916       236   3063680   1% /var/run
none                   3063916         0   3063916   0% /var/lock
/dev/sda2            507294432 472583432  29557348  95% /home
/dev/sdd3               970524         4    970520   1% /media/Transfer
/dev/mapper/udisks-luks-uuid-466c07e5-d61b-4332-bcbd-2a6c5247eb50-uid1000
                       5852784         4   5852780   1% /media/Encrypted
lisiano@Lisiano-Ubuntu:~$ 
```
I tried googling the solution but sadly i couldnt find it. Hope i posted this in the right section.
Also i haven't tried booting with a live usb/cd as im encoding a short film for school and i noticed it just yesterday.
Also does anyone know why SSH still reports this?
```
lisiano@Lisiano-Ubuntu:~$ ssh localhost
lisiano@localhost's password: 
Linux Lisiano-Ubuntu 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

*** System restart required ***
Last login: Wed Oct 13 23:09:40 2010 from lisiano-ubuntu
lisiano@Lisiano-Ubuntu:~$ 
``` And yes. I did reboot. The Restart Required icon is not lit either.

---

### Post by Lisiano on 2010-10-15
Odd... I resolved this by resizing the disk to be 1 MB less... It spit an error and said the right size finally...

---

