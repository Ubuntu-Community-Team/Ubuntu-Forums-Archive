---
title: "Having trouble uploading two packages to Launchpad"
date: 2011-06-15
forum: General Help
---

### Post by inameiname on 2011-06-15
Using the method below, I am able to correctly upload packages (both source files and repackaging of already-made debian files) to Launchpad. Unfortunately, two packages never seem to work (either failing, or not fully uploading): gtk-jzintv and pygtranslator. 

```

    1. PPA OpenPGP key setup if not already done
    2. Create a package directory named: ${PACKAGENAME}-${VERSION}~${YOURUNIQUEVERSIONNAME}
    3. Create a subdirectory in the package directory, named: ${PACKAGENAME}
    4. Create subdirectories and files in the subdirectory of the package directory. (Ie, if want /usr/bin/footool, "mkdir usr", "mkdir usr/bin" and "cp footool usr/bin").
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

```gtk-jzintv is too big to upload here, but here is a link to a copy of it. Sadly, I was not able to find a source.tar.gz for it, so only the debian is there to work with: [http://gnome-look.org/content/show.php/gtk-jzintv++%28Intellivision+Emulator%29?content=141124]("http://gnome-look.org/content/show.php/gtk-jzintv++%28Intellivision+Emulator%29?content=141124")

pygtranslator is below, both the debian version I use, and the only source.tar.gz that I could find for it.

gtk-jzintv always seems to fail to build, no matter what I do, and pygtranslator sometimes builds just fine, but upon further review of the debian package on there, it's missing things, namely the juice of the package. Often, only the '/usr/share/docs/*' stuff is there, not the actual program/package stuff.

If anybody has any suggestions, please let me know.

---

### Post by inameiname on 2011-06-18
While this doesn't work for all packages, and I still get some that  won't upload, no matter what I do, such as the latest Bleachbit, this is  how I fixed those few files:

For nautilus-kill-thumbs and nautilus-kill-metamac, to which I had issues prior to the ones regarding these two packages, I simply compressed  the files: /usr/lib/nautilus/extensions-2.0/libnautilus-kill-thumbs.so  and 'libnautilus-kill-metamac.so' in each and set a postinst script to  have it untarred after installed since  /usr/lib/nautilus/extensions-2.0/libnautilus-kill-thumbs.so (and  'libnautilus-kill-metamac.so' respectively) wouldn't go into it. Its  very weird way to do it, I know, but it works just fine.

For gtk-jzintv, I got rid of some of the excess stuff inside the  original deb (the creator it didn't make it very well, but no big deal),  and using the idea from those first two above, compressed the one  folder and one 'exe' (which exes were causing errors just like '*.so'  files in other two), and used a postinst script to untar them  afterwards. Again, good enough.

Finally, for pygtranslator, I realized the original debian package had  put the pygtranslator python script inside /usr/local/bin, and when  Launchpad tried to remake it on their servers, an error came up because  of the folder /usr/local. Therefore, I just changed it to be put in  /usr/bin/, just as all the other apps, and that worked just fine. 

Since I figured these out, and sort of have a grasp on this, even though its not 100 percent, I'll mark this as solved.

---

