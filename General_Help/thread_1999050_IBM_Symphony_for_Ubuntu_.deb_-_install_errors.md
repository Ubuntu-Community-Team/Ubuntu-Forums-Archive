---
title: "IBM Symphony for Ubuntu .deb - install errors"
date: 2012-06-07
forum: General Help
---

### Post by stormbind on 2012-06-07
Hi all,

I am trying to install IBM Lotus Symphony 3.0.1 for Ubuntu using their .deb installer

Ubunto Software Center gives error, "Dependency not satisfiable: libnotify1 >= 0.4.4"

I tried apt-get libnotify-bin and it says I have the latest version.

How do I fix this?

---

### Post by stormbind on 2012-06-07
Apparently, I need to install this package via the Software Center:

[http://packages.ubuntu.com/natty/i386/libnotify1/download](http://packages.ubuntu.com/natty/i386/libnotify1/download)

How do I derive the full Software Center "APT line" for the above, and complete the install?

EDIT / SOLVED:

Do NOT add the APT line as a repository as this causes Software Center to crash.  Instead, download the .deb from one of the mirrors (via link above) and open only that package in Software Center.  Software Center will read the .deb package and install the missing library.

You can then install the newer versions of IBM Lotus Symphony.

---

### Post by Enigmapond on 2012-06-07
No soluttion but the problem may be the file you are trying to install is for Ubuntu 10.04 and may not be compatible with Natty or higher.

---

### Post by wilee-nilee on 2012-06-07
Get the hardy version for some reason it installs I just installed it in the development release.

I had a no install with this one as well.

You want this version.

symphony_3.0-1hardy1_i386.deb

Hard to get a download of this one as well I saved the deb after the last time.

---

### Post by stormbind on 2012-06-07
Actually, the solution I posted works (I was just too silly to see how).

Download the library as a .deb and then open it in Ubuntu Software Center. Install. Download symphony 3.0.1 as a .deb and all works fine.

Symphony is slow to start-up, but its working.

For those that don't know: Symphony is an older version of OpenOffice/LibreOffice with a built-in older version of FireFox. It has a combined GUI and some plugins for the IBM cloud.

---

### Post by GoodPanos on 2012-06-22
Thank you!  This worked great ):P

---

### Post by roly33 on 2013-04-11
> **stormbind said:**
> Apparently, I need to install this package via the Software Center:

[http://packages.ubuntu.com/natty/i386/libnotify1/download](http://packages.ubuntu.com/natty/i386/libnotify1/download)

How do I derive the full Software Center "APT line" for the above, and complete the install?

EDIT / SOLVED:

Do NOT add the APT line as a repository as this causes Software Center to crash.  Instead, download the .deb from one of the mirrors (via link above) and open only that package in Software Center.  Software Center will read the .deb package and install the missing library.

You can then install the newer versions of IBM Lotus Symphony.

Sorry for opening an old thread but I've been pointed here from the [thread]("http://ubuntuforums.org/showthread.php?t=2134432") that I created the download link no longer works.

@[COLOR=#000000]wilee-nilee where can I get [/COLOR][COLOR=#000000]symphony_3.0-1hardy1_i386.deb from?

Roland[/COLOR]

---

### Post by alejandro3 on 2013-08-25
In the following link you can find the package [COLOR=#333333][FONT=Ubuntu][SIZE=2][SIZE=3]libnotify1_0.4.5-1ubuntu3_i386.deb [SIZE=2]it will install the dependecy you need for Symphony[/SIZE][/SIZE]
[/SIZE]
[/FONT][/COLOR][http://packages.ubuntu.com/lucid/i386/libnotify1/download](http://packages.ubuntu.com/lucid/i386/libnotify1/download)



Enjoy!
[COLOR=#333333][FONT=Ubuntu]


[/FONT][/COLOR]

---

### Post by mphamvu on 2013-12-23
I followed instructions above, it worked though not yet to try the software...

---

