---
title: "LibreOffice for 10.04"
date: 2012-04-05
forum: General Help
---

### Post by Dave_L on 2012-04-05
LibreOffice is not in the Ubuntu 10.04 repositories, but I'd like to install it (replacing OpenOffice).

Are the LibreOffice builds in this PPA considered stable? [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

The note at the top of the page suggests that they might not be stable:

> Most of the packages in this ppa have only experienced minor testing -- in fact it is the place to enable a wider audience to test packages before they are published into the distro proper. In general this ppa is _not_ for the average user to install without a closer look (if it would be, its packages would be in the main repositories).

---

### Post by cogier on 2012-04-05
I use 10.04 and have just checked and Libre Office is available from the Software Centre - See attached. 

Have you completed all your system updates as that is all I can think of that would prevent you seeing this?

---

### Post by Dave_L on 2012-04-05
> **cogier said:**
> I use 10.04 and have just checked and Libre Office is available from the Software Centre - See attached.

You have LibreOffice PPA in your list of sources. ;)

---

### Post by claracc on 2012-04-06
As ppa information says > Most of the packages in this ppa have only experienced minor testing -- in fact it is the place to enable a wider audience to test packages before they are published into the distro proper. In general this ppa is _not_ for the average user to install without a closer look (if it would be, its packages would be in the main repositories).

I would install libreoffice from its .deb package following instructions from libreoffice.org place for the ubuntu system: [http://www.libreoffice.org/get-help/installation/linux/](http://www.libreoffice.org/get-help/installation/linux/)

Since there is now a libreoffice 3.5 I suppose libreoffice 3.4 is stable enough.

I think you have to remove openoffice previously to install libreoffice.

---

### Post by mastablasta on 2012-04-06
you can also download a .deb file and install it (intrucitons are in the file).
 
3.3.x is stable
3.4.x is stable
3.5.x is new version but is also stable

---

### Post by Dave_L on 2012-04-07
Thanks for the replies.

I decided to download the debs (LibO_3.5.2_Linux_x86_install-deb_en-US.tar.gz contains a bunch of .debs) from libreoffice.org, and installed via the provided instructions (dpkg -i *.deb).

It worked without any problems.

Unlike installing from the PPA, OpenOffice was not removed, so both LibreOffice and OpenOffice can be used. I may remove OpenOffice later after I'm satisfied that I no longer need it.

---

