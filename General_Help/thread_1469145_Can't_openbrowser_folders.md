---
title: "Can't open/browser folders"
date: 2010-05-01
forum: General Help
---

### Post by loganvdh on 2010-05-01
So, I'm running Ubuntu 9.10, and I can't open any folders. Nor can I put any files onto my desktop. I read on another thread that you should try reinstalling Nautilus, so I did that, and nothing changed. I also tried to open a folder in the Terminal, in this case the downloads folder, and I got this.
(nautilus:2172): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2172): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2172): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2172): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault
Any help?

---

### Post by tgalati4 on 2010-05-02
Open a terminal:

dmesg | grep error

---

### Post by loganvdh on 2010-05-02
Sorry if this is a little newbish, but now nothing has changed, and it says this:
[   56.248434] nautilus[1985]: segfault at b6e1dfdc ip 00bc8760 sp b6e1dfe0 error 6 in libgvfsdbus.so[bac000+24000]
[  112.099968] nautilus[2038]: segfault at b6f0cfdc ip 00e59760 sp b6f0cfe0 error 6 in libgvfsdbus.so[e3d000+24000]
[  968.017177] nautilus[2228]: segfault at b6de9fdc ip 008a1760 sp b6de9fe0 error 6 in libgvfsdbus.so[885000+24000]
[ 1017.559056] nautilus[2235]: segfault at b6e5afdc ip 00c0c760 sp b6e5afe0 error 6 in libgvfsdbus.so[bf0000+24000]
[ 1093.123558] nautilus[2245]: segfault at b6f5dfdc ip 00ba3760 sp b6f5dfe0 error 6 in libgvfsdbus.so[b87000+24000]

---

### Post by tgalati4 on 2010-05-02
Well, the number in [brackets] is the time in seconds since boot.  Nautilus is definitely having problems.  The number in [brackets] after nautilus is the process number.  You have multiple threads (processes) of nautilus since it tries to restart after each segmentation fault.

A segfault is a serious crash of a program that is not recoverable.  It's equivalent to a Windows Blue Screen of Death, except it doesn't take out your whole operating system with it.

the b6***** is the address where the fault occured.  I'm not sure what the ip and sp designators are.  I'm not sure what error 6 is either.  libgvfsdbus.so is a shared object library (lib and *.so) that has something to do with gnome virtual file system (gvfs) and dbus--the data communication bus--for interprocess communication.

So yes, something is broken.

I don't think nautilus is the problem.  It seems like that your file system is messed up in a subtle way.

What is the output of:

sudo fdisk -l

---

### Post by loganvdh on 2010-05-02
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaeba9ca1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14267   114599646   83  Linux
/dev/sda2           14268       14593     2618595    5  Extended
/dev/sda5           14268       14593     2618563+  82  Linux swap / Solaris

---

### Post by tgalati4 on 2010-05-02
What is the output of:

sudo fsck /dev/sda1
sudo fsck /dev/sda2

Now we need to get into the details:

What are the parts that make up gvfs?

