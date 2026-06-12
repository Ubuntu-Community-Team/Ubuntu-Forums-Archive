---
title: "Trouble building barry 0.16 &amp; friends on x86_64"
date: 2010-01-11
forum: General Help
---

### Post by digitijit on 2010-01-11
Has barry 0.16 been built and used successfully under Ubuntu 9.10 running on the x86_64 architecture? 

I have tried and failed.   After copying barry_0.16.orig.tar.gz, barry_0.16-0.diff.gz and barry_0.16-0.dsc to my build tree (/usr/local/src/downloads/) and executing

$ dpkg-source -x barry_0.16-0.dsc

to expand the source tree, I have gotten the farthest using

$ DEB_BUILD_OPTIONS="--enable-gui --enable-opensync-plugin --enable-boost" fakeroot debian/rules binary

Eventually during the build I get a long list of warnings like the following:

make[3]: Entering directory `/usr/local/src/downloads/barry-0.16/tools'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/src/downloads/barry-0.16/debian/tmp/usr/local/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'btool' '/usr/local/src/downloads/barry-0.16/debian/tmp/usr/local/bin/btool'
libtool: install: warning: `../src/libbarry.la' has not been installed in `/usr/local/lib'
/usr/bin/install -c .libs/btool /usr/local/src/downloads/barry-0.16/debian/tmp/usr/local/bin/btool
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'bidentify' '/usr/local/src/downloads/barry-0.16/debian/tmp/usr/local/bin/bidentify'
libtool: install: warning: `../src/libbarry.la' has not been installed in `/usr/local/lib'
/usr/bin/install -c .libs/bidentify /usr/local/src/downloads/barry-0.16/debian/tmp/usr/local/bin/bidentify
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'bjavaloader' '/usr/local/src/downloads/barry-0.16/debian/tmp/usr/local/bin/bjavaloader'
...

The build terminates with:

dh_lintian -plibbarry-dev
dh_install -plibbarry-dev 
cp: cannot stat `./debian/tmp/usr/lib/libbarry.a': No such file or directory
dh_install: cp returned exit code 1
make: *** [binary-install/libbarry-dev] Error 1
$

That is, libbarry.la is not being inserted into the source tree and libbarry.a does not get created.  Given that barry 0.16 and friends have been successfully built for several Debian derivatives running on i386 architectures, including Ubuntu 9.04, I am wondering whether this error might be an issue with building on an x86_64 box.  Any suggestions will be much appreciated. 

Cheers,
Digit Ijit

---

