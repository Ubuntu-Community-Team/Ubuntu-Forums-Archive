---
title: "Help installing bank statement decoder"
date: 2010-09-05
forum: General Help
---

### Post by bigseb on 2010-09-05
My bank statement s get delivered via email but they require a special decoder to be read. I got the decoder here [https://www.standardbank.co.za/secure/decoder/securedecoder.html ]("https://www.standardbank.co.za/secure/decoder/securedecoder.html")(the gui version), extracted it and tried to install it but the terminal gives me the following message:

 bigseb@bigseb-laptop:~/Documents/reader$ sudo rpm -i /striata-reader-1.0-27-linux-2.4-intel
rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details.
bigseb@bigseb-laptop:~/Documents/reader$

Can anyone help with this?

---

### Post by gandaran on 2010-09-05
> rpm: please use alien to install rpm packages on Debian 
you are trying to install a rpm package in Ubuntu, Ubuntu doesn't use rpm packages but .deb packages, if there isn't a .deb package with that program then do what the message tells you, install ALIEN first from the repositories then use it to convert it to .deb.
you can also install RPM then you can install the .rpm directly but this is not recommended.

---

### Post by bigseb on 2010-09-05
> **gandaran said:**
> you are trying to install a rpm package in Ubuntu, Ubuntu doesn't use rpm packages but .deb packages, if there isn't a .deb package with that program then do what the message tells you, install ALIEN first from the repositories then use it to convert it to .deb.
you can also install RPM then you can install the .rpm directly but this is not recommended.
Installed rpm via synaptic but still doesn't work. will try Alien. Thanks

---

### Post by bigseb on 2010-09-05
> **bigseb said:**
> Installed rpm via synaptic but still doesn't work. will try Alien. Thanks
Installed Alien... and now? 

Terminal:

bigseb@bigseb-laptop:~$ sudo alien ~/Documents/reader/striata-reader-1.0-27-linux-2.4-intel.rpm
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package striata-reader: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/striata-reader
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: error: couldn't find library libkio.so.4 needed by debian/striata-reader/usr/local/Striata/reader/kdeopen (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps -Tdebian/striata-reader.substvars debian/striata-reader/usr/local/Striata/reader/gnomeopen debian/striata-reader/usr/local/Striata/reader/striata-reader debian/striata-reader/usr/local/Striata/reader/kdeopen returned exit code 2
make: [binary-arch] Error 9 (ignored)
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/striata-reader.substvars -Pdebian/striata-reader returned exit code 255
make: *** [binary-arch] Error 9
find: `striata-reader-1.0': No such file or directory
bigseb@bigseb-laptop:~$

---

### Post by todak on 2010-09-05
This is the format you need to convert the .rpm to .deb: ```
sudo alien --scripts striata-reader-1.0-27-linux-2.4-intel.rpm
``` It will then convert and you can install it like any other .deb. I converted it myself to verify and it converted with no errors.
The error message: ```
error: incorrect format: unknown tag
``` is nothing to worry about. It merely warns you that the COPYRIGHT package attribute could not be found in the RPM and the alien command tried to retrieve it. You can verify this by executing alien with the additional -v (verbose) switch.

---

### Post by gandaran on 2010-09-05
> **bigseb said:**
> Installed Alien... and now? 

Terminal:

bigseb@bigseb-laptop:~$ sudo alien ~/Documents/reader/striata-reader-1.0-27-linux-2.4-intel.rpm
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package striata-reader: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/striata-reader
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: error: couldn't find library libkio.so.4 needed by debian/striata-reader/usr/local/Striata/reader/kdeopen (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps -Tdebian/striata-reader.substvars debian/striata-reader/usr/local/Striata/reader/gnomeopen debian/striata-reader/usr/local/Striata/reader/striata-reader debian/striata-reader/usr/local/Striata/reader/kdeopen returned exit code 2
make: [binary-arch] Error 9 (ignored)
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/striata-reader.substvars -Pdebian/striata-reader returned exit code 255
make: *** [binary-arch] Error 9
find: `striata-reader-1.0': No such file or directory
bigseb@bigseb-laptop:~$

bigseb

there are to many errors here, it will be very difficult  to install this package, one is about architecture, looks like you are running Ubuntu 64-bits and the package is 32-bits, another I think is this program needs kde libs to run which you haven't if you are using gnome.

---

### Post by bigseb on 2010-09-06
> **gandaran said:**
> bigseb

there are to many errors here, it will be very difficult  to install this package, one is about architecture, looks like you are running Ubuntu 64-bits and the package is 32-bits, another I think is this program needs kde libs to run which you haven't if you are using gnome.
So you're saying it won't work? Ouch!

---

### Post by tbag on 2010-09-06
Hi BigSeb,

Have you tried the Debian version of the Striata Reader?

You can find it here :
[http://www.striata.com/resources/striata-reader/striata-reader-linux-ubuntu-/details.html]("http://www.striata.com/resources/striata-reader/striata-reader-linux-ubuntu-/details.html")

Give it a bash and let me know.

Regards,
Theunis

---

### Post by Ghost_Mazal on 2010-09-06
Hi bigseb , I also get such statements from ABSA bank.
 
I installed striata by getting the deb package from the straita site themselves.
It works fine with me.

---

### Post by bigseb on 2010-09-07
@ tbag and ghost_mazal:

Thanks that worked perfectly. Shot brus!

---

### Post by tbag on 2010-09-07
> **bigseb said:**
> @ tbag and ghost_mazal:
Thanks that worked perfectly. Shot brus!

Pleasure. We (Yes, I work for Striata :p) have also requested that Standard Bank update their site with the latest versions of the Striata Reader. 

Enjoy!

---