tgalati4@tpad-Gloria7 ~ $ locate gvfs
/etc/profile.d/gvfs-bash-completion.sh
/home/herb3538/.gvfs
/home/tgalati4/.gvfs
/usr/bin/gvfs-cat
/usr/bin/gvfs-copy
/usr/bin/gvfs-info
/usr/bin/gvfs-less
/usr/bin/gvfs-ls
/usr/bin/gvfs-mkdir
/usr/bin/gvfs-monitor-dir
/usr/bin/gvfs-monitor-file
/usr/bin/gvfs-mount
/usr/bin/gvfs-move
/usr/bin/gvfs-open
/usr/bin/gvfs-rename
/usr/bin/gvfs-rm
/usr/bin/gvfs-save
/usr/bin/gvfs-trash
/usr/bin/gvfs-tree
/usr/include/glib-2.0/gio/gvfs.h
/usr/lib/gvfs
/usr/lib/libgvfscommon-dnssd.so.0
/usr/lib/libgvfscommon-dnssd.so.0.0.0
/usr/lib/libgvfscommon.so.0
/usr/lib/libgvfscommon.so.0.0.0
/usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gvfs/gvfs-fuse-daemon
/usr/lib/gvfs/gvfs-gphoto2-volume-monitor
/usr/lib/gvfs/gvfs-hal-volume-monitor
/usr/lib/gvfs/gvfsd
/usr/lib/gvfs/gvfsd-archive
/usr/lib/gvfs/gvfsd-burn
/usr/lib/gvfs/gvfsd-cdda
/usr/lib/gvfs/gvfsd-computer
/usr/lib/gvfs/gvfsd-dav
/usr/lib/gvfs/gvfsd-dnssd
/usr/lib/gvfs/gvfsd-ftp
/usr/lib/gvfs/gvfsd-gphoto2
/usr/lib/gvfs/gvfsd-http
/usr/lib/gvfs/gvfsd-localtest
/usr/lib/gvfs/gvfsd-network
/usr/lib/gvfs/gvfsd-obexftp
/usr/lib/gvfs/gvfsd-sftp
/usr/lib/gvfs/gvfsd-smb
/usr/lib/gvfs/gvfsd-smb-browse
/usr/lib/gvfs/gvfsd-trash
/usr/share/gvfs
/usr/share/dbus-1/services/gvfs-daemon.service
/usr/share/doc/gvfs
/usr/share/doc/gvfs-backends
/usr/share/doc/gvfs-bin
/usr/share/doc/gvfs-fuse
/usr/share/doc/libgvfscommon0
/usr/share/doc/gvfs/AUTHORS
/usr/share/doc/gvfs/NEWS.gz
/usr/share/doc/gvfs/README
/usr/share/doc/gvfs/TODO
/usr/share/doc/gvfs/changelog.Debian.gz
/usr/share/doc/gvfs/copyright
/usr/share/doc/gvfs-backends/AUTHORS
/usr/share/doc/gvfs-backends/NEWS.gz
/usr/share/doc/gvfs-backends/README
/usr/share/doc/gvfs-backends/TODO
/usr/share/doc/gvfs-backends/changelog.Debian.gz
/usr/share/doc/gvfs-backends/copyright
/usr/share/doc/gvfs-bin/AUTHORS
/usr/share/doc/gvfs-bin/NEWS.gz
/usr/share/doc/gvfs-bin/README
/usr/share/doc/gvfs-bin/TODO
/usr/share/doc/gvfs-bin/changelog.Debian.gz
/usr/share/doc/gvfs-bin/copyright
/usr/share/doc/gvfs-fuse/AUTHORS
/usr/share/doc/gvfs-fuse/NEWS.gz
/usr/share/doc/gvfs-fuse/README
/usr/share/doc/gvfs-fuse/TODO
/usr/share/doc/gvfs-fuse/changelog.Debian.gz
/usr/share/doc/gvfs-fuse/copyright
/usr/share/doc/libgvfscommon0/AUTHORS
/usr/share/doc/libgvfscommon0/NEWS.gz
/usr/share/doc/libgvfscommon0/README
/usr/share/doc/libgvfscommon0/TODO
/usr/share/doc/libgvfscommon0/changelog.Debian.gz
/usr/share/doc/libgvfscommon0/copyright
/usr/share/doc/python-gnome2/examples/vfs/pygvfsmethod
/usr/share/doc/python-gnome2/examples/vfs/pygvfsmethod/README
/usr/share/doc/python-gnome2/examples/vfs/pygvfsmethod/pyfs.conf
/usr/share/doc/python-gnome2/examples/vfs/pygvfsmethod/pyfs.py.gz
/usr/share/gvfs/mounts
/usr/share/gvfs/remote-volume-monitors
/usr/share/gvfs/mounts/archive.mount
/usr/share/gvfs/mounts/burn.mount
/usr/share/gvfs/mounts/cdda.mount
/usr/share/gvfs/mounts/computer.mount
/usr/share/gvfs/mounts/dav+sd.mount
/usr/share/gvfs/mounts/dav.mount
/usr/share/gvfs/mounts/dns-sd.mount
/usr/share/gvfs/mounts/ftp.mount
/usr/share/gvfs/mounts/gphoto2.mount
/usr/share/gvfs/mounts/http.mount
/usr/share/gvfs/mounts/localtest.mount
/usr/share/gvfs/mounts/network.mount
/usr/share/gvfs/mounts/obexftp.mount
/usr/share/gvfs/mounts/sftp.mount
/usr/share/gvfs/mounts/smb-browse.mount
/usr/share/gvfs/mounts/smb.mount
/usr/share/gvfs/mounts/trash.mount
/usr/share/gvfs/remote-volume-monitors/gphoto2.monitor
/usr/share/gvfs/remote-volume-monitors/hal.monitor
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gvfs.mo
/usr/share/locale-langpack/ru/LC_MESSAGES/gvfs.mo
/var/lib/dpkg/info/gvfs-backends.list
/var/lib/dpkg/info/gvfs-backends.md5sums
/var/lib/dpkg/info/gvfs-backends.postinst
/var/lib/dpkg/info/gvfs-bin.conffiles
/var/lib/dpkg/info/gvfs-bin.list
/var/lib/dpkg/info/gvfs-bin.md5sums
/var/lib/dpkg/info/gvfs-fuse.list
/var/lib/dpkg/info/gvfs-fuse.md5sums
/var/lib/dpkg/info/gvfs.list
/var/lib/dpkg/info/gvfs.md5sums
/var/lib/dpkg/info/libgvfscommon0.list
/var/lib/dpkg/info/libgvfscommon0.md5sums
/var/lib/dpkg/info/libgvfscommon0.postinst
/var/lib/dpkg/info/libgvfscommon0.postrm
/var/lib/dpkg/info/libgvfscommon0.shlibs
/var/lib/dpkg/info.saved.20100317_154331/gvfs-backends.list
/var/lib/dpkg/info.saved.20100317_154331/gvfs-backends.md5sums
/var/lib/dpkg/info.saved.20100317_154331/gvfs-backends.postinst
/var/lib/dpkg/info.saved.20100317_154331/gvfs-bin.conffiles
/var/lib/dpkg/info.saved.20100317_154331/gvfs-bin.list
/var/lib/dpkg/info.saved.20100317_154331/gvfs-bin.md5sums
/var/lib/dpkg/info.saved.20100317_154331/gvfs-fuse.list
/var/lib/dpkg/info.saved.20100317_154331/gvfs-fuse.md5sums
/var/lib/dpkg/info.saved.20100317_154331/gvfs.list
/var/lib/dpkg/info.saved.20100317_154331/gvfs.md5sums
/var/lib/dpkg/info.saved.20100317_154331/libgvfscommon0.list
/var/lib/dpkg/info.saved.20100317_154331/libgvfscommon0.md5sums
/var/lib/dpkg/info.saved.20100317_154331/libgvfscommon0.postinst
/var/lib/dpkg/info.saved.20100317_154331/libgvfscommon0.postrm
/var/lib/dpkg/info.saved.20100317_154331/libgvfscommon0.shlibs
tgalati4@tpad-Gloria7 ~ $ 
tgalati4@tpad-Gloria7 ~ $ cat /var/lib/dpkg/info/gvfs-bin.list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gvfs-bin
/usr/share/doc/gvfs-bin/README
/usr/share/doc/gvfs-bin/TODO
/usr/share/doc/gvfs-bin/AUTHORS
/usr/share/doc/gvfs-bin/copyright
/usr/share/doc/gvfs-bin/NEWS.gz
/usr/share/doc/gvfs-bin/changelog.Debian.gz
/usr/bin
/usr/bin/gvfs-cat
/usr/bin/gvfs-copy
/usr/bin/gvfs-info
/usr/bin/gvfs-less
/usr/bin/gvfs-ls
/usr/bin/gvfs-mkdir
/usr/bin/gvfs-monitor-dir
/usr/bin/gvfs-monitor-file
/usr/bin/gvfs-mount
/usr/bin/gvfs-move
/usr/bin/gvfs-open
/usr/bin/gvfs-rename
/usr/bin/gvfs-rm
/usr/bin/gvfs-save
/usr/bin/gvfs-trash
/usr/bin/gvfs-tree
/etc
/etc/profile.d
/etc/profile.d/gvfs-bash-completion.sh
tgalati4@tpad-Gloria7 ~ $ 
tgalati4@tpad-Gloria7 ~ $ cat /usr/share/doc/gvfs-bin/README
gvfs is a userspace virtual filesystem designed to work with the i/o
abstractions of gio (a library availible in glib >= 2.15.1). It
installs several modules that are automatically used by applications
using the APIs of libgio. There is also fuse support that allows
applications not using gio to access the gvfs filesystems.

