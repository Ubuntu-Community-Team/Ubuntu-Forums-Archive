---
title: "Problem installing Open Office 3.2.0"
date: 2010-02-11
forum: General Help
---

### Post by t0p on 2010-02-11
I am trying to install Open Office 3.2.0 (downloaded from [www.openoffice.org](www.openoffice.org)).  But installation failed.  Thing is, I can't post the "details" thrown up by the installation wizard as I can't copy-paste it!  Grrr!

Okay, it's a dependency thing as far as I can tell.  Here's some of what it says:

```

error: Failed dependencies:

libfreetype.so.6 is needed by ooobasis3.2-core04-3.2.0-9483.i586

```

It goes on to say it needs ooobasis3.2-core04 is required.  But obviously it doesn't have ooobasis3.2-core04 because it doesn't have libfreetype.so.6.  And so it goes.

I did a search for "libfreetype" and the only similarly named packages I found were libfreetype6 and libfreetype6-dev - and both of those are already installed!

In the OOo README it says:

> System Requirements:

- Linux Kernel version 2.4 or higher
- glibc2 version 2.3.2 or higher
- gtk version 2.2.0 or higher
- Pentium compatible PC (Pentium III or Athlon recommended)
- 256 MB RAM (512 MB RAM recommended)
- 440 MB available hard disk space
- Chinese, Japanese and Korean versions: 440 MB available hard disk space
- X Server with 1024x768 resolution (higher resolution recommended), with at least 256 colors
- Window Manager
- Gnome 2.6 or higher, with the gail 1.8.6 and the at-spi 1.7 packages, required for support of assistive technology tools (AT tools)


and I don't know *how* to check if I have all that.  I searched Synaptic for "glibc" and the only similarly named packages I found were glibc-doc and glibc-source - neither of which fit the bill, I fear.

Any suggestions or advice?

---

### Post by lykwydchykyn on 2010-02-11
I haven't upgraded yet, but are you using the .deb files or something else?

---

### Post by t0p on 2010-02-11
Ah never mind.  The stupid openoffice.org site led me to a generic Linux package that was a bunch of rpms that are installed via a java set-up program.  My own fault: the download button said click it for all OS versions other than Linux Debian and Mac OS.  I thought "Ubuntu is an OS other than Debian."  I *should* have thought "Ubuntu is not Debian but it *is* based on Debian.  So I should pretend it is Debian for the purposes of this download."  Silly rabbit!

But now Google has led me to a .deb package on [this page]("http://download.openoffice.org/other.html").

I'm now downloading the 32-bit Linux .deb.  Once I've installed it (or tried to) I'll report back.

---

### Post by t0p on 2010-02-11
Okay, I downloaded the 32-bit Linux deb version - **OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz** - to my Desktop and extracted it there.  So it extracted out to a folder called **OOO320_m12_native_packed-1_en-US.9483**.

Inside that folder are folders called **DEBS**, **licenses** and **readmes**, and a script called **update**.  Inside **DEBS** are a number of deb files with names like **OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-base_3.2.0-12_i386.deb**, **OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-binfilter_3.2.0-12_i386.deb**, **OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-core01_3.2.0-12_i386.deb**... none of them has a name that jumps out as an installer.  The folders **licenses** and **readmes** contain licenses and readmes.  The **update** script doesn't seem to do anything.

I'm sure there should be some kind of installer script.  But there isn't one.

Anyone know what to do?

---

### Post by samantha_ on 2010-02-11
> **t0p said:**
> Okay, I downloaded the 32-bit Linux deb version - **OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz** - to my Desktop and extracted it there.  So it extracted out to a folder called **OOO320_m12_native_packed-1_en-US.9483**.

Inside that folder are folders called **DEBS**, **licenses** and **readmes**, and a script called **update**.  Inside **DEBS** are a number of deb files with names like **OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-base_3.2.0-12_i386.deb**, **OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-binfilter_3.2.0-12_i386.deb**, **OOO320_m12_native_packed-1_en-US.9483/DEBS/ooobasis3.2-core01_3.2.0-12_i386.deb**... none of them has a name that jumps out as an installer.  The folders **licenses** and **readmes** contain licenses and readmes.  The **update** script doesn't seem to do anything.

I'm sure there should be some kind of installer script.  But there isn't one.

Anyone know what to do?

I couldn't find one either.
and it didnt create a menu, but assuming your in the debs directory,
```

sudo dpkg -i *.deb

```
should work.

---

### Post by spcwingo on 2010-02-11
> **samantha_ said:**
> I couldn't find one either.
and it didnt create a menu, but assuming your in the debs directory,
```

sudo dpkg -i *.deb

```
should work.

After that cd into the desktop-integration directory and issue the same command again:

```
sudo dpkg -i ./*.deb
```

