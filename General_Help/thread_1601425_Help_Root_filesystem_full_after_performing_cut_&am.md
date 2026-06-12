---
title: "Help: Root filesystem full after performing cut &amp; paste in Webmin File Manager"
date: 2010-10-20
forum: General Help
---

### Post by ukkisavosta on 2010-10-20
Hello everyone,

Total newbie here. I am running Ubuntu Linux 10.04.1 on an AMD 64-bit system. The server is primarily used for Windows file sharing via Samba in a small local network. I use webmin and putty to administer the system. I have two 1.4 TB drives for storage and one 500 GB drive with 18 GB mounted for root.

Problem: I performed a large cut & paste operation (25.8 GB of files) using the File Manager in Webmin to move a certain folder into another folder within /media/Work. The operation failed and I am now getting a "root filesystem full" error, and am stumped.

Output for command "df -h":

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root
                       18G   18G     0 100% /
none                  873M  276K  872M   1% /dev
none                  877M     0  877M   0% /dev/shm
none                  877M  600K  877M   1% /var/run
none                  877M     0  877M   0% /var/lock
none                  877M     0  877M   0% /lib/init/rw
/dev/sda1             228M   33M  184M  15% /boot
/dev/mapper/ubuntu-Backups
                      440G  284M  417G   1% /media/Backups
/dev/mapper/samsung_b-Files
                      1.4T  109G  1.2T   9% /media/Files
/dev/mapper/samsung_c-Work
                      1.4T   36G  1.3T   3% /media/Work
Output for command "du -hs /*":

