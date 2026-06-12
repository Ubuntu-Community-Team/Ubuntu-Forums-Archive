---
title: "Package Manager and Repository problem"
date: 2006-05-25
forum: General Help
---

### Post by keirnna on 2006-05-25
I wanted to stop using the Ubuntu install DVD as a repository, so I unchecked it from the list of repositories in the package manager. I then started to get these errors:
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

So I went back into my repositories and checked the install DVD, but I now get this error:
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

My overall goal is to not use the DVD to install packages, because I normally don't have an optical drive with my laptop. If this is not possible then I would like to get rid of this error. TIA!

---

### Post by keirnna on 2006-05-25
I also tried this:

keirnna@ubuntulapnak:~$ apt-cdrom
apt 0.6.40.1ubuntu10 for linux i386 compiled on Apr 22 2006 02:17:30
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See fstab(5)
keirnna@ubuntulapnak:~$ apt-cdrom -d /media/cdrom0
apt 0.6.40.1ubuntu10 for linux i386 compiled on Apr 22 2006 02:17:30
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See fstab(5)
keirnna@ubuntulapnak:~$ apt-cdrom add -d /media/cdrom0
Using CD-ROM mount point /media/cdrom0/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [c367d1545bb0b8959110c9705b941245-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
Copying package lists...gpgv: Signature made Thu 13 Oct 2005 03:48:47 AM JST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
E: Could not open file /var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_Release - open (13 Permission denied)
E: Could not open file /var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_Release.gpg - open (13 Permission denied)

---