You should now have your menu entries.  ;)

---

### Post by luigi_mb on 2010-02-11
> **t0p said:**
> Okay, I downloaded the 32-bit Linux deb version - **OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz** - to my Desktop and extracted it there.  So it extracted out to a folder called **OOO320_m12_native_packed-1_en-US.9483**.

...


Make sure you also get 

**OOo_3.2.0_LinuxIntel_langpack_en-US_deb.tar.gz**

or one of the other similar packages if you use a language other than US English.

/luigi

---

### Post by samantha_ on 2010-02-11
> **spcwingo said:**
> After that cd into the desktop-integration directory and issue the same command again:

```
sudo dpkg -i ./*.deb
```

You should now have your menu entries.  ;)

already checked that. there was no desktop-integration folder - which was why I fell back to 3.1

---

### Post by spcwingo on 2010-02-11
> **samantha_ said:**
> already checked that. there was no desktop-integration folder - which was why I fell back to 3.1

I promise that it's in there as I just upgraded to OOo3.2...did you download this one?

[http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz]("http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz")

---

### Post by PGTips91 on 2010-02-11
> **samantha_ said:**
> I couldn't find one either.
and it didnt create a menu, but assuming your in the debs directory,
```

sudo dpkg -i *.deb

```
should work.

On the main download instructions page it has the following instructions : --

[Instructions for Downloading and Installing OpenOffice.org 3.x]("http://download.openoffice.org/common/instructions.html#other_linux")
> Linux RPM-based Installation
Prerequisites

If you want Java integration, you want to make sure you have the latest JRE installed. It should be at least JRE 1.5. You can find the JRE for Linux at the Java JRE for Linux download site. Or, you can choose to have the JRE included with your OpenOffice.org download. Alternatively, a JRE might be included on the installation media of your distro as part of a complete Java development environment.
Installation Steps

   1. Review the System Requirements
   2. Unpack the downloaded image into a directory. For example, currently, the following command would unpack into the current directory:
   3. tar xvzf OOo_3.0.0_LinuxIntel_install_xxxxxx.tar.gz
      This will create a source directory with the OpenOffice.org installation. The directory will have a rather long name but be prefixed by "OOO3...".
   4. su to root, if necessary, and navigate to OpenOffice.org installation directory, the OOO3... source directory.
      Since the default packaging of OpenOffice.org for Linux is RPM, you will likely need to be root to run the rpm command.
   5. cd into the RPMS subdirectory of the source directory.
      You should see a lot of rpms here and one sub-directory called "desktop-integration".
   6. Install this new version by typing rpm -Uvih *rpm.
      By default, this will install OpenOffice in your /opt directory.
      NOTE: See additional installation options and other useful information in the Setup Guide.
   7. Finally, cd to desktop-integration. Depending on your package manager/system, install the appropriate desktop interface.


For the version that I have downloaded, OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz, I presume the instructions would just need to be amended to replace the rpm command by the command you've given.

OK, done that.

Next, cd into the Desktop Integration and run the command again, but with errors.

I've removed the previous version of OpenOffice with Synaptic. Now to run again. Still no-go.
```
paul@paul-ArtistX07:/media/Spare/DownloadedInstallationFiles/OpenOffice.org/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$ sudo dpkg -i *.deb
dpkg: regarding openoffice.org3.2-debian-menus_3.2-9472_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org3.2-debian-menus_3.2-9472_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.2-debian-menus_3.2-9472_all.deb
paul@paul-ArtistX07:/media/Spare/DownloadedInstallationFiles/OpenOffice.org/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$

```

Starting OpenOffice from the menu now opens OpenOffice 3.0.1 not 3.2.0 so I am now in a muddle!

Paul

---

### Post by samantha_ on 2010-02-11
> **PGTips91 said:**
> On the main download instructions page it has the following instructions : --

[Instructions for Downloading and Installing OpenOffice.org 3.x]("http://download.openoffice.org/common/instructions.html#other_linux")


For the version that I have downloaded, OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz, I presume the instructions would just need to be amended to replace the rpm command by the command you've given.

OK, done that.

Next, cd into the Desktop Integration and run the command again, but with errors.

I've removed the previous version of OpenOffice with Synaptic. Now to run again. Still no-go.
```
paul@paul-ArtistX07:/media/Spare/DownloadedInstallationFiles/OpenOffice.org/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$ sudo dpkg -i *.deb
dpkg: regarding openoffice.org3.2-debian-menus_3.2-9472_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org3.2-debian-menus_3.2-9472_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.2-debian-menus_3.2-9472_all.deb
paul@paul-ArtistX07:/media/Spare/DownloadedInstallationFiles/OpenOffice.org/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$

```

