---
title: "apt-get update/install errors"
date: 2006-03-04
forum: General Help
---

### Post by wjk3 on 2006-03-04
Hello,

I'm new to Ubuntu and Linux in general.  I have been running it for a week or so and have installed it a few times and had a few issues with it.

my problem now is this.

wjk3@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release .gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Pa ckages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restric ted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Pa ckages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restric ted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Get:1 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy Release.gpg [189B]
Get:2 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security Release.gpg [189B]
Get:3 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates Release.gpg [189B]
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy Release
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security Release
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates Release
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/main Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/restricted Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/multiverse Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/main Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/restricted Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/universe Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/multiverse Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/main Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/restricted Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/universe Packages
Hit [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/multiverse Packages
Fetched 3B in 1s (2B/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/di sts/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-RO M recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/di sts/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this  CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Relea se i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fB reezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i38 6_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Relea se i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10% 20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricte d_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

The error lines are what the problem is.  I cant install an application either.

wjk3@ubuntu:~$ sudo apt-get install vlc libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package libdvdcss2 has no installation candidate
wjk3@ubuntu:~$


Not sure what the problem is. The only things I've run since installing it the last time is Automatiks.  Installed Firefox 1.5 and some of the plugins for it, JRE 1.5, and can't recall what else.

Any help, assistance, information is appreciated very much in advance.

Thanks

---

### Post by poningru on 2006-03-04
go into synaptic (system->admin->synaptic) and then go into settings->repositories and then remove the cdrom repository.

---

### Post by wjk3 on 2006-03-04
Thanks. Did that and it fixed it.

---

