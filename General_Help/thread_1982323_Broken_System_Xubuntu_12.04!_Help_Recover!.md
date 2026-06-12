---
title: "Broken System Xubuntu 12.04! Help Recover!"
date: 2012-05-18
forum: General Help
---

### Post by childe joseph on 2012-05-18
I've been working on my problem(s) since yesterday morning. I had a bad shut down on my system. Upon reboot Grub seemed fine I was able to mount my encrypted drive, and delivered to lightdm login prompt. After typing my password, screen dropped to verbose for a sec like usual, but instead of taking me to my desktop I was back at my login screen. O.K. I tried various workarounds. First tried ctrl+alt+F1 dropped to console logged in my user, ran startx, output was:

xauth:  file /root/.Xauthority does not exist


Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable
xinit: server error



next I ran,  startx  --  :1 

after that screen just went black....nothing!

hmmm....reboot now!

Repeated above process this time I logged in through tty console, stopped lightdm, remember

"Server is already active for display 0"

ctrl+alt+F6 confirmed lightdm was stopped. I did delete the specified file at /tmp/.XO-lock.

Yes at that point I was able to still browse file system and make changes. It's at this point that I should have started moving files to my external HDD. But I still was not all too worried.

Still in terminal. I decided to reconfigure X altogether using dpkg. That didn't work. O.K. how about " sudo dpkg-reconfigure -a" with no errors upon the return of my prompt. Good. Maybe I should have ran "update-initramfs" and "update-grub" just to cover my bases but I did not!

reboot now!

Grub is still working. I'm  still able to successfully mount encrypted volume sda5_crypt  ( The only light I can still see at the end of this tunnel)

Now after I successfully mount the encrypted drive, I'm dropped to initramfs prompt. Well this might be good, so I type "exit" and my output looks like

/init: line 352:can't open /root/dev/console: no such file
[ 432.790729] Kernel panic - not syncing: Attempted to kill init!
[ 432.790790] Pid: 1, comm: init Not tainted 3.2.0-24-generic-pae #37-Ubuntu
[ 432.790851] Call Trace:
[ 432.790884]  [<c1592732>] ? printk+0xx2d/0x2f
[ 432.790926]  [<c1592600>] panic+0x161
[ 432.790969]  [<c105dfe4>] forget_original_parent+0x1e4/0x1f0
[ 432.791024]  [<c10eab21>] ? perf_cgroup_attach_task+0x11/0x20
[ 432.791077]  [<c10eab30>] ? perf_cgroup_attach_task+0x20/0x20
[ 432.791130]  [<c105e004>] exit_notify+0x14/0x140
[ 432.791174]  [<c105e7dc>] do_exit+0x1ac/0x390
[ 432.791215]  [<c114497d>] ? vfs_write+0xed/0x160 
[ 432.791260]  [<c105eb18>] do_group_exit+0x38/0xa0
[ 432.791304]  [<c105eb98>] sys_exit_group+0x18/0x20
[ 432.791350]  [<c15af11f>] sysenter_do_call+0x12/0x28
[ 432.791400] panic occured, switching back to text console

Any help in recovering my broken system would be greatly appreciated.

---

### Post by Toz on 2012-05-18
Log into your account via Ctrl+Alt+F1 and inspect the ownership of the files .Xauthority and .ICEauthority. If not owned by you, either change ownership or simply delete the files and try again.

~/.xsession-errors may also contain some information about why the login is failing.

---

### Post by childe joseph on 2012-05-18
> **Toz said:**
> Log into your account via Ctrl+Alt+F1 and inspect the ownership of the files .Xauthority and .ICEauthority. If not owned by you, either change ownership or simply delete the files and try again.

~/.xsession-errors may also contain some information about why the login is failing.

Ctrl+Alt+F1 is the blinking initramfs prompt. 
Ctrl+Alt+ F2-F6 is just a blinking curser. There are no tty consoles present

---

