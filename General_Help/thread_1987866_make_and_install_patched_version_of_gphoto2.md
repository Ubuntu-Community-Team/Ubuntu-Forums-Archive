---
title: "make and install patched version of gphoto2"
date: 2012-05-26
forum: General Help
---

### Post by BandD on 2012-05-26
I was given  a link to this patch [(http://gphoto.svn.sourceforge.net/viewvc/gphoto/branches/libgphoto2-2_4/libgphoto2/camlibs/ptp2/library.c?r1=14007&r2=14020&pathrev=14020)]("http://gphoto.svn.sourceforge.net/viewvc/gphoto/branches/libgphoto2-2_4/libgphoto2/camlibs/ptp2/library.c?r1=14007&r2=14020&pathrev=14020") for gphoto2 to fix an issue with Shotwell not being able to display image previews in import mode. But I don't know exactly how to patch it to the current version of gphoto and then install that patched version.

Here's the bug report[ https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/986676]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/986676") 

I'm very comfortable with the command line and have used make & make install before...

---

### Post by csiko on 2012-09-12
I have exactly the same issue on Ubuntu 12.04 amd64: shotwell fails to show preview images with my Canon EOS 1100D connected.
 
I tried to get the newest package of libghoto2 via apt-get but the newest package is version 2.4.13:
[http://www.ubuntuupdates.org/package/core/precise/main/updates/libgphoto2](http://www.ubuntuupdates.org/package/core/precise/main/updates/libgphoto2)

According to the gphoto homepage [http://www.gphoto.org/](http://www.gphoto.org/) , the newest version is 2.5.0.

How should I install the new libgphoto2 without messing up with Ubuntu's package management system?

---

### Post by eric-yorba on 2012-09-12
> **csiko said:**
> According to the gphoto homepage [http://www.gphoto.org/](http://www.gphoto.org/) , the newest version is 2.5.0.

Be warned that GPhoto 2.5 won't work with existing applications out of the box; as the release notes mention, the ABI has changed.

That said, if you build Shotwell from git master today it will work with GPhoto 2.5.

---

### Post by csiko on 2012-09-12
> **eric-yorba said:**
> Be warned that GPhoto 2.5 won't work with existing applications out of the box; as the release notes mention, the ABI has changed.

That said, if you build Shotwell from git master today it will work with GPhoto 2.5.

Thanks for the warning. In order to keep work at a minimum level, I decided to stick with the current version 2.4.13 and just patch the file. And - after some trial and error - I succeeded!

I did the following (this was the first time ever I built a package, comments are welcome):

getting the package source
```
apt-get source libgphoto2-2
``````
cd libgphoto2-2.4.13
```patching file camlibs/ptp2/library.c (see [http://gphoto.svn.sourceforge.net/viewvc/gphoto/branches/libgphoto2-2_4/libgphoto2/camlibs/ptp2/library.c?r1=14007&r2=14020&pathrev=14020](http://gphoto.svn.sourceforge.net/viewvc/gphoto/branches/libgphoto2-2_4/libgphoto2/camlibs/ptp2/library.c?r1=14007&r2=14020&pathrev=14020) for the patch)

Renaming the package description
```
dch -l local 'My patched version of libgphoto2-2'
```Commiting my changes
```
dpkg-source --commit
```Building it (this took some time)
```
debuild -us -uc
```Installing the package
```
dpkg -i ../libgphoto2-2_2.4.13-1ubuntu1.2local1_amd64.deb
```shotwell is now able to show the thumbnail preview when the camera is connected and the import function is working now (although the "hide previously imported pics" function seems not to work).

---

### Post by eric-yorba on 2012-09-12
> **csiko said:**
> shotwell is now able to show the thumbnail preview when the camera is connected and the import function is working now (although the "hide previously imported pics" function seems not to work).

Great to hear you got this working!

As for the "hide previously imported" issue, did you import the photos in question when they did not have previews?

I ask because it sounds likely, and because that's a limitation of the feature.  It knows whether or not a photo was imported previously based on a hash of the preview image.

That said, after the photo is imported it should detect any duplicates.

---