Starting OpenOffice from the menu now opens OpenOffice 3.0.1 not 3.2.0 so I am now in a muddle!

Paul
You havent removed them well enough.
```

sudo apt-get remove openoffice.org-core

```

---

### Post by PGTips91 on 2010-02-11
> **samantha_ said:**
> You havent removed them well enough.
```

sudo apt-get remove openoffice.org-core

```

Thanks, but still no go.

I tried again, this time using gdebi-gtk and it spits out an error message : --
> Error: Breaks exisiting package 'openoffice.org-common' conflict: openoffice.org-debian-menus ( )


I've tried to delete those items from the menu [right-click on menu and choose 'edit'] but without success!

Paul

---

### Post by spcwingo on 2010-02-11
> **PGTips91 said:**
> Thanks, but still no go.

I tried again, this time using gdebi-gtk and it spits out an error message : --


I've tried to delete those items from the menu [right-click on menu and choose 'edit'] but without success!

Paul

Try removing those two packages using synaptic (openoffice.org-common and openoffice.org-debian-menus) and then try installing again noting any errors.

---

### Post by altonbr on 2010-02-11
Shoulda followed this thread: [http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)

Seems to have a good success rate too.

---

### Post by PGTips91 on 2010-02-12
> **altonbr said:**
> Shoulda followed this thread: [http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)

Seems to have a good success rate too.

I finally managed to get the desktop-integration to install, after I had been through and uninstalled, in Synaptic, anything that had previously been installed, including any configuration files left behind otherwise.

Now my menu works again and loads the latest version of OpenOffice.org

Paul

---

### Post by XEyedBear on 2010-02-18
> **spcwingo said:**
> After that cd into the desktop-integration directory and issue the same command again:

```
sudo dpkg -i ./*.deb
```You should now have your menu entries.  ;)

This information is extracted directly from the instructions at this url:

[http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros)

and it seems to work - but NOT for KUBUNTU I now find, to my regret. Having deleted the Ubuntu distro versions of Open Office,as per instructions, I now cannot find out where the OOO-released version of 3.2 is and so cannot do any work!

Does anybody know how to start OOo 3.2 under Kbuntu?


Sorry, forgot to give the error messages I get under Kuntu:

dpkg: regarding .../openoffice.org3.2-debian-menus_3.2-9472_all.deb containing openoffice.org-debian-menus:
 openoffice.org-common conflicts with openoffice.org-debian-menus
  openoffice.org-debian-menus (version 3.2-9472) is to be installed.
dpkg: error processing ./openoffice.org3.2-debian-menus_3.2-9472_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 ./openoffice.org3.2-debian-menus_3.2-9472_all.deb

---

### Post by PGTips91 on 2010-02-18
> **XEyedBear said:**
> This information is extracted directly from the instructions at this url:

[http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros)

and it seems to work - but NOT for KUBUNTU I now find, to my regret. Having deleted the Ubuntu distro versions of Open Office,as per instructions, I now cannot find out where the OOO-released version of 3.2 is and so cannot do any work!

Does anybody know how to start OOo 3.2 under Kbuntu?


Sorry, forgot to give the error messages I get under Kuntu:

dpkg: regarding .../openoffice.org3.2-debian-menus_3.2-9472_all.deb containing openoffice.org-debian-menus:
 openoffice.org-common conflicts with openoffice.org-debian-menus
  openoffice.org-debian-menus (version 3.2-9472) is to be installed.
dpkg: error processing ./openoffice.org3.2-debian-menus_3.2-9472_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 ./openoffice.org3.2-debian-menus_3.2-9472_all.deb

I think that if you go into synaptic and remove anything to do with the old installation, you will clear the way for the installation. I had the same error message, but after going into Synaptic, Status, Not Installed (Residual Config) and removed everything, then the next attempt at installing OpenOffice.org3 succeeded.

Worth a try any way.

I've just manually changed a quick-launch icon so that it now works with OpenOffice.org3 but checking the data in the menu and copying and pasting it into the icon properties.

The command to launch it is ```
openoffice.org3 -writer %U
```
You could try typing that into a Konsole window to see if it will start it up even though the menu installation is not complete.

Paul

---

### Post by mikilewinger on 2010-02-25
I tried installing without uninstalling and made a mess - any dpkg/synaptic/apt-get command would be refused on account of errors (several types). In the end, I succeeded after reinstalling openoffice with

```
apt-get install openoffice*.*

```

and then cleaned up apt's cache files by deleting them (...) with

```
rm /var/cache/apt/*.bin

```

afterwards rebuilding the apt package repository data with

```
apt-get update
```

and FINALLY removing openoffice 3.1 according to the instructions found in this post. I could probably have performed the same process by reinstalling openoffice 3.1 after apt cleanup.

I hope this helps,

Michael

---

