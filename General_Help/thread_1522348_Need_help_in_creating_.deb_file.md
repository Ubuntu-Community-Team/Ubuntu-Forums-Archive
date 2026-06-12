---
title: "Need help in creating .deb file"
date: 2010-07-02
forum: General Help
---

### Post by debcreate on 2010-07-02
Trying to create deb file from a simple python project. Got the following error for **dpkg-buildpackage **command
i have'nt created any configure file or make file for this project as i m a new bie.
Do i need to create config file or make file????????
[INDENT][SIZE=2]dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/usr/Desktop/package/ubuntu/build-0.2ubuntu9.04'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/usr/Desktop/package/ubuntu/build-0.2ubuntu9.04'
make: *** [clean] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 2
[/SIZE][/INDENT]Thnks for the help

---

