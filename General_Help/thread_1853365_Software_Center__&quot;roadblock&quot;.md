---
title: "Software Center  &quot;roadblock&quot; ?"
date: 2011-10-02
forum: General Help
---

### Post by jimberry on 2011-10-02
When I tried to install the latest jAlbum package (jalbum_10.0.1-1_all.deb)  from [http://jalbum.net/en/software/download](http://jalbum.net/en/software/download), the installation manager (Ubuntu Software Center) reported "Items cannot be installed or removed until the package catalog is repaired" and offered to repair the package catalog. The repair, however, also failed with the message
"sun-dlj-v1-1 license could not be presented
try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive

dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6.26-1natty1_amd64.deb (--unpack):
subprocess new pre-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Unpacking sun-java6-jre (from .../sun-java6-jre_6.26-1natty1_all.deb) ..."

I think this is a "roadblock" from an unsuccessful earlier attempt to install something else, Lucida TrueType fonts(from the SunJRE). This is "ticked" in the Ubuntu Software Center package list (as though it is successfully installed), but does not show up as an available font in Libre Office Writer.
Trying to uninstall Lucida TrueType fonts also results in the message "Items cannot be installed or removed until the package catalog is repaired".

Is there a way to exit from this "vicious circle"?

---

### Post by jimberry on 2011-10-04
:confused: No thoughts on this?

---

### Post by oldos2er on 2011-10-04
If you haven't accepted the Sun java EULA, that could be the problem. Run ```
sudo dpkg --configure -a
``` when the EULA comes up, use Tab to highlight 'Ok' then press Enter.

---

### Post by jimberry on 2011-10-04
Thanks.
However -
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6.26-1natty1); however:
  Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-fonts

Does this need Sun/Oracle java installed instead of openJDK? 
I can do without the sun-java6-fonts, but this problem seems to prevent me from installing any other unrelated packages. I really just want to remove the roadblock.  Up to now, I have not had any issues with openJDK.

---

### Post by oldos2er on 2011-10-05
jalbum has these dependencies, sun-java5-jre sun-java6-jre sun-java7-jre openjdk-6-jre. Try ```
sudo apt-get clean

sudo apt-get install sun-java6-jre sun-java6-fonts
``` then try installing jalbum again.

---

### Post by jimberry on 2011-10-06
Thanks, but are you sure jAlbum has ALL of those dependencies, or just "one or the other"?

I had been running earlier releases of jAlbum on Ubuntu without Sun jre and never had a problem. It's true that some jAlbum users have had problems with some JPG files, and these problems have typically resolved by installing Sun jre. But these could really have been problems with specific graphics card drivers.   

Eventually, the Ubuntu OS presented me with a solution involving stepping through a help screen clearing up the failed earlier attempts to install some fonts that apparently DID have a dependency on sun-java6-jre.

---

### Post by oldos2er on 2011-10-06
I think only one of the *-jre packages is required. The installer for jalbum checks your system to see if at least one of those packages is installed.

---

