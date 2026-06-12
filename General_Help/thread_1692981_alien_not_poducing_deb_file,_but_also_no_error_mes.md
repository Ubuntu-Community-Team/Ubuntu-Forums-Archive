---
title: "alien not poducing deb file, but also no error message"
date: 2011-02-22
forum: General Help
---

### Post by LonelyStar on 2011-02-22
Hi,

I want to install drivers for a SensAble Phantom OMNI.
I got a package from the SensAble homepage, containing a rpm.
So I did:

```

sudo alien phantomdevicedrivers-4.3-1.i686.rpm
Warning: Skipping conversion of scripts in package phantomdevicedrivers: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
phantomdevicedrivers_4.2-3_i386.deb generated

```

But it is wrong. No deb file is created. But, as you can see, there is also no error message.
What could be wrong? What can I do?

Thanks!
Nathan

---

### Post by anglican on 2011-02-22
> **LonelyStar said:**
> Hi,

I want to install drivers for a SensAble Phantom OMNI.
I got a package from the SensAble homepage, containing a rpm.
So I did:

```

sudo alien phantomdevicedrivers-4.3-1.i686.rpm
Warning: Skipping conversion of scripts in package phantomdevicedrivers: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
phantomdevicedrivers_4.2-3_i386.deb generated

```But it is wrong. No deb file is created. But, as you can see, there is also no error message.
What could be wrong? What can I do?

Thanks!
NathanWhat output do you get if you use the "--verbose" or "--veryverbose" options for alien?

H

---

### Post by LonelyStar on 2011-02-23
Hey,

Thanks for the reply. The output:

```


sudo alien phantomdevicedrivers-4.3-1.i686.rpm --scripts --veryverbose
	LANG=C rpm -qp --queryformat %{NAME} phantomdevicedrivers-4.3-1.i686.rpm
phantomdevicedrivers
	LANG=C rpm -qp --queryformat %{VERSION} phantomdevicedrivers-4.3-1.i686.rpm
4.2
	LANG=C rpm -qp --queryformat %{RELEASE} phantomdevicedrivers-4.3-1.i686.rpm
2
	LANG=C rpm -qp --queryformat %{ARCH} phantomdevicedrivers-4.3-1.i686.rpm
i686
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} phantomdevicedrivers-4.3-1.i686.rpm
- release 2
	LANG=C rpm -qp --queryformat %{SUMMARY} phantomdevicedrivers-4.3-1.i686.rpm
SensAble PHANToM device drivers
	LANG=C rpm -qp --queryformat %{DESCRIPTION} phantomdevicedrivers-4.3-1.i686.rpm
The PHANToM device drivers provide support for devices in the SensAble PHANToM family.
	LANG=C rpm -qp --queryformat %{PREFIXES} phantomdevicedrivers-4.3-1.i686.rpm
/usr
	LANG=C rpm -qp --queryformat %{POSTIN} phantomdevicedrivers-4.3-1.i686.rpm
/sbin/ldconfig
ln -sf /dev/parport0 /dev/phnepp
	LANG=C rpm -qp --queryformat %{POSTUN} phantomdevicedrivers-4.3-1.i686.rpm
/sbin/ldconfig
if [ $1 = 0 ] ; then
    rm -f /dev/phnepp
fi
	LANG=C rpm -qp --queryformat %{PREUN} phantomdevicedrivers-4.3-1.i686.rpm
(none)
	LANG=C rpm -qp --queryformat %{LICENSE} phantomdevicedrivers-4.3-1.i686.rpm
commercial
	LANG=C rpm -qp --queryformat %{PREIN} phantomdevicedrivers-4.3-1.i686.rpm
(none)
	LANG=C rpm -qcp phantomdevicedrivers-4.3-1.i686.rpm
	rpm -qpi phantomdevicedrivers-4.3-1.i686.rpm
Name        : phantomdevicedrivers         Relocations: /usr 
Version     : 4.2                               Vendor: SensAble Technologies
Release     : 2                             Build Date: Mon 19 Sep 2005 04:45:24 PM CEST
Install Date: (not installed)               Build Host: Hasan-Linux.sensable.com
Group       : System                        Source RPM: phantomdevicedrivers-4.2-2.src.rpm
Size        : 1605633                          License: commercial
Signature   : (none)
Packager    : SensAble Technologies
URL         : http://www.sensable.com/
Summary     : SensAble PHANToM device drivers
Description :
The PHANToM device drivers provide support for devices in the SensAble PHANToM family.

	LANG=C rpm -qpl phantomdevicedrivers-4.3-1.i686.rpm
/etc/SensAble/PHANToMDeviceDrivers
/usr/lib/libPHANToMIO.so
/usr/lib/libPHANToMIO.so.4.2
/usr/sbin/PHANToMConfiguration
/usr/sbin/PHANToMTest
/usr/sbin/devid
/usr/sbin/hload
/usr/share/PHANTOM/doc
/usr/share/PHANTOM/doc/HW_userguide_Linux.pdf
	mkdir phantomdevicedrivers-4.2
	chmod 755 phantomdevicedrivers-4.2
	rpm2cpio phantomdevicedrivers-4.3-1.i686.rpm | lzma -t -q > /dev/null 2>&1
	rpm2cpio phantomdevicedrivers-4.3-1.i686.rpm | (cd phantomdevicedrivers-4.2;  cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
3139 blocks
	chmod 755 phantomdevicedrivers-4.2/./
	chmod 755 phantomdevicedrivers-4.2/./usr
	chmod 755 phantomdevicedrivers-4.2/./usr/lib
	chmod 755 phantomdevicedrivers-4.2/./usr/sbin
	chmod 755 phantomdevicedrivers-4.2/./usr/share
	chmod 755 phantomdevicedrivers-4.2/./usr/share/PHANTOM
	chmod 755 phantomdevicedrivers-4.2/./etc
	chmod 755 phantomdevicedrivers-4.2/./etc/SensAble
	chown 0:0 phantomdevicedrivers-4.2//etc/SensAble/PHANToMDeviceDrivers
	chmod 755 phantomdevicedrivers-4.2//etc/SensAble/PHANToMDeviceDrivers
	chown 0:0 phantomdevicedrivers-4.2//usr/lib/libPHANToMIO.so.4.2
	chmod 755 phantomdevicedrivers-4.2//usr/lib/libPHANToMIO.so.4.2
	chown 0:0 phantomdevicedrivers-4.2//usr/sbin/PHANToMConfiguration
	chmod 4755 phantomdevicedrivers-4.2//usr/sbin/PHANToMConfiguration
	chown 0:0 phantomdevicedrivers-4.2//usr/sbin/PHANToMTest
	chmod 4755 phantomdevicedrivers-4.2//usr/sbin/PHANToMTest
	chown 0:0 phantomdevicedrivers-4.2//usr/sbin/devid
	chmod 755 phantomdevicedrivers-4.2//usr/sbin/devid
	chown 0:0 phantomdevicedrivers-4.2//usr/sbin/hload
	chmod 4755 phantomdevicedrivers-4.2//usr/sbin/hload
	chown 0:0 phantomdevicedrivers-4.2//usr/share/PHANTOM/doc
	chmod 755 phantomdevicedrivers-4.2//usr/share/PHANTOM/doc
	chown 0:0 phantomdevicedrivers-4.2//usr/share/PHANTOM/doc/HW_userguide_Linux.pdf
	chmod 644 phantomdevicedrivers-4.2//usr/share/PHANTOM/doc/HW_userguide_Linux.pdf
	mkdir phantomdevicedrivers-4.2/debian
	date -R
Wed, 23 Feb 2011 09:53:11 +0100

	date -R
Wed, 23 Feb 2011 09:53:11 +0100

	chmod 755 phantomdevicedrivers-4.2/debian/rules
	debian/rules binary 2>&1
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: No packages to build.
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb

phantomdevicedrivers_4.2-3_i386.deb generated
	find phantomdevicedrivers-4.2 -type d -exec chmod 755 {} ;
	rm -rf phantomdevicedrivers-4.2

```

