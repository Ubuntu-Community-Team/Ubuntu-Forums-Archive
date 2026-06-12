---
title: "Unable to install or remove any packages."
date: 2010-12-09
forum: General Help
---

### Post by kanishkdudeja on 2010-12-09
im facing a very serious problem. This error pops up when i try to install/remove any package. Please see the screenshot.

---

### Post by drewsus on 2010-12-09
```
sudo apt-get install -f
```
?

---

### Post by sikander3786 on 2010-12-09
As suggested above, first of all follow these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If these don't fix the issue, seems like the directory /var/cache/debconf is missing. Try creating that.

```
sudo mkdir /var/cache/debconf
```

And again,

```
sudo dpkg --configure -a
```

If errors persist, it'd be better to post the text in your post rather than screenshot. You can copy/paste the text between terminal and your post ;-)

---

### Post by kanishkdudeja on 2010-12-09
i created the debconf directory..

After creating..

kanishk@Inspiron-1525:~$ sudo dpkg --configure -a
Setting up crossplatformui (1.0.38) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart acpid
acpid start/running, process 3029
package libqtgui4 exist
QT_VERSION = 4
Sorry! The usb-serial driver does not support your Linux version.
Sorry! Make usb-serial driver error.
But, it try to use the default driver module.
mv: cannot stat `/usr/local/bin/ztemtApp/ztemt.ko': No such file or directory
dpkg: error processing crossplatformui (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 crossplatformui


kanishk@Inspiron-1525:~$ sudo dpkg --configure -a
Setting up crossplatformui (1.0.38) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart acpid
acpid start/running, process 3029
package libqtgui4 exist
QT_VERSION = 4
Sorry! The usb-serial driver does not support your Linux version.
Sorry! Make usb-serial driver error.
But, it try to use the default driver module.
mv: cannot stat `/usr/local/bin/ztemtApp/ztemt.ko': No such file or directory
dpkg: error processing crossplatformui (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 crossplatformui

---

### Post by karthick87 on 2010-12-09
Run the following,
```
sudo service acpid restart
```

```
sudo dpkg --configure -a
```

---

### Post by sikander3786 on 2010-12-09
So the error is limited to a single package now.

> Errors were encountered while processing:
crossplatformui

Try reinstalling or removing that package.

```
sudo apt-get install --reinstall crossplatformui
```

If errors,

```
sudo apt-get remove --purge crossplatformui
```

Let us know how that goes.

---

### Post by kanishkdudeja on 2010-12-09
@karthik87..

no it still shows the same errors

---

### Post by karthick87 on 2010-12-09
Have you followed @sikander3786 post [#6]("http://ubuntuforums.org/showpost.php?p=10217979&postcount=6").

---

### Post by kanishkdudeja on 2010-12-09
@sikander3876..

kanishk@Inspiron-1525:~$ sudo apt-get install --reinstall crossplatformui
[sudo] password for kanishk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of crossplatformui is not possible, it cannot be downloaded.
The following package was automatically installed and is no longer required:
  discover-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up crossplatformui (1.0.38) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart acpid
acpid start/running, process 2423
package libqtgui4 exist
QT_VERSION = 4
Sorry! The usb-serial driver does not support your Linux version.
Sorry! Make usb-serial driver error.
But, it try to use the default driver module.
mv: cannot stat `/usr/local/bin/ztemtApp/ztemt.ko': No such file or directory
dpkg: error processing crossplatformui (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 crossplatformui

	  You have to configure "localepurge" with the command

	      dpkg-reconfigure localepurge

	  to make /usr/sbin/localepurge actually start to function.

	  Nothing to be done, exiting ...

E: Sub-process /usr/bin/dpkg returned an error code (1)
kanishk@Inspiron-1525:~$ sudo apt-get remove --purge crossplatformui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  discover-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  crossplatformui*
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 173007 files and directories currently installed.)
Removing crossplatformui ...
Purging configuration files for crossplatformui ...
dpkg: warning: while removing crossplatformui, directory '/usr/local' not empty so not removed.
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for python-support ...

it seems to have worked..now shud i reinstall this package..why is this package needed ?

---

### Post by sikander3786 on 2010-12-09
I think it is needed for some USB internet devices.

If you are using one, you can try re-installing the package.

```
sudo apt-get install crossplatformui
```

If everything seems to work fine without that, you might not consider installing that again as there seem to be many problems with that package.

Happy Ubuntu-ing!

---

### Post by kanishkdudeja on 2010-12-09
yeah im using reliance connect broadband. but it seems to work fine without it. n it isnt there in the repostories. so im okay without it..:)

---

### Post by kanishkdudeja on 2010-12-09
thanks guys..:)

---

### Post by lokesh1507 on 2010-12-09
[COLOR=Navy][B]hi all, 
Is there any buddy who can solve my problem?
My problem is same as written above 
Issue:: Unable to install or remove any packages 
Machine configuration: Toshiba L640-X4310
OS: Release 10.10 (Maverick) kernel linux 2.6.35-23-generic gnome 2.32
Error log:
[/B][/COLOR][COLOR=Green]
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Preconfiguring packages ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 145960 files and directories currently installed.) 
Preparing to replace libssl0.9.8 0.9.8o-1ubuntu4.2 (using .../libssl0.9.8_0.9.8o-1ubuntu4.3_i386.deb) ... 
Unpacking replacement libssl0.9.8 ... 
Setting up libssl0.9.8 (0.9.8o-1ubuntu4.3) ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 145960 files and directories currently installed.) 
Preparing to replace libk5crypto3 1.8.1+dfsg-5ubuntu0.1 (using .../libk5crypto3_1.8.1+dfsg-5ubuntu0.2_i386.deb) ... 
Unpacking replacement libk5crypto3 ... 
Preparing to replace libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.1 (using .../libgssapi-krb5-2_1.8.1+dfsg-5ubuntu0.2_i386.deb) ... 
Unpacking replacement libgssapi-krb5-2 ... 
Preparing to replace libkrb5-3 1.8.1+dfsg-5ubuntu0.1 (using .../libkrb5-3_1.8.1+dfsg-5ubuntu0.2_i386.deb) ... 
Unpacking replacement libkrb5-3 ... 
Preparing to replace libkrb5support0 1.8.1+dfsg-5ubuntu0.1 (using .../libkrb5support0_1.8.1+dfsg-5ubuntu0.2_i386.deb) ... 
Unpacking replacement libkrb5support0 ... 
Preparing to replace nautilus-sendto-empathy 2.32.0.1-0ubuntu1 (using .../nautilus-sendto-empathy_2.32.1-0ubuntu1_i386.deb) ... 
Unpacking replacement nautilus-sendto-empathy ... 
Preparing to replace empathy 2.32.0.1-0ubuntu1 (using .../empathy_2.32.1-0ubuntu1_i386.deb) ... 
Unpacking replacement empathy ... 
Preparing to replace empathy-common 2.32.0.1-0ubuntu1 (using .../empathy-common_2.32.1-0ubuntu1_all.deb) ... 
Unpacking replacement empathy-common ... 
Preparing to replace libwvstreams4.6-base 4.6.1-1 (using .../libwvstreams4.6-base_4.6.1-1ubuntu1_i386.deb) ... 
Unpacking replacement libwvstreams4.6-base ... 
Preparing to replace libwvstreams4.6-extras 4.6.1-1 (using .../libwvstreams4.6-extras_4.6.1-1ubuntu1_i386.deb) ... 
Unpacking replacement libwvstreams4.6-extras ... 
Preparing to replace libuniconf4.6 4.6.1-1 (using .../libuniconf4.6_4.6.1-1ubuntu1_i386.deb) ... 
Unpacking replacement libuniconf4.6 ... 
Preparing to replace wvdial 1.60.3 (using .../wvdial_1.60.4_i386.deb) ... 
Unpacking replacement wvdial ... 
Preparing to replace gnome-ppp 0.3.23-1 (using .../gnome-ppp_0.3.23-1ubuntu2_i386.deb) ... 
Unpacking replacement gnome-ppp ... 
Preparing to replace gwibber 2.32.2-0ubuntu1 (using .../gwibber_2.32.2-0ubuntu2_all.deb) ... 
Unpacking replacement gwibber ... 
Preparing to replace gwibber-service 2.32.2-0ubuntu1 (using .../gwibber-service_2.32.2-0ubuntu2_all.deb) ... 
Unpacking replacement gwibber-service ... 
Preparing to replace libibus2 1.3.7-1ubuntu3 (using .../libibus2_1.3.7-1ubuntu4_i386.deb) ... 
Unpacking replacement libibus2 ... 
Preparing to replace ibus 1.3.7-1ubuntu3 (using .../ibus_1.3.7-1ubuntu4_i386.deb) ... 
Unpacking replacement ibus ... 
Preparing to replace python-ibus 1.3.7-1ubuntu3 (using .../python-ibus_1.3.7-1ubuntu4_all.deb) ... 
Unpacking replacement python-ibus ... 
Preparing to replace ibus-gtk 1.3.7-1ubuntu3 (using .../ibus-gtk_1.3.7-1ubuntu4_i386.deb) ... 
Unpacking replacement ibus-gtk ... 
Preparing to replace libmagickcore3 7:6.6.2.6-1ubuntu1 (using .../libmagickcore3_7%3a6.6.2.6-1ubuntu1.1_i386.deb) ... 
Unpacking replacement libmagickcore3 ... 
Preparing to replace libmagickwand3 7:6.6.2.6-1ubuntu1 (using .../libmagickwand3_7%3a6.6.2.6-1ubuntu1.1_i386.deb) ... 
Unpacking replacement libmagickwand3 ... 
Preparing to replace imagemagick 7:6.6.2.6-1ubuntu1 (using .../imagemagick_7%3a6.6.2.6-1ubuntu1.1_i386.deb) ... 
Unpacking replacement imagemagick ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
Preparing to replace libmagickcore3-extra 7:6.6.2.6-1ubuntu1 (using .../libmagickcore3-extra_7%3a6.6.2.6-1ubuntu1.1_i386.deb) ... 
Unpacking replacement libmagickcore3-extra ... 
Preparing to replace openssl 0.9.8o-1ubuntu4.2 (using .../openssl_0.9.8o-1ubuntu4.3_i386.deb) ... 
Unpacking replacement openssl ... 
Preparing to replace software-center 3.0.5 (using .../software-center_3.0.7_all.deb) ... 
Unpacking replacement software-center ... 
Preparing to replace telepathy-haze 0.4.0-1 (using .../telepathy-haze_0.4.0-1ubuntu0.1_i386.deb) ... 
Unpacking replacement telepathy-haze ... 
Preparing to replace tomboy 1.4.0-0ubuntu2 (using .../tomboy_1.4.2-0ubuntu1_i386.deb) ... 
Unpacking replacement tomboy ... 
Preparing to replace xdg-utils 1.0.2+cvs20100307-1 (using .../xdg-utils_1.0.2+cvs20100307-1ubuntu0.1_all.deb) ... 
Unpacking replacement xdg-utils ... 
Preparing to replace libgexiv2-0 0.2.0-0ubuntu2 (using .../libgexiv2-0_0.2.0-0ubuntu2.1_i386.deb) ... 
Unpacking replacement libgexiv2-0 ... 
Preparing to replace libx264-98 2:0.98.1653+git88b90d9-3 (using .../libx264-98_2%3a0.98.1653+git88b90d9-3ubuntu1_i386.deb) ... 
Unpacking replacement libx264-98 ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Rebuilding /usr/share/applications/desktop.en_IN.ISO8859-1.cache... 
WARNING: System locale is invalid 
Processing triggers for libglib2.0-0 ... 
Processing triggers for man-db ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for gconf2 ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_COLLATE to default locale: No such file or directory 
Processing triggers for python-support ... 
Processing triggers for libgtk2.0-0 ... 
Processing triggers for shared-mime-info ... 
Setting up crossplatformui (1.0.38) ... 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service acpid restart 
 
Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart acpid 
acpid start/running, process 5438 
package libqtgui4 exist 
QT_VERSION = 4 
Sorry! The usb-serial driver does not support your Linux version. 
Sorry! Make usb-serial driver error. 
But, it try to use the default driver module. 
mv: cannot stat `/usr/local/bin/ztemtApp/ztemt.ko': No such file or directory 
dpkg: error processing crossplatformui (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libkrb5support0 (1.8.1+dfsg-5ubuntu0.2) ... 
Setting up libk5crypto3 (1.8.1+dfsg-5ubuntu0.2) ... 
Setting up libkrb5-3 (1.8.1+dfsg-5ubuntu0.2) ... 
Setting up libgssapi-krb5-2 (1.8.1+dfsg-5ubuntu0.2) ... 
Setting up empathy-common (2.32.1-0ubuntu1) ... 
Setting up nautilus-sendto-empathy (2.32.1-0ubuntu1) ... 
Setting up empathy (2.32.1-0ubuntu1) ... 
Setting up libwvstreams4.6-base (4.6.1-1ubuntu1) ... 
Setting up libwvstreams4.6-extras (4.6.1-1ubuntu1) ... 
Setting up libuniconf4.6 (4.6.1-1ubuntu1) ... 
Setting up wvdial (1.60.4) ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
 
/etc/wvdial.conf already exists -- not probing your modem. 
  (Run wvdialconf manually if you want to re-detect your modem.) 
 
Setting up gnome-ppp (0.3.23-1ubuntu2) ... 
Setting up gwibber-service (2.32.2-0ubuntu2) ... 
Setting up libibus2 (1.3.7-1ubuntu4) ... 
Setting up python-ibus (1.3.7-1ubuntu4) ... 
Setting up ibus (1.3.7-1ubuntu4) ... 
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/ja_JP (xinput-ja_JP) in auto mode. 
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/ko_KR (xinput-ko_KR) in auto mode. 
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_CN (xinput-zh_CN) in auto mode. 
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_TW (xinput-zh_TW) in auto mode. 
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_HK (xinput-zh_HK) in auto mode. 
update-alternatives: using /etc/X11/xinit/xinput.d/ibus to provide /etc/X11/xinit/xinput.d/zh_SG (xinput-zh_SG) in auto mode. 
Setting up ibus-gtk (1.3.7-1ubuntu4) ... 
Setting up libmagickcore3 (7:6.6.2.6-1ubuntu1.1) ... 
Setting up libmagickwand3 (7:6.6.2.6-1ubuntu1.1) ... 
Setting up imagemagick (7:6.6.2.6-1ubuntu1.1) ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
Setting up libmagickcore3-extra (7:6.6.2.6-1ubuntu1.1) ... 
Setting up openssl (0.9.8o-1ubuntu4.3) ... 
Setting up software-center (3.0.7) ... 
 
(process:5593): Gtk-WARNING **: Locale not supported by C library. 
    Using the fallback 'C' locale. 
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display 
  warnings.warn(str(e), _gtk.Warning) 
WARNING:root:setlocale failed with 'unsupported locale setting' 
Setting up telepathy-haze (0.4.0-1ubuntu0.1) ... 
Setting up tomboy (1.4.2-0ubuntu1) ... 
Setting up xdg-utils (1.0.2+cvs20100307-1ubuntu0.1) ... 
Setting up libgexiv2-0 (0.2.0-0ubuntu2.1) ... 
Setting up libx264-98 (2:0.98.1653+git88b90d9-3ubuntu1) ... 
Processing triggers for python-central ... 
Setting up gwibber (2.32.2-0ubuntu2) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for python-support ... 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 crossplatformui 
Setting up crossplatformui (1.0.38) ... 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service acpid restart 
 
Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart acpid 
acpid start/running, process 5644 
package libqtgui4 exist 
QT_VERSION = 4 
Sorry! The usb-serial driver does not support your Linux version. 
Sorry! Make usb-serial driver error. 
But, it try to use the default driver module. 
mv: cannot stat `/usr/local/bin/ztemtApp/ztemt.ko': No such file or directory 
dpkg: error processing crossplatformui (--configure): 
 subprocess installed post-installation script returned error exit status 1 [/COLOR]
,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

please help me out.

---

### Post by kanishkdudeja on 2010-12-09
try everything that has been suggested in the thread.

---

### Post by sikander3786 on 2010-12-10
@**lokesh1507**:

Welcome to the forums :-)

This thread has been marked Solved by the OP so not many users will be seeing your post. It would be better to start a new thread under Installations & Upgrades sub-forum and include the output of these commands from Terminal under Applications > Accessories menu.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

Thanks.

---

### Post by sampath sree on 2011-10-25
GUYS CHECK THIS OUT>>>>


Well this is *only for experts* and read it completely before you start. 
This is like, reverse-engineering the Debian package management. 
It seems that the package, you are having problem with, is *crossplatformui*. 
so: 
 - Backup the file* /var/lib/dpkg/info/crossplatformui**.postrm* 
 - Edit the file  */var/lib/dpkg/info/crossplatformui.postrm* and insert 
"exit 0" soon after the shebang line. 
 - Run *sudo apt-get -f --purge remove* 
 - *Perform all the steps* (run/debug the backup file) *that the postrm file 
was meant to do* if you really want to clean up the package. 
- Move on.. 
*DISCLAIMER: Follow the steps at your own risk. I bear no responsibility if 
it renders your system unstable.* 


I got the solution here>>> IT WORKS >>>>
above is pasted frm here

[http://groups.google.com/group/foss-nepal/browse_thread/thread/8f4f96bb3d383728](http://groups.google.com/group/foss-nepal/browse_thread/thread/8f4f96bb3d383728)

---

