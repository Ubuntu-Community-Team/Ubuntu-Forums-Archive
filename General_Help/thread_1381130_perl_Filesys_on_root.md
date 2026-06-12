---
title: "perl Filesys on root /"
date: 2010-01-14
forum: General Help
---

### Post by comingme on 2010-01-14
========================================
I run a little script that prints the available space for file system:
```
#!/usr/bin/perl5
sub CheckDiskSpace
{
    use Filesys::DiskFree;
    my $handle = new Filesys::DiskFree;
    $handle->df();

$loc1 = '/dev';
$loc2 = '/var/run';
$loc3 = '/boot';
print "... $loc1, $loc2, $loc3, '/' \n";

    foreach my $file ($loc1,$loc2,$loc3,'/' )
    {
        my $bytesavailable=$handle->avail($file);
        print "at $file, available bits = $bytesavailable \n";
    }
}

CheckDiskSpace();
```========================================
[COLOR=DarkOrange]The result is:
... /dev,/var/run,/boot,'/'
at /dev, available bits = 1028820992
at /var/run, available bits = 1028730880
at /boot, available bits =
at /, available bits =[/COLOR]
========================================

I then type command "df -a" and get:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                 1004736       116   1004620   1% /var/run
varlock                1004736         0   1004736   0% /var/lock
[COLOR=DarkOrange]udev                   1004736        28   1004708   1% /dev[/COLOR]
devshm                 1004736        12   1004724   1% /dev/shm
devpts                       0         0         0   -  /dev/pts
tmpfs                  1004736        12   1004724   1% /dev/shm
securityfs                   0         0         0   -  /sys/kernel/security
gvfs-fuse-daemon     620395268  10647256 609748012   2% /root/.gvfs
[COLOR=DarkOrange]/dev/sda1               497829    139305    332822  30% /media/_boot[/COLOR]
```========================================

I then run "gparted" and get the picture as attached. It shows /dev/sda3 is mounted to '/'.

========================================
The thing I do not understand is:
Why cannot perl script tell the available size of "/"?
Why doesnot df command show "/" as a mount point while gparted correctly shows that?

I tried to mount /dev/sda3 to '/' but it says it already exists.
My system is ubuntu server.

Can someone help me? Thanks.

---