### Post by steeldriver on 2012-05-18
I think your best option at this point is to boot with a LiveCD or USB and fix the boot partition from there - you may find this useful:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by childe joseph on 2012-05-23
I solved this issue myself. I didn't bother to save the system. I just  needed my encrypted Home folder. I didn't find a "precise" solution  altogether I did alot of searching before finding 4 or5 articles I could  seam together to come up with this. One article in particular I was  located on a Fedora forum. My issue stemmed from a bad shut down. I  figure a few config files got scrambled. When I rebooted I was able to  boot with grub fine, enter the password to mount my encrypted LVM. On  the login screen ,  I could enter my password to login and mount the  encrypted Home folder, and I would get a bunch of errors and finally a  kernel panic! I couldn't bring up a terminal with Ctrl+Alt+F1-6. 

In finding a solution the hardest part seemed to be the disk and folder  encryptions. I hope this helps others who might come across the same  sort of problem. What took me close to 12 hrs, will take all of  about  15 minutes.

To follow these instructions you must know your LVM password to  unencrypt and mount it, as well as know your password to unencrypt and  mount your home folder. Start by booting Live Ubuntu 12.04 Cd, choose  Try Ubuntu. When you reach the desktop, go to the menu and start typing  terminal. Open terminal and start. 

sudo apt-get install lvm2

ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7490

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156301311    77899777    5  Extended
/dev/sda5          501760   156301311    77899776   83  Linux

Disk /dev/sdb: 500.1 GB, 500107859968 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002267

For me, my encrypted home folder is located on /dev/sda5, type

root@ubuntu:~# cryptsetup -v luksDump /dev/sda5
LUKS header information for /dev/sda5

Version:           1
Cipher name:       aes
Cipher mode:       cbc-essiv:sha256
Hash spec:         sha1
Payload offset:    2056
MK bits:           256
MK digest:         82 75 54 55 08 50 dd 3b 6b 29 4a 3d 83 00 e7 f8 69 cf c9 e6 
MK salt:           67 c5 c6 e3 58 f1 cf 59 40 40 63 55 19 2d 61 45 
                   8d 59 46 a4 e7 af ae 04 75 7d bb cc 6a a5 be d9 
MK iterations:     20750
UUID:              3ef89f2e-a91a-4b8c-b875-dc350bcb357d

Key Slot 0: ENABLED
    Iterations:             83305
    Salt:                   3b e6 26 b4 09 1c 36 ed d4 1f 1a d6 a9 13 87 e3 
                              ff c0 4c d7 27 1d b8 5b d8 84 ff 65 b3 de a0 b6 
    Key material offset:    8
    AF stripes:                4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED
Command successful.

root@ubuntu:~# lvdisplay

--- Logical volume ---
  LV Name                /dev/yourLVname/root
  VG Name                freedomnet
  LV UUID                XbjpIT-YdGc-VOGH-gLGP-jdnd-z47i-SZt26p
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                72.80 GiB
  Current LE             18636
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Name                /dev/yourLVname/swap_1
  VG Name                freedomnet
  LV UUID                vBveYw-G1Y8-uFF3-a0Iz-kr9m-9plr-1Ci1Ol
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                1.49 GiB
  Current LE             382
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

Make the LVM active, type 

root@ubuntu:~# vgchange -a y yourLVname
 2 logical volume(s) in volume group "yourLVname" now active

root@ubuntu:~# ecryptfs-add-passphrase --fnek
passphrase:

root@ubuntu:~# ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/f3febdcc-5ccd-4e26-859f-9776e9f902fd/home/.ecryptfs/yourhomefolder/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [cc52165c89839b0f] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.cEtgzpLq].

root@ubuntu:~# ecryptfs-mount-private

Change ownership of your encrypted home folder to the current live root,  to make it so you can move files to your external USB or HD.

chown root /tmp/ecryptfs.cEtgzpLq
chown: changing ownership of `/tmp/ecryptfs.cEtgzpLq': Read-only file system

root@ubuntu:~# sudo nautilus

to open nautilus as root, press F3 in that window, browse to the files  you just unencrypted, on the otherside open directory of your external  USB storge device or HD....and start copying the files.

---

