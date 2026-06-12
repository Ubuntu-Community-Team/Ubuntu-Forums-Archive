---
title: "apt-get moment 22: unmet dependecies"
date: 2006-02-10
forum: General Help
---

### Post by mirshafie on 2006-02-10
I tried to install libfame with apt-get yesterday, but something went seriously wrong. Now I can't install new packages because:

[INDENT]
[20:58:21] ~ $ sudo apt-get install (any-package)
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gstreamer0.8-fame: Depends: libfame0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/INDENT]

Ok, nothing strange with that really, apt-get -f install should fix this, right? Only:

[INDENT][21:00:56] ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfame0
The following NEW packages will be installed:
  libfame0
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
54 not fully installed or removed.
Need to get 0B/86.0kB of archives.
After unpacking 352kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 101564 files and directories currently installed.)
Unpacking libfame0 (from .../libfame0_0.9.0-0unofficialubuntu1_i386.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame-0.9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
[/INDENT]

So, at the moment i cannot use apt-get to do anything. I've tried removing these packages and others, but I always get the same error message, and nobody on #ubuntu seemed to know anything about this.

How can I fix it? And is there any way to install packages that are not in any way related to gstreamer or libfame with apt-get in the meantime, by skipping the dependency check or something?

I'd really appreciate some help here :)

---

### Post by Greg2 on 2006-02-10
[QUOTE=mirshafie]
dpkg: error processing /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame-0.9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/QUOTE]
There are two libfame packages in the repositories. Try to remove the libfame package that you already have installed with:```
sudo apt-get --purge remove libfame-0.9
```
Then try to use ‘sudo apt-get -f install’ again.

If that does not work, ‘then’ you will have to ‘manually’ remove the package first with:```
sudo rm /usr/lib/libfame-0.9.so.0.0.0
``` and ‘probably’ the same for /usr/share/doc/libfame0 and whatever else is installed.

---

### Post by mirshafie on 2006-02-10
Thanks for the reply!
I'm afraid "--purge remove" does not work, I get the same error message as before.
The broken package is gstreamer0.8-fame. There's no package by that name in my /usr/lib, so I can't remove it.

I have /usr/lib/gstreamer-0.8/, and in that directory about 176 files by the names libgst*.so. Nothing even close to libfame or or anything like that.

By the way, if I do locate gstreamer0.8-fame I get this:
[INDENT]/var/lib/dpkg/info/gstreamer0.8-fame.preinst
/var/lib/dpkg/info/gstreamer0.8-fame.postinst
/var/lib/dpkg/info/gstreamer0.8-fame.md5sums
/var/lib/dpkg/info/gstreamer0.8-fame.postrm
/var/lib/dpkg/info/gstreamer0.8-fame.list
/var/cache/apt/archives/gstreamer0.8-fame_0.8.11-0unofficialubuntu5.2_i386.deb
/usr/share/doc/gstreamer0.8-fame
/usr/share/doc/gstreamer0.8-fame/NEWS.gz
/usr/share/doc/gstreamer0.8-fame/README.Debian
/usr/share/doc/gstreamer0.8-fame/copyright
/usr/share/doc/gstreamer0.8-fame/changelog.Debian.gz
[/INDENT]

To me, none of these files seem important to this matter. But perhaps I should remove them just in case?

Cheers
sam

---

### Post by mirshafie on 2006-02-11
After running Adept (a KDE package manager similar to Synaptic - if any Gnome user would ever run into this problem), the problems are gone. I usually do not use GUI package managers, but Adept seemed to somehow remove gstreamer0.8-plugins and gstreamer0.8-fame.

So now everything seems to work as usual.

Thanks for taking the time to help me!

---

### Post by Greg2 on 2006-02-11
There is a known bug in the Synaptic package manager; It requires a clean environment with no half installed packages to perform any additional changes.

That is why I was trying to get you to remove the wrong libfame dependency for gstreamer0.8-fame, so that the package manager could install the proper libfame0 from the same repository as gstreamer0.8-fame. I know this to be true because I’ve installed (without any problems) gstreamer0.8-fame version 0.8.11-0unofficialubuntu5.2 with libfame0 version 0.9.0-0unofficialubuntu1 from the cipherfunk.org repository.

Anyway, I’m glad you have it fixed. :)

---

