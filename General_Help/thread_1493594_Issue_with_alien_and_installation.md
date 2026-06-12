---
title: "Issue with alien and installation"
date: 2010-05-26
forum: General Help
---

### Post by qyot27 on 2010-05-26
I want to use [darwinx](http://lists.fedoraproject.org/pipermail/mingw/2009-July/001832.html) ([repo link](http://build2.openftd.org/darwinx/)) with Ubuntu 10.04 64-bit, rather than having to rely on Fedora 11, so I'm trying to use alien to convert the relevant RPMs to DEBs and install them.  The necessary ones that I know of are:

darwinx-filesystem (used: darwinx-filesystem-13-1.fc11.noarch.rpm)
darwinx-odcctools (used: darwinx-odcctools-691.1-0.20090617.12.fc11.x86_64.rpm)
darwinx-gcc (used: darwinx-gcc-5646-9.fc11.x86_64.rpm)
darwinx-libstdcxx (used: darwinx-libstdcxx-39-3.fc11.noarch.rpm)
darwinx-sdk-leopard (used: darwinx-sdk-leopard-312_2621-14.fc11.noarch.rpm)

alien can convert and install the first four without any issues, but the SDK fails.  The error is below:
```
qyot27@ubuntu:~$ sudo alien darwinx-sdk-leopard-312_2621-14.fc11.noarch.rpm
error: incorrect format: unknown tag
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
		xargs -0 -r -i cp -a {} debian/darwinx-sdk-leopard
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_md5sums: Compatibility levels before 5 are deprecated.
dh_builddeb
dh_builddeb: Compatibility levels before 5 are deprecated.
dpkg-deb - error: (upstream) version (`unknown') doesn't contain any digits
dpkg-deb: 1 errors in control file
dh_builddeb: dpkg-deb --build debian/darwinx-sdk-leopard .. returned exit code 2
make: *** [binary-arch] Error 9
find: `darwinx-sdk-leopard-312_2621': No such file or directory
qyot27@ubuntu:~$ 
```
[On Launchpad](https://bugs.launchpad.net/ubuntu/+source/gcc-4.4/+bug/433115), there's an entry concerning darwinx, and the poster mentioned that they got it to install on 8.04 by using alien to convert them to .tgz first, but declines to mention whether they converted the source RPMs or the binary ones, nor any additional steps taken to make the install work.

Without the SDK, I get the 'No working C compiler found' error because I'm thinking the SDK is where all the header files for the cross-compiler are.

---

### Post by dino99 on 2010-05-26
[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7834625](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7834625)

[http://www.howtoforge.com/apples-darwin-streaming-server-on-centos-5.2](http://www.howtoforge.com/apples-darwin-streaming-server-on-centos-5.2)

[COLOR="Blue"]http://www.clusterlabs.org/wiki/Install[/COLOR]

---

### Post by qyot27 on 2010-05-26
I know how to use alien's help, but that error has me stumped, which is why I included it - directing me to the wiki page that is meant for basic use doesn't solve that or point me in the right direction to troubleshooting it properly.  Darwin Streaming Server is completely irrelevant to cross-compiling software for OSX on Linux (which is what darwinx is, much like mingw32 is for Windows cross-compilation; heck, it's Fedora's mingw team that manages darwinx), and I have no idea what that last link is for.

Forgive me for being terse, but I'm failing to see what I was supposed to draw from those.

---

### Post by dino99 on 2010-05-26
> **qyot27 said:**
> I know how to use alien's help, but that error has me stumped, which is why I included it - directing me to the wiki page that is meant for basic use doesn't solve that or point me in the right direction to troubleshooting it properly.  Darwin Streaming Server is completely irrelevant to cross-compiling software for OSX on Linux (which is what darwinx is, much like mingw32 is for Windows cross-compilation; heck, it's Fedora's mingw team that manages darwinx), and I have no idea what that last link is for.

Forgive me for being terse, but I'm failing to see what I was supposed to draw from those.

yeah you need to understand the spirit of these links and not followed them blindly, as you might know most of errors are between chair and keyboard

*** sudo alien darwinx-sdk-[COLOR="Red"]leopard[/COLOR]-312_2621-14.fc11.noarch.rpm  ***

---

### Post by qyot27 on 2010-05-26
You're still making no sense to me whatsoever, because the aforementioned links still have A) nothing to do with alien or cross-compiling, and B) nothing to do with Ubuntu or any of this process.  The only thing I *can* draw from it is you pointing the finger at me for it failing when I'm unsure you even understood the intent of what I asked in the first post, and still not elaborating on what you think I should be taking away from them, aside from insinuating it being a user error.

_To make myself abundantly clear:_
I am not asking how to use alien.
I am not asking anything about media streaming, or anything at all to do with media.
I am not asking anything about Fedora/CentOS.
Nothing about what I am asking involves an actual machine running OSX, in whole or in part.
I am not asking how to install or compile software.

I **am** asking what I need to do to resolve the *specific* problem that caused alien to fail when processing that particular .rpm, as evidenced in the error log I also posted, something that still has not been addressed at all.  I said in my original post that the first four packages had no problems getting converted to .deb and installing.  There is also nothing wrong with 'leopard' being in the .rpm's filename, as the SDK that darwinx has to rely on is OSX 10.5 Leopard's (as evidenced by the cross-compile targets i686/x86_64-apple-darwin**9** that get used for the task when darwinx is working properly; Darwin 9 is Leopard's base version, as far as any of this is concerned, thus it makes total sense for 'leopard' to be in the filename).

You want everything I did laid out?  Here.
```
wget http://build2.openftd.org/darwinx/darwinx-filesystem-13-1.fc11.noarch.rpm
wget http://build2.openftd.org/darwinx/darwinx-libstdcxx-39-3.fc11.noarch.rpm
wget http://build2.openftd.org/darwinx/darwinx-odcctools-691.1-0.20090617.12.fc11.x86_64.rpm
wget http://build2.openftd.org/darwinx/darwinx-gcc-5646-9.fc11.x86_64.rpm
wget http://build2.openftd.org/darwinx/darwinx-sdk-leopard-312_2621-14.fc11.noarch.rpm
sudo alien -i *.rpm
```
I left no room for spelling errors or mismatched alien opts.  After the SDK failed with the defaults, I also tried converting it to .tgz with the -t option, but yet again it failed because of sbin errors or something like that (I didn't save the .tgz errors).  I even grabbed the source RPM and tried to convert that, but again no dice.  I tried again (which the error log shows) to convert to .deb *without* installing, but the error is in the conversion process.

---

### Post by Ashkan_s on 2010-07-14
Hi

I had the same problem (with another rpm package).

First I converted it to .tgz using:
```
sudo alien -kt --scripts <package.rpm>
``` 

Then I converted it to .deb using:
```
sudo alien --scripts --version=i386 <package.tgz>
```

Actually at fisrt time I used:
```
sudo alien -k --scripts --version=i386 <package.tgz>
```
But it doesn't mean using both -k and --version at the same time.

I am using alien 8.81

---