The gvfs model differs from e.g. gnome-vfs in that filesystems must
be mounted before they are used. There is a central daemon (gvfsd)
that handles coordinting mounts, and then each mount is (typically)
in its own daemon process (although mounts can share daemon process).

gvfs comes with a set of backends, including trash support, sftp,
smb, http, dav and others. More backends are planned.

gvfs also contains modules for gio that implement hal volume monitors
and the gnome uri-scheme handler configuration.

There is a set of command line programs starting with "gvfs-" that
lets you run commands (like cat, ls, stat, etc) on files in the gvfs
mounts.

My .gvfs directory is empty on Jaunty.  I'm not sure what files are stored there.

And I think the gvfs stands for gnu virtual file system, as gnome-vfs is something different.

How long were you running 9.10 before this problem started?

Also take a Live CD of 9.10 and run that for a couple of days to make sure that nautilus comes up OK and that you don't have some mysterious hardware problem.

So, I don't think you have a nautilus problem.  If you can open a terminal shell and move around the directories, then the file system should be intact.  That leaves the interaction with nautilus with gvfs and dbus.  I wouldn't try to reinstall gvfs or dbus because that can cause breakage.

---

### Post by nivek1385 on 2010-06-12
I'm having a similar issue.  Running nautilus via sudo or with a path appended is fine.  Running nautilus normally and via Gnome Do neither one work.  Running nautilus via command line gives a segfault.  Looking in var/log/messages, I get the following:

