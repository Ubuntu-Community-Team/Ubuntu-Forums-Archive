---
title: "Dell Inspiron 14 Trackpad Darts about While Typing"
date: 2011-10-14
forum: General Help
---

### Post by jamesisin on 2011-10-14
I built a laptop for my girlfriend for graduate school.  It's running 10.04 and all seems well enough except the trackpad is a bit touchy.  While typing the mouse might flit about the screen which causes issues with data entry.  Is there a way to deal with this?

Dell Inspiron 14 or N4030 is the laptop.

Thanks.

(Also it doesn't have scrolling and I'm wondering if that's something that can be set up without too much pain.)

---

### Post by jamesisin on 2011-11-08
So since no one has offered any suggestions on how I might fix this I decided I'd just disable the track pad while typing.  Sounds good, right?

Well, on her machine there is no Trackpad tab on her Mouse Preferences dialog.  What's up with that?  She's using the same version this laptop I'm on now is (10.04) and I have one.

---

### Post by Rodney9 on 2011-11-08
You could try > gpointing-device-settings you can install it through the Software Center and / or Synaptic. 

GUI tool for setting pointing devices. Currently it can configure mouse type
device (mouse, trackpoint etc.) and touchpads.

For mouse you can configure middle button emulation, wheel emulation and
scrolling.

It can enable and disable touchpad, or scrolling on it as well as additional
parameters like palm detection, locked drags, tapping and scrolling.

It is a successor of GSynaptics.

---

### Post by jamesisin on 2011-11-11
Rodney9 - Thanks.  That looks to be a very robust utility.  Unfortunately it has the same problem.  It also thinks the trackpad is a PS2 mouse.

---

### Post by jamesisin on 2012-02-28
C'mon; she's threatening to buy a Mac.  Help a brother out here.

---

### Post by ubuntu-freak on 2012-03-21
Have you tried the latest version of Ubuntu? For better hardware support and such. Also, there is now a native option to disable the touchpad while typing. I suggest you uncheck that option before attempting to play any games which require simultaneous use of the touchpad and keyboard, however.

---

### Post by peter d on 2012-03-21
I believe the laptop you have may well have an ALPS touchpad. I have one too on my Dell and didn't have the touchpad tab in Mouse and Touchpad settings. I installed psmouse-alps-dkms which solved the problem.

You can get it here [http://people.canonical.com/~sforshe...s_0.10_all.deb](http://people.canonical.com/~sforshe...s_0.10_all.deb)

I guess this only works with ALPS Glidepoint touchpads. Hope it works.

---

### Post by aeronutt on 2012-03-21
> **peter d said:**
> I believe the laptop you have may well have an ALPS touchpad. I have one too on my Dell and didn't have the touchpad tab in Mouse and Touchpad settings. I installed psmouse-alps-dkms which solved the problem.

You can get it here [http://people.canonical.com/~sforshe...s_0.10_all.deb](http://people.canonical.com/~sforshe...s_0.10_all.deb)

I guess this only works with ALPS Glidepoint touchpads. Hope it works.

+1, this fixed mine too.  Also, not that I'd strongly recommend a beta load, but 12.04 beta recongnizes my touchpad. (Dell Vostro)

---

### Post by jamesisin on 2012-03-22
> **peter d said:**
> You can get it here [http://people.canonical.com/~sforshe...s_0.10_all.deb](http://people.canonical.com/~sforshe...s_0.10_all.deb)



Thanks.  Your link is truncated.  Could you offer it again, perhaps in a code box?

---

### Post by jamesisin on 2012-03-22
Never mind.  I sorted it:

[http://people.canonical.com/~sforshee/lp877666/psmouse-alps-dkms/](http://people.canonical.com/~sforshee/lp877666/psmouse-alps-dkms/)

If anyone can point me to a bug report where I can add myself that would be nice too.

---

### Post by jamesisin on 2012-03-22
Not so good I guess:

```
DKMS: ldtarball Completed.
First Installation: checking all kernels...
Building only for 2.6.32-40-generic
Building for architecture i686
Building initial module for 2.6.32-40-generic

Error! Bad return status for module build on kernel: 2.6.32-40-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/psmouse-alps/0.11/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 47, in <module>
    report['SourcePackage'] = apport.packaging.get_source(package)
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 106, in get_source
    if self._apt_pkg(package).installed:
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 66, in _apt_pkg
    raise ValueError, 'package does not exist'
ValueError: package does not exist
dpkg: error processing psmouse-alps-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 psmouse-alps-dkms
```

---

### Post by jamesisin on 2012-03-26
Essentially adding that package did nothing to alter my system.  The track pad is still recognized (incorrectly) as a PS2 mouse.

Anybody else?

---

### Post by jamesisin on 2012-03-31
It appears that this machine does have an ALPS touchpad:

[http://drivers.softpedia.com/get/KEYBOARD-and-MOUSE/ALPS/Dell-Inspiron-N4030-Notebook-Alps-Touchpad-Driver-A01.shtml](http://drivers.softpedia.com/get/KEYBOARD-and-MOUSE/ALPS/Dell-Inspiron-N4030-Notebook-Alps-Touchpad-Driver-A01.shtml)

Since installing the package/driver suggested above I now get an error when running apt-get:

```
Setting up psmouse-alps-dkms (0.11) ...
Removing old psmouse-alps-0.11 DKMS files...

-------- Uninstall Beginning --------
Module:  psmouse-alps
Version: 0.11
Kernel:  3.0.0-14-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 0.11
completely from the DKMS tree.
------------------------------
Done.
Loading new psmouse-alps-0.11 DKMS files...

Loading tarball for module: psmouse-alps / version: 0.11

Creating /var/lib/dkms/psmouse-alps/0.11/source
Copying dkms.conf to /var/lib/dkms/psmouse-alps/0.11/source...
Loading /var/lib/dkms/psmouse-alps/0.11/3.0.0-14-generic/x86_64...

DKMS: ldtarball Completed.
First Installation: checking all kernels...
Building only for 2.6.32-40-generic
Building for architecture i686
Building initial module for 2.6.32-40-generic

Error! Bad return status for module build on kernel: 2.6.32-40-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/psmouse-alps/0.11/build/ for more information.
dpkg: error processing psmouse-alps-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...

Setting up thunderbird (11.0.1+build1-0ubuntu0.10.04.1~mts1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 psmouse-alps-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by jamesisin on 2012-03-31
I added myself to a bug report for this issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662948](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662948)

Still seeking any useful workaround.

---