I do not see any error message ...

---

### Post by anglican on 2011-02-23
> **LonelyStar said:**
> Hey,

Thanks for the reply. The output:

```


sudo alien phantomdevicedrivers-4.3-1.i686.rpm --scripts --veryverbose
    ... snip

```I do not see any error message ...No, neither do I... very odd. Perhaps if you try the "--generate" option to create the temporary directory to build the package in then "debian/rules binary" to build the package, you might have more success. BTW which directory are you running alien in... and have you checked for the package in the parent directory?

H

---

### Post by LonelyStar on 2011-02-23
Hey,

I am running alien in ~/Phantom (a directory I created for the purpose). There is no deb in the parent directory. I also have searched for it using find in /.

Running alien with generate produced 2 dirctories:
```

phantomdevicedrivers-4.2
phantomdevicedrivers-4.2.orig

```
What I find strange is that the version number is not the same as in the rpm file name.

OK, I go into phantomdevicedrivers-4.2 and do:
```

sudo debian/rules binary
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: No packages to build.
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb

```

where is the file supposed to be created? I thing it is not working, because I can not find it ...

Regards,
Nathan

---

### Post by kabel_kabel on 2011-03-01
I'm experiencing the same problem, in my case i'm trying to install lotus notes that is packaged in rpm package. Here is my command:

```
sudo alien -d -k --scripts --veryverbose ibm_lotus_notes-8.5.i586.rpm
```

and no deb as output. When i try to add -t switch:

```
sudo alien -d -k -t --scripts --veryverbose ibm_lotus_notes-8.5.i586.rpm
```

as an output i'm getting ibm_lotus_notes-8.5.i586.tgz, but no deb package.

If i do the following:

```
sudo alien -i -d -k --scripts --veryverbose ibm_lotus_notes-8.5.i586.rpm
```

i get the following output:

```
......
	date -R
Tue, 01 Mar 2011 22:21:09 -0600

	chmod 755 ibm_lotus_notes-8.5/debian/rules
	debian/rules binary 2>&1
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: No packages to build.
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb

	dpkg --no-force-overwrite -i ibm-lotus-notes_8.5-20081211.1925_i386.deb
dpkg: error processing ibm-lotus-notes_8.5-20081211.1925_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ibm-lotus-notes_8.5-20081211.1925_i386.deb
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <GETPERMS> line 9624.
	find ibm_lotus_notes-8.5 -type d -exec chmod 755 {} ;
	rm -rf ibm_lotus_notes-8.5
```

which indeed confirms that deb is not being produced.

Does somebody knows where we should file this bug, i mean who is the maintainer of this utility (alien)?

Thanks,
Kabel

---

### Post by sambrightman on 2011-03-06
I filed [bug 730236]("https://bugs.launchpad.net/ubuntu/+source/alien/+bug/730236"), as I have the same problem building something else.

---