Jun 12 21:37:26 laptux kernel: [  386.764996] nautilus[4364]: segfault at 1732bdb ip 01732bdb sp b5e6a0e0 error 4 in libavutil.so.49.15.0[1a02000+c000]
Jun 12 21:54:44 laptux kernel: [ 1424.756118] nautilus[5401]: segfault at 1d0899d ip 01d0899d sp b5ea91b0 error 4 in libxvidcore.so.4.1[1d37000+9e000]
Jun 12 22:35:19 laptux kernel: [ 3859.199261] nautilus[9521]: segfault at 1e61bdb ip 01e61bdb sp b5cfe130 error 4 in libamrnb.so.3.0.0[254a000+39000]
Jun 12 22:36:18 laptux kernel: [ 3918.762541] nautilus[9585]: segfault at 5bcb99d ip 05bcb99d sp b5e22160 error 4 in libstdc++.so.6.0.13[5e0c000+e6000]
Jun 12 22:38:40 laptux kernel: [ 4060.844424] nautilus[9800]: segfault at 7abdbdb ip 07abdbdb sp b5e6e130 error 4 in libvorbisenc.so.2.0.3[7eb2000+b000]
Jun 12 22:59:18 laptux kernel: [ 5298.223303] nautilus[11820]: segfault at 38bbbdb ip 038bbbdb sp b5ea6130 error 4 in libopenjpeg-2.1.3.0.so[397b000+1d000]
Jun 12 22:59:54 laptux kernel: [ 5335.015369] nautilus[11861]: segfault at 608cbdb ip 0608cbdb sp b5f36130 error 4 in libdvdcss.so.2.1.0[66aa000+8000]

Of course, the workaround for this is just setting an alias such that when executing "nautilus" it instead executes "nautilus ~" but that doesn't solve the actual problem, just works around it.  Any ideas?

---

