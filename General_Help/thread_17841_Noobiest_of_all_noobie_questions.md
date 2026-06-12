---
title: "Noobiest of all noobie questions"
date: 2005-03-03
forum: General Help
---

### Post by BillyD on 2005-03-03
Being a Windows user, I am familiar of where to keep my personal files stored.  However, in ubuntu/linux, all of the folder names are kinda foreign.  So, my question is, what is the recommended location of storing personal files?  In other words, what is the equivalent of the "My Documents" folder of Windows in Ubuntu?   Thanks!

---

### Post by jsgotangco on 2005-03-03
In a linux system the /home folder is where users get to put their files, etc. Inside the /home folder are the use folders, so let's say you have a username of billyd, your home folder is located at /home/billyd

This folder is created during configuration and setup. Inside your /home/billyd folder, you can get to put any files you want.

---

### Post by BillyD on 2005-03-03
[QUOTE=jsgotangco]In a linux system the /home folder is where users get to put their files, etc. Inside the /home folder are the use folders, so let's say you have a username of billyd, your home folder is located at /home/billyd

This folder is created during configuration and setup. Inside your /home/billyd folder, you can get to put any files you want.[/QUOTE]
 Oh okay, I see.  Thanks for the quick reply!

---

### Post by doni on 2005-03-03
here's a little guide to the linux filesystem architecture:

> /sbin - This directory contains all the binaries that are essential to the
working of the system. These include system administration as well as
maintenance and hardware configuration programs. Find lilo, fdisk, init,
ifconfig etc here. These are the essential programs that are required by
all the users. Another directory that contains system binaries is /usr/sbin.
This directory contains other binaries of use to the system administrator.
This is where you will find the network daemons for your system along with
other binaries that only the system administrator has access to, but which are
not required for system maintenance, repair etc.

/bin - In contrast to /sbin, the bin directory contains several useful
commands that are used by both the system administrator as well as
non-privileged users. This directory usually contains the shells like
bash, csh etc. as well as much used commands like cp, mv, rm, cat, ls.
There also is /usr/bin, which contains other user binaries. These binaries
on the other hand are not essential for the user. The binaries in /bin
however, a user cannot do without.

/boot - This directory contains the system.map file as well as the Linux
kernel. Lilo places the boot sector backups in this directory.

/dev - This is a very interesting directory that highlights one important
characteristic of the Linux filesystem - everything is a file or a
directory. Look through this directory and you should see hda1, hda2 etc,
which represent the various partitions on the first master drive of the
system. /dev/cdrom and /dev/fd0 represent your CDROM drive and your floppy
drive. This may seem strange but it will make sense if you compare the
characteristics of files to that of your hardware. Both can be read from
and written to. Take /dev/dsp, for instance. This file represents your
speaker device. So any data written to this file will be re-directed to
your speaker. Try 'cat /etc/lilo.conf > /dev/dsp' and you should hear some
sound on the speaker. That's the sound of your lilo.conf file! Similarly,
sending data to and reading from /dev/ttyS0 ( COM 1 ) will allow you to
communicate with a device attached there - your modem.

/etc - This directory contains all the configuration files for your system.
Your lilo.conf file lies in this directory as does hosts, resolv.conf and
fstab. Under this directory will be X11 sub-directory which contains the
configuration files for X. More importantly, the /etc/rc.d directory
contains the system startup scripts. This is a good directory to backup
often. It will definitely save you a lot of re-configuration later if you
re-install or lose your current installation.

/home - Linux is a multi-user environment so each user is also assigned a
specific directory which is accessible only to them and the system
administrator. These are the user home directories, which can be found
under /home/username. This directory also contains the user specific
settings for programs like IRC, X etc.

/lib - This contains all the shared libraries that are required by system
programs. Windows equivalent to a shared library would be a DLL file.

/lost+found - Linux should always go through a proper shutdown. Sometimes
your system might crash or a power failure might take the machine down.
Either way, at the next boot, a lengthy filesystem check using fsck will
be done. Fsck will go through the system and try to recover any corrupt
files that it finds. The result of this recovery operation will be placed
in this directory. The files recovered are not likely to be complete or
make much sense but there always is a chance that something worthwhile is
recovered.

/mnt - This is a generic mount point under which you mount your filesystems
or devices. Mounting is the process by which you make a filesystem
available to the system. After mounting your files will be accessible
under the mount-point. This directory usually contains mount points or
sub-directories where you mount your floppy and your CD. You can also
create additional mount-points here if you want. There is no limitation to
creating a mount-point anywhere on your system but convention says that
you do not litter your file system with mount-points.

/opt - This directory contains all the software and add-on packages that
are not part of the default installation. Generally you will find KDE and
StarOffice here. Again, this directory is not used very often as it's
mostly a standard in Unix installations.

/proc - This is a special directory on your system. We have a more detailed
article on this one here.

/root - We talked about user home directories earlier and well this one is
the home directory of the user root. This is not to be confused with the
system root, which is directory at the highest level in the filesystem.

/tmp - This directory contains mostly files that are required temporarily.
Many programs use this to create lock files and for temporary storage of
data. On some systems, this directory is cleared out at boot or at
shutdown.

/usr - This is one of the most important directories in the system as it
contains all the user binaries. X and its supporting libraries can be
found here. User programs like telnet, ftp etc are also placed here.
/usr/doc contains useful system documentation. /usr/src/linux contains the
source code for the Linux kernel.

/var - This directory contains spooling data like mail and also the output
from the printer daemon. The system logs are also kept here in
/var/log/messages. You will also find the database for BIND in /var/named
and for NIS in /var/yp. 

stolen from: [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/) 

most important for you are propably /etc and /home.

cheerio

---

### Post by Jad on 2005-03-03
Good article doni.
Billy, Linux gives you the power to customize your desktop just as you want it to be, you can organize your folders under /home/billy assuming your username is billy as you want 
for example 
under /home/jad/ I have the following directories 
Documents  to save my personal and business documents, and I have more directories under the /home/jad/Documents 
also I have Downloads directory with categoriezed directories under it 
same for music and movies

---

### Post by jsgotangco on 2005-03-03
also the advantage of having /home/user in a separate partition is that even if you bork the whole system you can just reinstall the whole linux system again but make sure you don't format the /home/user so that files still get intact.

/home/user also has A LOT of hidden files that contains user-specific configurations like your themes, icons an the hidden folders/files usually start with a dot.

---

### Post by BillyD on 2005-03-04
Thanks for the input everyone.  This helps out a lot.   :D

---

