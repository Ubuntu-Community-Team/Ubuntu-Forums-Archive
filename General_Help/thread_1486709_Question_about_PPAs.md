---
title: "Question about PPAs"
date: 2010-05-18
forum: General Help
---

### Post by inameiname on 2010-05-18
Firstly, my goal/intention is to have a way to upload, and keep uploading, the most recent Deb files of several Apps which have older versions in the official channels, so as those I know can simply add my PPA or link to their sources.list and get updated. 

However, having never created my own PPA before, I noticed it doesn't allow Deb uploads, nor according to this: "We will not accept uploads of packages that are unmodified from their  original source in Ubuntu or Debian, only packages that include your own  changes," I can't upload anything unless I personally make it from source. 

Finally, my question is if anybody knows of a way I can create an online source, like a PPA (or a PPA, if I am mistaken with the how to), so I can share the more updated versions of Deb packages that I find, regardless of if I personally build them?

---

### Post by inameiname on 2011-06-18
This is an old thread, and I have recently figured out how to just us Launchpad and create my own PPA. Actually was able to figure out how to repackage debian packages I have into source files for Launchpad upload and evental repacking of debian packages on it.

I used this method, and for the most part (few exceptions, it works just fine):

```

Debian package creation and Launchpad PPA use:


PPA OpenPGP key setup (only needed for Launchpad PPA use) (OpenPGP key in PPA must match the one on the computer before making debian package)
    Generate new key
        Open Passwords and Encryption Keys. Select File > New, select PGP Key and then follow the on-screen instructions.
        ...OR...
        gpg --gen-key
    Publish new key to Ubuntu keyserver
        Open Passwords and Encryption Keys. Select My Personal Keys tab, and your key. Select Remote > Sync and Publish Keys, and Sync button.
        Select the key server hkp://keyserver.ubuntu.com (Add it if its not there.)
        ...OR...
        gpg --keyserver hkp://keyserver.ubuntu.com --send-keys
    Import an OpenPGP key
        Open Passwords and Encryption Keys. Select My Personal Keys tab, and your key. Select/copy Fingerprint text (ten blocks of numbers/letters).
        ...OR...
        gpg --fingerprint
        ...once have, put in the appropriate section on Launchpad.net to start verification process...
    Verify new key
        Copy/paste email message received upon import of OpenPGP key from "-----BEGIN PGP MESSAGE-----" till "-----END PGP MESSAGE-----" to file.txt
        gpg -d file.txt (You will be asked to enter your passphrase and you get the decrypted message.)

    List new key (Public and Private keys)
        Public:
            gpg --list-keys
        Private:
            gpg --list-secret-keys
    Backup new key (Public and Private keys)
        Using the above commands to list your public and private keys:
        Public:
            Look for line that starts something like "pub 1024D/". The part after 1024D is key_id. To export key:
            gpg -ao text-public.key --export key_id
        Private:
            Look for line that starts something like "sec 1024D/". The part after 1024D is key_id. To export secret key:
            gpg -ao text-private.key --export-secret-keys key_id
    Restore old keys (Public and Private keys) (instead of doing all of the above to generate new ones if for instance you redo your computer)
        To restore your keys, copy the two files created above to the machine and type:
        Public:
            gpg --import text-public.key
        Private:
            gpg --import text-private.key


Basic example of a control file:
    Package: Space-sunrise
    Source: plymouth
    Version: 1.0
    Architecture: all
    Maintainer: Andre "Osku" Schmidt
    Installed-Size: 444
    Depends: plymouth, plymouth-label
    Replaces: plymouth (<< 0.8.1-1~)
    Provides: plymouth-theme
    Section: x11
    Priority: optional
    Description: Plymouth theme for Ubuntu >= 10.04 & Linux Mint >= 9


Debian package creation options:

Option #1 (from scratch, without the source code OR are just remaking current deb file, such as for changing version number, the right way) (needs build-essential autoconf automake autotools-dev dh-make debhelper devscripts dput fakeroot xutils lintian pbuilder):
    1. PPA OpenPGP key setup above
    2. Create a package directory named: ${PACKAGENAME}-${VERSION}~${YOURUNIQUEVERSIONNAME}
    3. Create a subdirectory in the package directory, named: ${PACKAGENAME}
    4. Create subdirectories/files in a subdirect of package direct. (if want /usr/bin/footool, "mkdir usr", "mkdir usr/bin" and "cp footool usr/bin").
       If using a current deb file, just copy all its subdirectories into ${PACKAGENAME}, excluding its DEBIAN subdirectory (leave for later)
    5. Compress the package directory into a tar.gz file, rename it: ${PACKAGENAME}_${VERSION}~${YOURUNIQUEVERSIONNAME}.orig.tar.gz
    6. cd /path/to/package directory
    7. dh_make -n -s -e your@emailaddress.com # this will create the DEBIAN subdirectory for the new deb being made
    8. dpkg-depcheck -d ./configure    # find dependencies, and once found, add to section in subdirectory DEBIAN/control in the package directory
    9. Edit changelog, copyright, control, rules, manpage (if want to adhere to policy, ensure name & email are = what's on record for your gpp key)
       Also be sure to change 'unstable' to the correct '${UBUNTUVERSION}'
       If using a current deb file, ensure the original DEBIAN subdirectory contents are put into the new 'DEBIAN' subdirectory
       If using a current deb file/making your own, create a debian/${PACKAGENAME}.install file, make it executable, and add the following:
        #!/usr/bin/make -f
        # add more lines like below when necessary
        <put_whatever_dirctory(s)_here>/ /
    10. debuild (is a wrapper which approx. equals: dpkg-buildpackage + lintian or linda + debsign) (choose one: 'debuild -S' is Launchpad-friendly)
        debuild # requires sig, builds tar.gz & deb, creates .changes & build files (rejected on Launchpad: must be source only to work)
        debuild -S    # requires sig, builds tar.gz, creates .changes & .build files (accepted on Launchpad: but not perfect)
        debuild -b # requires sig, builds deb, creates .changes & .build files (rejected on Launchpad: missing tar.gz)
        debuild -i -us -uc -S # no sig required, builds tar.gz, creates .changes & .build files (rejected on Launchpad due to missing sig)
        debuild -i -us -uc -b # no sig required, builds deb, creates .changes & .build files (rejected on Launchpad: missing tar.gz/sig.)
        dpkg-buildpackage -rfakeroot # requires sig, builds tar.gz & deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc # no sig required, builds tar.gz & deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -S # requires sign, builds tar.gz, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc -S # no sig required, builds tar.gz, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -b # requires sig, builds deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc -b # no sig required, builds deb, creates .changes, no .build (rejected on Launchpad)
        fakeroot debian/rules clean && fakeroot debian/rules binary # builds deb only
        lintian -Ivi ../yourpackage.changes # optional, to check the new deb package
    11. dput ppa:<yourppausername>/<yourppaname> <package.changes>    # optional, to upload to a Launchpad PPA

Option #2 (from source code (source tar file), the right way) (needs build-essential autoconf automake autotools-dev dh-make debhelper devscripts dput fakeroot xutils lintian pbuilder):
    1. PPA OpenPGP key setup above
    2. tar xvf sourcefilesarchive.tar.gz
    3. cd /path/to/extracted/sourcefiles
    4. Do steps 7-12 above

```

As such, I'll mark this as solved.

---