> 
7.7M    /bin
33M     /boot
4.0K    /cdrom
276K    /dev
22M     /etc
54M     /home
0       /initrd.img
0       /initrd.img.old
272M    /lib
0       /lib64
16K     /lost+found
160G    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/7561/task/7561/fd/3': No such file or directory
du: cannot access `/proc/7561/task/7561/fdinfo/3': No such file or directory
du: cannot access `/proc/7561/fd/3': No such file or directory
du: cannot access `/proc/7561/fdinfo/3': No such file or directory
0       /proc
128K    /root
7.4M    /sbin
4.0K    /selinux
4.0K    /srv
0       /sys
20K     /tmp
1.2G    /usr
280M    /var
0       /vmlinuz
0       /vmlinuz.old
4.0K    /webmin-setup.out
I'd be grateful if anyone could give me a hand and point me in the right direction. 

Thanks a lot!

---

### Post by ukkisavosta on 2010-10-20
Just an update on this: I performed some find functions for large files and rebooted the server a couple of times, and I am now getting garbled entries in the directory listing at /.

> 
\r
6g\232
\bA\b\204\b\213\b\303\b\306\b\307\b\310\b\334\b\335\b\336\b\337\b\340\b\343\bd
bin
\225B*\002^J\002aJ\030mH\v\004ph\377sH\v\004\030\025h=
boot
\177\001\277$\001\277$\001B\f\373R\001\301\f\360\021,\034\022a\001\320\031\001\2                      14\004\001\f\300
cdrom
\265\255D
:\023\330d5\217\253
dev
\214\037\377\377\377\377\377\372D\002\002@\020\002\bhE
etc
\225\026h=
\360\200hL\374\004\001\277\224\b\200\237AVÜB
home
initrd.img
initrd.img.old
\rj0J\032aJ\030\016\005
\rj0J\032aJ\030cH\001dhdhdh\235S\271
\rjaJ\030cH\001dhdhdh\236S\271
\rjaJ\030cH\001dhdhdh\235S\271
\rjaJ\030mH\v\004sH\v\0041\b\026h
\rjaJ\030mH\v\004sH\v\004\037\025h\354-\230\026h
\225^J\002aJ\030mH\v\004sH\v\004\026\b\024\bM\bg\b\003
\316\340\251\330}\343\262jv\366$
\250\357\016\343\214.L\020H\307d^\372~\225\365\216\240N\360T\220\366\360\037\360                      \221\325\314[\330\021\212
lib
lib64
lost+found
media
mnt
\231\020\215@\001\230N\342\020\004\223
\204\002Å\250\022\001ED\002\325\354s\022\001L\004\002\347\344\367\022\001R\326\0                      02\371\242\255\022\001Y\226\003
opt
\371@\307\327P
\006\205\b\037\244\371P\2053\3225
\225PJ\003^J\002aJ\030\034\025h=
\225PJ\003^J\002aJ\030mH\004nH\004sH\v\004u\b\001%\025h=
proc
\020PVGqY\306]D\035A\004\234\001\003d\377\367VU\367\255J7v\002sV\317á¶¿\256\372\                      3\360q\307\001\324\371\277$\001\274_\001\3468b\001\254\034\217\177\0010\277\177\                      001\242\204\035\377\r\017\r\306\005\001\240\017\017\204Q\005\021\204\035\377^\20                      4Q\005m\f\024\003$\001
root
sbin
selinux
SrP\375\376\226\024\342\0338\230E\vB\241p\344Io\227p\264\246Q=\204Jb\021\002\233                      \274\231\270W\351L\351sL\211\211Ó\260YN\237K-,È\242B\344s\250~\025Ð¤\354Í°\215>c                      (A\226\025\002$\211\244IR\236i\221\bÈ,\271\030_)m\224\322\360\264\221)\036dK-)dC                      \246\302\302\306\\\330[\225\ni*YORR\323Ê263P\221\n\224#=+3OJl\230\234\211\246R\3                      16\302<\240\204\ \224,\374O\022\377\376\f9\023s\020Ð¥\rOi\377\351It:SCYt\351r\31                      7\313\033\225
srv
sys
tmp
\242U\271\264\266\264\213\366\343\376\037\310
usr
var
vmlinuz
vmlinuz.old
\362V\367\224\353:*Ur\253W\245R\317\177m\261R
\376\267w\003
webmin-setup.out
How quaint. If there's something positive in this, I can still log into the server and my root filesystem usage is down from 100% to 98%.

> 
Usage of /:   98.0% of 17.52GB
I don't know how to perform a fsck on the root (how does one go about unmounting "/"?) and I tried to rm one of the garbled directories/files with no luck, so I'm pretty much out of ideas.

Seems like I'm going to have to do a full reinstall from scratch. I just can't understand how Webmin's File Manager managed to cause all this trouble.

---

### Post by albandy on 2010-10-20
Boot with a livecd and type: sudo fsck /dev/sda1
considering sda1 as / partition.

---

### Post by ukkisavosta on 2010-10-20
> **albandy said:**
> Boot with a livecd and type: sudo fsck /dev/sda1
considering sda1 as / partition.

Thanks for the suggestion - I'll try that.

---

### Post by ukkisavosta on 2010-10-20
Ok, I booted up the server with a Ubuntu 10.10 LiveCD and launched Gparted, which would only crash due to an assertion error. I then launched Disk Utility and identified all volumes in the suspected drive (sda1, sda2 and sda5). I ran Fsck on these, and it reported the following:

sda1: clean

sda2: "...short read while trying to open... zero length partition?"

sda5: "fsck.LVM2_member: not found. Error 2 while executing..."

Afterwards I booted the server back up, and was greeted with the following root filesystem usage:

> 
Usage of /:   11.3% of 17.52GB
So I'm pretty much back to normal concerning root filesystem usage, but I still get the garbled entries in the root directory listing. I'm totally lost as to what took place, why and when, but everything seems to work normally, save for those garbled entries which give me a "no such file or directory" error when I try to remove/rename/chown them.

I checked the kernel log and the only disk-related entries I could find were:

> 
Oct 20 20:01:46 ubuntu kernel: [    6.223085] kjournald starting.  Commit interval 5 seconds
Oct 20 20:01:46 ubuntu kernel: [    6.223095] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Oct 20 20:01:46 ubuntu kernel: [    6.223461] EXT3 FS on dm-4, internal journal
Oct 20 20:01:46 ubuntu kernel: [    6.223465] EXT3-fs: mounted filesystem with ordered data mode.
Oct 20 20:01:46 ubuntu kernel: [    6.274136] kjournald starting.  Commit interval 5 seconds
Oct 20 20:01:46 ubuntu kernel: [    6.274140] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Oct 20 20:01:46 ubuntu kernel: [    6.274412] EXT3 FS on dm-1, internal journal
Oct 20 20:01:46 ubuntu kernel: [    6.274415] EXT3-fs: mounted filesystem with ordered data mode.
Oct 20 20:01:46 ubuntu kernel: [    6.309197] kjournald starting.  Commit interval 5 seconds
Oct 20 20:01:46 ubuntu kernel: [    6.309201] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Oct 20 20:01:46 ubuntu kernel: [    6.309473] EXT3 FS on dm-0, internal journal
Oct 20 20:01:46 ubuntu kernel: [    6.309476] EXT3-fs: mounted filesystem with ordered data mode.
Not sure whether these are relevant in any way. I'm still contemplating as to whether I should just do a complete reinstall or not.

---

### Post by SwellJoe on 2010-10-20
> **ukkisavosta said:**
> I just can't understand how Webmin's File Manager managed to cause all this trouble.

The File Manager is not magic. It uses standard filesystem functions for all of its actions, so, moving the files from the command line would have resulted in the same behavior.

The possibilities are endless for what could have gone wrong, but I would first suspect hardware problems. Try running badblocks on your disk. If there are any errors, you have a failing disk. You can also check the SMART status. Webmin has a module for SMART, which works with most modern disks (though not all, and not if you're in a VPS).

If your filesystem is ext4, that may be to blame. We've had a couple of reports of odd behaviors out of systems running ext4 that went away when the user reverted to ext3. (That said, I use ext4 on my desktop and laptop and have never had problems, so who knows. I don't really think this is the cause of the problem you're having, but I thought I'd mention it.)

Failing RAM can also cause problems like this, especially during large file operations.

In short, the fact that you performed the operation is Webmin is a red herring. Just because you happened to be looking at and clicking around in Webmin when the problem happened, doesn't mean Webmin caused the problem.

---

### Post by ukkisavosta on 2010-10-21
Hi SwellJoe,

Thanks for the input. Good to hear that File Manager is an unlikely culprit, as I think it's a very handy app. I'm not familiar with the underlying mechanisms, but based on the log files it seems very transparent and the commands it issued were, like you said, nothing magic. I still doubt whether issuing the commands through the command line would have caused changes in the root filesystem, because I would have issued the commands as a normal user without root permissions (whereas File Manager has full root permissions). Actually, I should've issued the command through one of my Windows computers, because the files were in a shared Samba folder.

Filesystems are ext3, so no problem there. As for RAM, I ran Memtest without a hitch before installing Ubuntu, so I guess that's ruled out as well. The media drives are new Samsung units, but my system drive is an ill-fated Seagate, which has been recovered from the BSY state previously (see [http://www.msfn.org/board/topic/128092-seagate-barracuda-720011-troubles/](http://www.msfn.org/board/topic/128092-seagate-barracuda-720011-troubles/)). It hasn't given me any trouble since, but you never know... but why should the system drive be concerned in a file operation taking place in a completely different drive? If it's using a temporary folder, shouldn't it be outside the root filesystem?

---

### Post by ukkisavosta on 2010-11-08
I was finally able to delete the zero length files using the following command:

```

sudo find / -maxdepth 1 -type f -size 0 -ok rm {} \;

```So I consider this problem solved.

N.B. This code will remove all zero length files in the root directory, so be careful. You can replace "/" with the target directory. If you wish to delete directories instead of files, replace "-type f" with "-type d".

---

### Post by ukkisavosta on 2010-11-10
I have now realised why this problem happened in the first place. Coming from the Windows world, I haven't yet adjusted my mind to the way Linux handles filesystems, so I originally created the target directory for the files in the root filesystem instead of the correct filesystem for the media, and the root filesystem did not have sufficient space to store the copied files.

I'd mounted my filesystems in /media/Files and /media/Work (each mounted filesystem being essentially a large partition in a separate physical drive). I then made the newbie mistake of creating a directory in /media instead of under either one of the mounted filesystems, and this new directory was naturally created in the root filesystem.

Also, the root filesystem is ext4 instead of ext3. I'm not sure whether this makes any difference, but I understand there is a possibility of corrupt files being created through delayed writes gone bad.

Anyway, PEBKAC. Will know better next time.

---

