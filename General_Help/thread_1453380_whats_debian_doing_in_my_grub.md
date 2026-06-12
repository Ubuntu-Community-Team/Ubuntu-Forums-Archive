---
title: "whats debian doing in my grub?"
date: 2010-04-13
forum: General Help
---

### Post by kiwimenace on 2010-04-13
I'm no linux pro, I have dual boot ubuntu/xp, mostly my girlfriend uses the xp i use the ubuntu sometimes, so I'm pretty feeble when its come to ubuntu.

Anyway the problem(assuming its a problem) until now in my grub i have had 2 or 3 ubuntu kernels and my xp, but now at the bottom under my xp I now have two debian choices, this is all in my grub that I'm talking about. This seems strange to me, I've worked with several ubuntu/xp/vista dual boot systems over the last year and never had this happen before, it seems strange and illogical to me.

If somebody could shed some light on this I would be very happy.
thanks in advance

---

### Post by Monotoko on 2010-04-13
Hmmm, that shouldnt be right, have you tried booting them?

If they do nothing you can probably just remove them.

---

### Post by kiwimenace on 2010-04-13
Yes seems totally abnormal to me, today though i did have a couple of strange things happen.  1 i got the warning about "couldn't grab mouse malicious third party maybe eves droping(or something like that)....... and also when i booted into ubuntu i had a couple of folders open a couple of time........

And when you do try to boot them, "error must load kernel first*"

---

### Post by Monotoko on 2010-04-13
Hmmm, that third party eves dropping message is a bit worrying..

Take a look at:

System -> Log File Viewer -> auth.log
and see if there is anything in there you dont recognise.

If you need to paste it here and i will have a look :)

---

### Post by kiwimenace on 2010-04-15
Apr 13 08:17:01 xxxxxx-box CRON[2376]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 08:17:01 xxxxxx-box CRON[2376]: pam_unix(cron:session): session closed for user root
Apr 13 09:17:01 xxxxxx-box CRON[2384]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 09:17:01 xxxxxx-box CRON[2384]: pam_unix(cron:session): session closed for user root
Apr 13 10:17:01 xxxxxx-box CRON[2390]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 10:17:01 xxxxxx-box CRON[2390]: pam_unix(cron:session): session closed for user root
Apr 13 11:17:01 xxxxxx-box CRON[2396]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 11:17:01 xxxxxx-box CRON[2396]: pam_unix(cron:session): session closed for user root
Apr 13 11:56:34 xxxxxx-box sudo:   xxxxxx : TTY=unknown ; PWD=/home/xxxxxx ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817448 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpSzMpNn
Apr 13 11:58:20 xxxxxx-box sudo:   xxxxxx : TTY=unknown ; PWD=/home/xxxxxx ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817448 --update-at-startup
Apr 13 12:08:19 xxxxxx-box gdm-session-worker[1562]: pam_unix(gdm:session): session opened for user xxxxxx by (uid=0)
Apr 13 12:08:19 xxxxxx-box gdm-session-worker[1562]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 13 12:08:21 xxxxxx-box seahorse-daemon[1674]: init gpgme version 1.1.8
Apr 13 12:17:01 xxxxxx-box CRON[2164]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 12:17:01 xxxxxx-box CRON[2164]: pam_unix(cron:session): session closed for user root
Apr 13 22:56:36 xxxxxx-box gdm-session-worker[1695]: pam_unix(gdm:session): session opened for user xxxxxx by (uid=0)
Apr 13 22:56:36 xxxxxx-box gdm-session-worker[1695]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 13 22:56:38 xxxxxx-box seahorse-daemon[1806]: init gpgme version 1.1.8
Apr 13 23:00:16 xxxxxx-box sudo: pam_unix(sudo:auth): conversation failed
Apr 13 23:00:16 xxxxxx-box sudo: pam_unix(sudo:auth): auth could not identify password for [xxxxxx]
Apr 13 23:00:16 xxxxxx-box sudo: pam_unix(sudo:auth): conversation failed
Apr 13 23:00:16 xxxxxx-box sudo: pam_unix(sudo:auth): auth could not identify password for [xxxxxx]
Apr 13 23:00:16 xxxxxx-box sudo: pam_unix(sudo:auth): conversation failed
Apr 13 23:00:16 xxxxxx-box sudo: pam_unix(sudo:auth): auth could not identify password for [xxxxxx]
Apr 13 23:00:16 xxxxxx-box sudo:   xxxxxx : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/xxxxxx ; USER=root ; COMMAND=/usr/bin/gdebi-gtk --non-interactive /home/xxxxxx/Downloads/skype-ubuntu-intrepid_2.1.0.81-1_i386.deb
Apr 13 23:17:01 xxxxxx-box CRON[2157]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 23:17:01 xxxxxx-box CRON[2157]: pam_unix(cron:session): session closed for user root
Apr 14 03:44:06 xxxxxx-box smbd[1659]: pam_unix(samba:session): session opened for user xxxxxx by (uid=0)
Apr 14 03:44:22 xxxxxx-box smbd[1659]: pam_unix(samba:session): session closed for user xxxxxx
Apr 15 14:41:18 xxxxxx-box sudo:     root : TTY=unknown ; PWD=/ ; USER=xxxxxx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Apr 15 14:41:18 xxxxxx-box sudo:     root : TTY=unknown ; PWD=/ ; USER=xxxxxx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Apr 15 14:41:18 xxxxxx-box sudo:     root : TTY=unknown ; PWD=/ ; USER=xxxxxx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Apr 15 14:58:25 xxxxxx-box gdm-session-worker[1688]: pam_unix(gdm:session): session opened for user xxxxxx by (uid=0)
Apr 15 14:58:25 xxxxxx-box gdm-session-worker[1688]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 15 14:58:26 xxxxxx-box seahorse-daemon[1996]: init gpgme version 1.1.8
Apr 15 15:17:01 xxxxxx-box CRON[2192]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 15 15:17:01 xxxxxx-box CRON[2192]: pam_unix(cron:session): session closed for user root
Apr 15 16:17:01 xxxxxx-box CRON[2233]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 15 16:17:01 xxxxxx-box CRON[2233]: pam_unix(cron:session): session closed for user root


