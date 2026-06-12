---
title: "Problem installing .bin file."
date: 2009-10-31
forum: General Help
---

### Post by bhishan on 2009-10-31
I am trying to install Adobe Reader in Karmic. I downloaded the .bin file from Adobe's website. Then I typed the commands as shown in the screenshot i have attached. My question is which place is the suitable place to install it and how do I install it there. As you can see in the screenshot I wanted it to install to the home folder and it wants to create a home folder in the desktop and install it there. Any solutions. Also, is there a way to install .bin file without using the terminal?

---

### Post by renkinjutsu on 2009-10-31
install it in /opt like it suggested

opt is in the root directory, but it's separate from all the other system libraries and binaries (usually where beta/alpha software is installed)

---

### Post by bhishan on 2009-10-31
> **renkinjutsu said:**
> install it in /opt like it suggested

opt is in the root directory, but it's separate from all the other system libraries and binaries (usually where beta/alpha software is installed)

oh, i didn't know it was a suggestion, lol, thanks

---

### Post by bhishan on 2009-10-31
> **renkinjutsu said:**
> install it in /opt like it suggested

opt is in the root directory, but it's separate from all the other system libraries and binaries (usually where beta/alpha software is installed)

But it says cannot write to directory /opt

---

### Post by renkinjutsu on 2009-10-31
you have to have root permissions to install it to /opt

run the command with sudo

---

### Post by QLee on 2009-10-31
[QUOTE=renkinjutsu]opt is in the root directory, but it's separate from all the other system libraries and binaries (usually where beta/alpha software is installed)[/QUOTE]


To clarify for the sake of being more complete, one can choose to install alpha or beta software there but it's not just for that, some distros and users prefer /opt over /usr/local, but according to the Linux Filesystem Hierarchy:
"Chapter 1. Linux Filesystem Hierarchy
1.13. /opt

This directory is reserved for all the software and add-on packages that are not part of the default installation. For example, StarOffice, Kylix, Netscape Communicator and WordPerfect packages are normally found here. To comply with the FSSTND, all third party applications should be installed in this directory. Any package to be installed here must locate its static files (ie. extra fonts, clipart, database files) must locate its static files in a separate /opt/'package' or /opt/'provider' directory tree (similar to the way in which Windows will install new software to its own directory tree C:\Windows\Progam Files\"Program Name"), where 'package' is a name that describes the software package and 'provider' is the provider's LANANA registered name.

Although most distributions neglect to create the directories /opt/bin, /opt/doc, /opt/include, /opt/info, /opt/lib, and /opt/man they are reserved for local system administrator use. Packages may provide "front-end" files intended to be placed in (by linking or copying) these reserved directories by the system administrator, but must function normally in the absence of these reserved directories. Programs to be invoked by users are located in the directory /opt/'package'/bin. If the package includes UNIX manual pages, they are located in /opt/'package'/man and the same substructure as /usr/share/man must be used. Package files that are variable must be installed in /var/opt. Host-specific configuration files are installed in /etc/opt.

Under no circumstances are other package files to exist outside the /opt, /var/opt, and /etc/opt hierarchies except for those package files that must reside in specific locations within the filesystem tree in order to function properly. For example, device lock files in /var/lock and devices in /dev. Distributions may install software in /opt, but must not modify or delete software installed by the local system administrator without the assent of the local system administrator.

The use of /opt for add-on software is a well-established practice in the UNIX community. The System V Application Binary Interface [AT&T 1990], based on the System V Interface Definition (Third Edition) and the Intel Binary Compatibility Standard v. 2 (iBCS2) provides for an /opt structure very similar to the one defined here.

Generally, all data required to support a package on a system must be present within /opt/'package', including files intended to be copied into /etc/opt/'package' and /var/opt/'package' as well as reserved directories in /opt. The minor restrictions on distributions using /opt are necessary because conflicts are possible between distribution installed and locally installed software, especially in the case of fixed pathnames found in some binary software.

The structure of the directories below /opt/'provider' is left up to the packager of the software, though it is recommended that packages are installed in /opt/'provider'/'package' and follow a similar structure to the guidelines for /opt/package. A valid reason for diverging from this structure is for support packages which may have files installed in /opt/ 'provider'/lib or /opt/'provider'/bin."

---

### Post by bhishan on 2009-10-31
> **renkinjutsu said:**
> you have to have root permissions to install it to /opt

run the command with sudo

I read in some forum, not to use sudo with the ./filename command. I did it anyways and it is working. thanks again:)

---

### Post by bhishan on 2009-10-31
> **QLee said:**
> To clarify for the sake of being more complete, one can choose to install alpha or beta software there but it's not just for that, some distros and users prefer /opt over /usr/local, but according to the Linux Filesystem Hierarchy:
"Chapter 1. Linux Filesystem Hierarchy
1.13. /opt

This directory is reserved for all the software and add-on packages that are not part of the default installation. For example, StarOffice, Kylix, Netscape Communicator and WordPerfect packages are normally found here. To comply with the FSSTND, all third party applications should be installed in this directory. Any package to be installed here must locate its static files (ie. extra fonts, clipart, database files) must locate its static files in a separate /opt/'package' or /opt/'provider' directory tree (similar to the way in which Windows will install new software to its own directory tree C:\Windows\Progam Files\"Program Name"), where 'package' is a name that describes the software package and 'provider' is the provider's LANANA registered name.

Although most distributions neglect to create the directories /opt/bin, /opt/doc, /opt/include, /opt/info, /opt/lib, and /opt/man they are reserved for local system administrator use. Packages may provide "front-end" files intended to be placed in (by linking or copying) these reserved directories by the system administrator, but must function normally in the absence of these reserved directories. Programs to be invoked by users are located in the directory /opt/'package'/bin. If the package includes UNIX manual pages, they are located in /opt/'package'/man and the same substructure as /usr/share/man must be used. Package files that are variable must be installed in /var/opt. Host-specific configuration files are installed in /etc/opt.

Under no circumstances are other package files to exist outside the /opt, /var/opt, and /etc/opt hierarchies except for those package files that must reside in specific locations within the filesystem tree in order to function properly. For example, device lock files in /var/lock and devices in /dev. Distributions may install software in /opt, but must not modify or delete software installed by the local system administrator without the assent of the local system administrator.

The use of /opt for add-on software is a well-established practice in the UNIX community. The System V Application Binary Interface [AT&T 1990], based on the System V Interface Definition (Third Edition) and the Intel Binary Compatibility Standard v. 2 (iBCS2) provides for an /opt structure very similar to the one defined here.

Generally, all data required to support a package on a system must be present within /opt/'package', including files intended to be copied into /etc/opt/'package' and /var/opt/'package' as well as reserved directories in /opt. The minor restrictions on distributions using /opt are necessary because conflicts are possible between distribution installed and locally installed software, especially in the case of fixed pathnames found in some binary software.

The structure of the directories below /opt/'provider' is left up to the packager of the software, though it is recommended that packages are installed in /opt/'provider'/'package' and follow a similar structure to the guidelines for /opt/package. A valid reason for diverging from this structure is for support packages which may have files installed in /opt/ 'provider'/lib or /opt/'provider'/bin."

Thanks a lot for the detailed info. I appreciate it.

---

### Post by Aditya Bhavaraju on 2009-12-19
Thanks a lot.....

---

