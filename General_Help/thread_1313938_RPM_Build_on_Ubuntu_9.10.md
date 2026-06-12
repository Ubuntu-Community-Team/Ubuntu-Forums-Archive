---
title: "RPM Build on Ubuntu 9.10"
date: 2009-11-04
forum: General Help
---

### Post by Scarfy on 2009-11-04
I just upgraded to Ubuntu 9.10 from 9.04 and RPM build has stopped working for me.

Instead of using /usr/src/rpm it now wants to use $HOME/rpmbuild

I can update my scripts to use that directory, but then a host of other problems occur.

Does anyone know how I can set the buildroot back to /usr/src/rpm, as it always was?

If I do,

**rpmbuild --buildroot /usr/src/rpm program.spec**

the buildroot parameter seems to be being ignored.

It is also ignored if I put it into the spec file itself.

Is there a bug in rpmbuild, because I've never seen this happen before. Is there something in my env that I need to set?

(in case anyone is wondering, I build RPMs and then use Alien to create DEB files).

Thanks,

Steve

---

### Post by Scarfy on 2009-11-04
After looking at this for a few hours, I can only say that rpmbuild appears to be broken under 9.10.

Either that or there have been changes made to the core functionality.

At any rate, the behaviour is completely different to what has been in there for a past few years and now none of my build scripts will work. Paths are being randomly appended and prepended to the file locations, and I have no idea why.

Oh well. People will just have to do with compiling from source, I guess.

---

### Post by hoffman60613 on 2009-11-13
Thanks to Scarfy for the work around.

I uninstalled rpm: **sudo apt-get remove rpm**

Then downloaded the following from **packages.ubuntu.com/januty**:

[LIST]
[*]libbeecrypt6_4.1.2-7_amd64.deb
[*]rpm_4.4.2.3-2ubuntu1_amd64.deb
[*]librpm4.4_4.4.2.3-2ubuntu1_amd64.deb
[/LIST]
If you are using 32bit, obviously substitute i386 for amd64...

Then installed those.  Finally I created a file **/etc/apt/preferences.d/rpm** with these contents to keep it from getting updated:
---- snip ---- snip ---- snip ---- snip ---- snip ----
Package: libbeecrypt6
   Pin: version 4.1.2-7*
   Pin-Priority: 1001

Package: rpm
   Pin: version 4.4.2.3-2ubuntu1*
   Pin-Priority: 1001

Package: librpm4.4
   Pin: version 4.4.2.3-2ubuntu1*
   Pin-Priority: 1001
---- snip ---- snip ---- snip ---- snip ---- snip ----

The rpm package now shows as a 'kept back' package and won't update.

Thanks again!

---

