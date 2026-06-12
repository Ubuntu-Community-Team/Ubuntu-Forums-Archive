---
title: "Ubuntu 10.04 problems with Skype and Lightning"
date: 2010-07-22
forum: General Help
---

### Post by runningjake on 2010-07-22
I hope it's ok to combine both of my problems in one thread.  For reference, I have a Sony VPCEB2Z1E that is 64 bit.

**Skype**

I've been trying to install skype in Ubuntu 10.04.  I tried multiple different ways to install skype but no matter what I get the same error.  For instance, using this method [http://linux.dipin.info/2010/01/how-to-install-skype-on-ubuntu-1004.html](http://linux.dipin.info/2010/01/how-to-install-skype-on-ubuntu-1004.html).  I also get the error

> dpkg: error processing skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb
It seems like I'm not installing the right version but it's the 64 bit version that I needed, so I'm confused here.

**Lightning**

It took a long time for me to get Thunderbird 3.1 on here but after long last it works thanks to this ([http://ubuntuguide.net/install-thunderbird-3-1-from-ppa-in-64-bit-ubuntu-10-04](http://ubuntuguide.net/install-thunderbird-3-1-from-ppa-in-64-bit-ubuntu-10-04)).  But lightning just won't work.  I downloaded the .xpi's from here: [http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/) . [gdata-provider.xpi]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/gdata-provider.xpi") works just fine but not lightning itself. Here's the error that I'm getting

> "Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86-gcc3). Please contact the author of this item about the problemHowever, from what I understand that's the right link for Thunderbird 3.1 on a 64 bit and it's the most recent that I could find.  If there's another link I'd really appreciate having it!

---

### Post by Jazzy_Jeff on 2010-07-22
Are you sure you installed the 64 bit version of Ubuntu? The 32 bit version will install and run just fine on 64 bit hardware. Try using the 32 bit package and see if it installs.

---

### Post by aeiah on 2010-07-22
both issues are because you're running the 32bit/i386/x86 version of ubuntu. dont worry about it, unless you've got more than 3GB ram

---

### Post by kennedyvelez on 2010-07-22
install the 32 bit package...

---

### Post by runningjake on 2010-07-22
UGH!!! you guys are all right.  Serves me right for trusting DH to give me the right version. Sigh.. Now off to reinstall Ubuntu because I have 4 GB of ram...

No wonder nothing was working today!

---

### Post by runningjake on 2010-07-23
Yep, it was definitely the 64 bit thing.  Everything is working fine!  I'm glad it was just that error...

---