P.S. I've noticed in forums that there is a standard way to post copied system info/commands like this, using a specific font etc, if somebody could point me in the right direction for that too would be cool.....



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dee7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7070    56789743+   7  HPFS/NTFS
/dev/sda2            7071        9729    21358417+   f  W95 Ext'd (LBA)
/dev/sda5            7071        9613    20426616   83  Linux
/dev/sda6            9614        9729      931738+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9ec72c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7585b15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1150d2b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07249335

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       28086   225600763+   c  W95 FAT32 (LBA)
/dev/sde2           28087       30401    18595237+  83  Linux

---

### Post by uRock on 2010-04-15
Running ```
w
``` will show everyone signed in at the moment. What ports do you have open? Maybe there is someone connecting from inside your wireless network. If you know your IP add it in place of the x ```
nmap x.x.x.x
``` If your Router's address 192.168.1.1 then run ```
nmap 192.168.1.0/24
``` This command will show ever interface on the network.
If you have ports open but you aren't sharing files, then enable the ubuntu firewall with ```
sudo ufw enable
``` If you need to open in ports in particular you can install GUFW whcih will appear in your System> Administration menu and you can add rules to open ports.

---

### Post by uRock on 2010-04-15
Here is what "w" will show when everything is fine.```
rabbit@rabbit-desktop:~$ w
 21:39:17 up  8:57,  2 users,  load average: 0.71, 0.46, 0.39
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rabbit   tty7     :0               12:42    8:57m 11:43   0.73s gnome-session
rabbit   pts/0    :0.0             21:39    0.00s  0.22s  0.01s w
rabbit@rabbit-desktop:~$ 

```Here is what it will show when something may be wrong.
```
rabbit@rabbit-desktop:~$ w
 21:49:57 up  9:08,  3 users,  load average: 0.22, 0.32, 0.34
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rabbit   tty7     :0               12:42    9:07m 12:02   0.73s gnome-session
rabbit   pts/0    :0.0             21:39    0.00s  0.22s  0.01s w
[COLOR="Red"]rabbit   pts/1    broken-windows.l 21:49    4.00s  0.21s  0.21s -bash[/COLOR]
rabbit@rabbit-desktop:~$ 
``` The red type is another system accessing via ssh.

---

### Post by kiwimenace on 2010-04-15
I understand bits and pieces of what you've posted, some commands will be useful later.....

But still whats the debian doing in my grub?

---

### Post by uRock on 2010-04-15
> **kiwimenace said:**
> I understand bits and pieces of what you've posted, some commands will be useful later.....

But still whats the debian doing in my grub?

I am thinking someone is hijacking your system and adding stuff. That is why I was saying to check your ports and secure your system.
"w" will show if someone else is signed into your system. If you have Remote Desktop enabled (find this in the System> Preferences menu), then someone may be connecting and installing whatever malware they want and that is most likely where the debian entries are coming from. 

Have you tried to boot the Debian entries though I doubt they are safe. 

I am hoping you have at least turned on UFW, by now.

---

### Post by uRock on 2010-04-15
Can you run ```
sudo fdisk -l
``` and paste the results so e can see if partitions have been edited?

---

### Post by kiwimenace on 2010-04-15
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dee7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7070    56789743+   7  HPFS/NTFS
/dev/sda2            7071        9729    21358417+   f  W95 Ext'd (LBA)
/dev/sda5            7071        9613    20426616   83  Linux
/dev/sda6            9614        9729      931738+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9ec72c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7585b15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1150d2b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07249335

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       28086   225600763+   c  W95 FAT32 (LBA)
/dev/sde2           28087       30401    18595237+  83  Linux

---

### Post by kiwimenace on 2010-04-15
fdisk details added to the post that contained my log...

---

