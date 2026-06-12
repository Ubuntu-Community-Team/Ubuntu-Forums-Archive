---
title: "Debianizing nmap 5.35"
date: 2010-10-08
forum: General Help
---

### Post by RageLtMan on 2010-10-08
I'm trying to make deb packages from the nmap5.35DC sources, and in order to cheat i've pulled the debian directory from the source package in the repos. However, dpkg-buildpackage fails with the following. Using alien to convert the RPMs causes nmap to crash on DNS resolution so this seems to be the better approach. Anyone try this yet? Has anyone seen this error?


dh_installchangelogs CHANGELOG
dh_movefiles
dh_movefiles: debian/tmp/usr/share/nmap/scripts/smb-pwdump.nse not found (supposed to put it in nmap)
dh_movefiles: debian/tmp/usr/share/zenmap/pixmaps/splash.png not found (supposed to put it in zenmap)
make[1]: *** [binary-common] Error 1
make[1]: Leaving directory `/mnt/build/nmap/src/nmap-5.35DC1'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2

---

### Post by mc4man on 2010-10-08
whether you're taking best approach can't say - never used nmap ect.

inside of your debian folder will be some .files that are similar to .install files.

So if something isn't found, ex. - 
"debian/tmp/usr/share/nmap/scripts/smb-pwdump.nse not found " then find that item in nmaps.file and comment it out

(conversely if something was shown as being in ../tmp/... but no place to 'go' then you'd need to add

---

### Post by RageLtMan on 2010-10-10
Thank you much, removed the two lines from the appropriate .files. Since this build creates new files, new NSE plugins, etc, is there a way to check if there are files that are created which it might not be including in the final package? Should i be concerned that the .files are now missing something created by the updated source code?

---

