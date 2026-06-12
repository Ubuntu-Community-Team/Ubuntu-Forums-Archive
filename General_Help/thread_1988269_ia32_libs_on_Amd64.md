---
title: "ia32 libs on Amd64"
date: 2012-05-27
forum: General Help
---

### Post by neigun on 2012-05-27
Has anyone had any suuccess installing the ia32 dependencies on an Amd64 system?

I've tried Synaptic,sudo apt-get install -f, Gdebi, Software Centre, etc but all to no avail.

I became aware that it was an issue when trying to install Google Earth 6.2.  The dependencies were installed on 11.10 but when I ugraded my system the packages had been deleted and not substtited with more recent versions.

There has been bug registered about this issue:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761?comments=all](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761?comments=all)

which I have posted to but no resolution as of yet.

Thanks in anticipation Guys,

Neil

---

### Post by Avaritia on 2012-05-27
It's not a bug, ia32 libs is been phased out (and should have never been used in the first place IMHO)

To install a 32 bit package add i386 to the packages name, like if you want 32 bit firefox you would do:

```
sudo apt-get install firefox:i386
```

---

### Post by MonkeyPaw on 2012-05-27
Odd, I have successfully installed ia32-libs several times on AMD64 machines through the software center. I need it because of an Adobe AIR application. Google Earth has a 64bit deb to install. If it is failing to launch, it might be an OpenGL issue.

---

### Post by neigun on 2012-05-27
> **Avaritia said:**
> It's not a bug, ia32 libs is been phased out (and should have never been used in the first place IMHO)

To install a 32 bit package add i386 to the packages name, like if you want 32 bit firefox you would do:

```
sudo apt-get install firefox:i386
```

Avaritia

I should have said it was a 64 bit version of Google Earth with what appears to be 32 bit dependencies included. 

Check out the link in my previous posting.  It is logged as a bug as some packages still require the associated dependencies.  I believe Skype is another package that has these sorts of issues.

Neil

---

### Post by oldos2er on 2012-05-27
In 12.04, ia32-libs is a transitional package, it should give you what you need to run Google Earth.

---

### Post by neigun on 2012-05-27
Thanks Ann I've tried installing the transitional package from both the command line and Synaptic but it still throws up an error message.

Neil

---

### Post by neigun on 2012-05-27
I'm now on my own machine.  This the error message which results when I use Gdebi to try and install Google Earth 6.2 64 bit:


(Reading database ... 211649 files and directories currently installed.)
Unpacking libqtcore4:i386 (from .../libqtcore4_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.1_i386.deb (--unpack):
 conffile './etc/xdg/Trolltech.conf' is not in sync with other instances of the same package
No apport report written because MaxReports has already been reached
                                                                    Selecting previously unselected package libqt4-xml:i386.
Unpacking libqt4-xml:i386 (from .../libqt4-xml_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-dbus:i386.
Unpacking libqt4-dbus:i386 (from .../libqt4-dbus_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-network:i386.
Unpacking libqt4-network:i386 (from .../libqt4-network_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-script:i386.
Unpacking libqt4-script:i386 (from .../libqt4-script_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-sql:i386.
Unpacking libqt4-sql:i386 (from .../libqt4-sql_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-xmlpatterns:i386.
Unpacking libqt4-xmlpatterns:i386 (from .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqtgui4:i386.
Unpacking libqtgui4:i386 (from .../libqtgui4_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-declarative:i386.
Unpacking libqt4-declarative:i386 (from .../libqt4-declarative_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-designer:i386.
Unpacking libqt4-designer:i386 (from .../libqt4-designer_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-opengl:i386.
Unpacking libqt4-opengl:i386 (from .../libqt4-opengl_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-qt3support:i386.
Unpacking libqt4-qt3support:i386 (from .../libqt4-qt3support_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-scripttools:i386.
Unpacking libqt4-scripttools:i386 (from .../libqt4-scripttools_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-sql-mysql:i386.
Unpacking libqt4-sql-mysql:i386 (from .../libqt4-sql-mysql_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-svg:i386.
Unpacking libqt4-svg:i386 (from .../libqt4-svg_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqt4-test:i386.
Unpacking libqt4-test:i386 (from .../libqt4-test_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libqtwebkit4:i386.
Unpacking libqtwebkit4:i386 (from .../libqtwebkit4_2.2.1-1ubuntu4_i386.deb) ...
Selecting previously unselected package ia32-libs-multiarch:i386.
Unpacking ia32-libs-multiarch:i386 (from .../ia32-libs-multiarch_20090808ubuntu36_i386.deb) ...
Selecting previously unselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_20090808ubuntu36_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.1_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by neigun on 2012-05-27
How did this spam get through?  

I've now removed the links as unfortunately it wasn't removed when the spam was.

---

### Post by neigun on 2012-07-01
Well a clean install resolved that issue- The install was necessary due to my tweaking ;)

Thanks for all the advice.  Must have been some conflict with dependencies ironically.

Neil

---

