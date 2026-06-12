---
title: "Package manager error messages?"
date: 2011-05-20
forum: General Help
---

### Post by terrykiwi83 on 2011-05-20
Ok so I have been trying to install some games from the Synaptic Package Manager and I get the same error all the time and am unable to install anything.

Here are the error messages:

[[IMG]http://img862.imageshack.us/img862/6184/screenshot1q.th.jpg[/IMG]](http://img862.imageshack.us/i/screenshot1q.jpg/)

[[IMG]http://img695.imageshack.us/img695/8358/screenshot2cn.th.jpg[/IMG]](http://img695.imageshack.us/i/screenshot2cn.jpg/)

[[IMG]http://img146.imageshack.us/img146/6593/screenshot3vi.th.jpg[/IMG]](http://img146.imageshack.us/i/screenshot3vi.jpg/)

I have tried these solutions to no avail.

```

sudo apt-get install -f

```

On doing the above I get

```


terry@Oracle:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libreoffice-l10n-common libebackend-1.2-1 libcanberra-gtk3-0
  libgnome-desktop-3-0 libgtkhtml-4.0-common libgtkhtml-4.0-0
  gnome-desktop3-data libedata-cal-1.2-11 libgtkhtml-editor-4.0-0
  libedata-book-1.2-9 libgtk-3-bin libgtk-3-0 libgail-3-0
  libcanberra-gtk3-module libgtk-3-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  liferea-data
The following NEW packages will be installed:
  liferea-data
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/385 kB of archives.
After this operation, 1,516 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 257990 files and directories currently installed.)
Unpacking liferea-data (from .../liferea-data_1.6.4-1ubuntu7_all.deb) ...
dpkg: error processing /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb (--unpack):
 trying to overwrite '/usr/share/liferea/pixmaps/available.png', which is also in package faenza-extras 0.9
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
terry@Oracle:~$ 

```

Anyone got any suggestions on how to fix?

FYI: Ubuntu 11.04, x64Bit, Unity Desktop

---

### Post by matt_symes on 2011-05-20
Hi

Open a terminal and type either

```
sudo dpkg -i --force-overwrite liferea-data_1.6.4-1ubuntu7_all.deb
```

or 

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb
```

I forget which one it is from the 2 above.

And then for good measure

```
sudo apt-get -f install
```

Hopefully that should fix it.

Kind regards

---

### Post by hansdown on 2011-05-20
Hi terrykiwi83.

Open synaptic.

In the bottom left, click custom filters.

In the top left, click broken.

You should be offered a choice to "fix boken packages".

---

### Post by terrykiwi83 on 2011-05-20
> **matt_symes said:**
> Hi

Open a terminal and type either

```
sudo dpkg -i --force-overwrite liferea-data_1.6.4-1ubuntu7_all.deb
```

or 

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb
```

I forget which one it is from the 2 above.

And then for good measure

```
sudo apt-get -f install
```

Hopefully that should fix it.

Kind regards

Hey Thanks, Worked a Treat (The 2nd One).

Thanks Muchly

---

### Post by donato roque on 2011-06-01
Thank you for this thread. 
I got the same problem.
Problem solved.

---

