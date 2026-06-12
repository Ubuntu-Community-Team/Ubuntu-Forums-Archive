---
title: "AMSN on 12.04"
date: 2012-04-07
forum: General Help
---

### Post by deserthowler on 2012-04-07
I use AMSN chat on several versions of Debian based systems on multiple platforms.  I can't find AMSN in the 12.04 repos and was wondering if there is a reason for this or if it is coming at later date.

Earl

---

### Post by howefield on 2012-04-07
It was removed from the Ubuntu repositories in 12.04.

[https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3)

---

### Post by noughtypixy on 2012-05-03
that sucks amsn has been my favorite chat cliant for years

had amsn configured exactly how I liked it and had even altered a fue lines of the code to my exact specifications so am rather disappointed at its removal, they could have at least left it on my machine even tho had taken it off the repository

---

### Post by noughtypixy on 2012-05-03
would going back to 10.04 let me get it back?
means saving loads onto disk then installing, repersonalising the whole system then laoding all my files back on so dont realy want to do it if dont have to
also I dont personaly care that they havent updated it for years I like it!

---

### Post by immoT on 2012-05-03
Install amsn on 12.04

go [https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3)

1) Builds
precise i386 / precise amd64
2) Built files
download:
amsn-data_0.98.4-0ubuntu3_all.deb
amsn_0.98.4-0ubuntu3_i386.deb
3) Install first amsn-data, then amsn (by doubleclicking)

Warning: this way installing package have never automatic updates.

---

### Post by youngunix on 2012-05-07
> **immoT said:**
> Install amsn on 12.04

go [https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3)

1) Builds
precise i386 / precise amd64
2) Built files
download:
amsn-data_0.98.4-0ubuntu3_all.deb
amsn_0.98.4-0ubuntu3_i386.deb
3) Install first amsn-data, then amsn (by doubleclicking)

Warning: this way installing package have never automatic updates.

If the above solution doesn't work or if you don't feel comfortable with this method, then try this:
+Go to [http://www.amsn-project.net/download.php](http://www.amsn-project.net/download.php)
+Download the **Windows version**
+Assuming you have "**Wine**" installed: *_right click_* on "**_aMSN-0.98.4-tcl85-windows-installer_**" > *_Open With_* > *_Wine Windows Program Loader_*
+And just follow the installation process.

Good Luck

---

### Post by Ethelshai on 2012-05-11
I managed to compile aMSN, launch it and log on. Chatting with my contacts worked without any problem. Of course, audio/video chats are not available since I didn't include farsight. Nonetheless aMSN is perfectly usable and stable. Here is what I did :

**1) Install all the required libraries, tools, compilers :**
```
sudo apt-get install build-essential libgupnp-igd-1.0-dev libv4l-dev tcl tcl8.5-dev tcl-tls tk tk8.5-dev libx11-dev libpng12-dev libjpeg62-dev libsnack2
```Note : If Apt can't find "tcl" or "tk", just indicate "tcl8.5" and "tk8.5" instead.

**2) Download the aMSN sources archive : [http://sourceforge.net/projects/amsn/files/amsn/0.98.4/amsn-0.98.4-src.tar.gz/download](http://sourceforge.net/projects/amsn/files/amsn/0.98.4/amsn-0.98.4-src.tar.gz/download)**

**3) Extract it :**
```
tar -xvzf amsn-0.98.4-src.tar.gz
```**4) Edit file utils/linux/capture/capture.h (and not capture.c). Look for the following section :**
```

#ifdef HAVSYS_VIDEODEV2_H
#   include <sys/videodev2.h>
#else
#   include <linux/videodev.h>
#endif

```And replace (mandatory or it will fail to compile and install) ```
<linux/videodev.h>
``` by ```
<linux/videodev2.h>
``` then save the file and close the editor.

**5) Go back to the sources base directory and enter :**
```
./configure
```Once this step will be completed, the following summary should appear :
```

compile time options summary
============================

    X11          : yes
    Tcl         : 8.5
    TK          : 8.5
    DEBUG        : no
    STATIC       : no
    FARSIGHT     : no
    LIBV4L       : yes
    GUPNP-IGD    : yes

```FARSIGHT is indicated a not included, which is normal in the present case. It won't bother you later on, but the only counterpart will be that voice/video chats won't be available.

**6) Compile the whole :**
```
make
```Everything should go smoothly. Normally, it doesn't take more than a few minutes, even on weak/slow machines.

**7) Install aMSN :**
```
sudo make install
```Normally, aMSN should even appear automatically in the installed software menus, and its tray icon should work as well, same for all the standard features. At worst, just create a launcher on the desktop (or anywhere else you see fit), and fill in the command field with "*amsn*". And there you go :)

Tested on Xubuntu 12.04 (i386 alternate install) on a Hercules eCafé EC-800 H20G/S netbook.

---

### Post by revpaul on 2012-05-15
nice fix thanks Ethelshai 
Amsn up and running.

---

### Post by razeer on 2012-08-27
Well, I know that this is solved, but, I still cant get it to work!

Lets start like this. Today I changed from using Windows since XP up to Windows 7 that I used since release. I wanted something new, but I still need to use some things, one is MSN and my cam. I tried to downloaded the ubuntu package and did get tar.gz, I know that I can extract it, but after that, I really dont know how to go further. I have tried to see tutorials as movie, and did read one on another forum. Still I dont get it.

Can anyone help me with a step-by-step guide how I should do after downloading the tar.gz? I want to learn, but as I said, I dont really get it.

Im using Ubuntu 12.04LTS 64-bit, and started with Ubuntu and Linux today.

Many thanks. (ps, sorry for my english)

---

### Post by Oranabi on 2012-10-06
> FARSIGHT is indicated a not included, which is normal in the present case. It won't bother you later on, but the only counterpart will be that voice/video chats won't be available.


and whatshould i do if i want to include FARSIGHT ?
i appretiate if someone shows me the way.

---

### Post by Claus7 on 2012-10-17
Hello,

> **Oranabi said:**
> and whatshould i do if i want to include FARSIGHT ?
i appretiate if someone shows me the way.

most probably it's not going to work! Farsight did somehow the work some time ago (a long time ago to be precise), yet after a change of protocol from the original msn, this was dropped because it demanded a lot amount of time from the developers. So, at the time being, I do not think that you will be able to implement such a feature, unless in version 1.0 or something this feature is back and running again.

In order to install amsn in any ubuntu box is trivial today. There is no need to downgrade. Take a look on my threads/posts about how to compile amsn with just one click, if you still have not guessed how to do it up to now.

Regards!

---

### Post by stlu on 2012-12-30
Here is another way: instead of adding a PPA repository, I just installed the backports by downloading from here:

[http://packages.ubuntu.com/precise-backports/amsn-data](http://packages.ubuntu.com/precise-backports/amsn-data)

and then

[http://packages.ubuntu.com/precise-backports/amsn](http://packages.ubuntu.com/precise-backports/amsn)

(I took the i386 package because my CPU is 32-bit, OR you might need the amd64 package if your CPU is 64-bit)


Then the graphical package manager automatically downloaded and installed tk8.5 (needed for amsn-data), and tcl-tls (needed for amsn).

---

