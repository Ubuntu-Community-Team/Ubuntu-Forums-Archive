---
title: "Cannot install VMWare on Ubuntu 5.10"
date: 2006-04-02
forum: General Help
---

### Post by dmorlow on 2006-04-02
When I try to install VMWare, I get the error below.  Can someone tell me how to fix this?  I tried to install GCC that it's looking for using Synaptics installer and get same error.

dorlow@ubuntu:~/vmware-distrib$ su root
Password:
root@ubuntu:/home/dorlow/vmware-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Workstation.

Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Workstation 5.0.0 build-13124 for Linux completed
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the library files?
[/usr/lib/vmware]

The path "/usr/lib/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want? [yes]

In which directory do you want to install the manual files?
[/usr/share/man]

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware]

The path "/usr/share/doc/vmware" does not exist currently. This program is goingto create it, including needed parent directories. Is this what you want?
[yes]

The installation of VMware Workstation 5.0.0 build-13124 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Workstation for the first time, you need to configure it
by invoking the following command: "/usr/bin/vmware-config.pl". Do you want thisprogram to invoke the command for you now? [yes]

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it.

END USER LICENSE AGREEMENT
FOR VMWARE(R) DESKTOP SOFTWARE PRODUCT


VMWARE, INC. LICENSES THIS DESKTOP SOFTWARE PRODUCT TO YOU SUBJECT TO THE
TERMS CONTAINED IN THIS END USER LICENSE AGREEMENT ("EULA").  READ THE
TERMS OF THIS EULA CAREFULLY.  BY INSTALLING, COPYING OR OTHERWISE USING
THE SOFTWARE (AS DEFINED BELOW), YOU AGREE TO BE BOUND BY THE TERMS OF
THIS EULA.  IF YOU DO NOT AGREE WITH THE TERMS OF THIS EULA, DO NOT INSTALL,
COPY OR USE THE SOFTWARE AND IF YOU HAVE PROOF OF PAYMENT, YOU MAY RETURN
THE UNOPENED SOFTWARE TO THE LOCATION AT WHICH YOU ACQUIRED IT WITHIN
THIRTY (30) DAYS FOR A REFUND OF THE LICENSE FEE.

NOTICE TO CUSTOMER
This EULA is a contract between you (either an individual or an entity)
and VMware, Inc. ("VMware"), which governs your use of the VMware software
product that accompanies this EULA and related software components, which
may include associated media, printed materials, and online or electronic
documentation.  This VMware software product is designed for installation
and use on a personal computer only.  You may not install or use this
VMware software product on a server.

DEFINITIONS
This Desktop software package includes a Desktop software product
(the "VMware Desktop Software") and Open Source Software components.
In this EULA, the VMware Desktop Software and associated media, printed
materials, and online or electronic documentation are collectively
referred to as the "Software."  The VMware Desktop Software enables you
to run one or more instances of third-party operating systems ("Guest
Operating Systems") and applications on a single personal computer.
A serial number ("Software License Key") issued to you by VMware is
required to use the Software.  The term "Number of Licensed Users "
means the number one (1), unless you received a VMware License Certificate
with this software product, in which case the term "Number of Licensed Users"
means the Number of Licensed Users set forth on the VMware License Certificate.

"Open Source Software" means various open source software components,
including, without limitation,  DHCP Server, Tcl/Tk, XFree86, Libresolv,
zlib, libpng, OpenSSL, Advanced Encryption Standard (AES), libfreetype.so.6,
libgcc_s.so.1, libstdc++-v3, libart_lgpl_2.so.2, libatk-1.0.so.0,
libatkmm-1.6.so.1, libgdkmm-2.4.so.1, libgdk_pixbuf-2.0.so.0,
libgdk-x11-2.0.so.0, libglade-2.0.so.0, libglib-2.0.so.0, libglibmm-2.4.so.1,
libglibmm_generate_extra_defs-2.4.so.1, libgmodule-2.0.so.0, libgnomecanvas-2.so.0,
libgnomecanvasmm-2.6.so.1, libgobject-2.0.so.0, libgtkmm-2.4.so.1,libgtk-x11-2.0.so.0,
libpango-1.0.so.0, libpangoft2-1.0.so.0, libpangomm-1.4.so.1,libpangox-1.0.so.0,libpangoxft-1.0.so.0, libsigc-2.0.so.0, libcrypto.so.0.9.7,libssl.so.0.9.7,
libfontconfig.so.1, libXft.so.2, libXrender.so.1, libexpat.so.0,libxml12.so.2,
libpng12.so.0, libpixops.so.2.0.1 and librsvg-2.so.2 licensed under the
terms of applicable open source license agreements included in the materials
relating to such software.  Some Open Source Software components are provided
with the version of the Software than runs on a Linux hostoperating system,
some Open Source Software components are providedwith the version of the
Software that runs on a Windows host operating system, and some Open Source
Software components are provided with both such versions of the Software.

WARNING FOR EVALUATION LICENSEES
The Software can be activated with a no-cost evaluation Software License Key.
Evaluation Software License Keys have an expiration date ("Expiration Date").
If you activate the Software with an evaluation Software License Key:
(i) you may use the Software until the Expiration Date only to evaluate
the suitability of the Software for licensing on a for-fee basis;
(ii) the limited 90-day warranty below is not applicable to you;  (iii) the
limited web-based support services are not applicable to you; (iv) the
provision of Updates for a period of eighteen (18) months from the date
of shipment of the Software is not applicable to you; and (v) THE SOFTWARE
IS PROVIDED TO YOU "AS IS" WITHOUT WARRANTY OF ANY KIND, WHETHER EXPRESS,
IMPLIED, STATUTORY, OR OTHERWISE.  VMWARE BEARS NO LIABILITY FOR ANY DAMAGES
RESULTING FROM USE (OR ATTEMPTED USE) OF THE SOFTWARE THROUGH OR AFTER THE
EXPIRATION DATE, AND HAS NO DUTY TO PROVIDE SUPPORT OR SOFTWARE UPDATES TO YOU.

OPEN SOURCE SOFTWARE
The Open Source Software is composed of individual software components,
each of which has its own copyright and its own applicable license conditions.
You must review the licenses within the individual packages to understand
your rights under them.  The licenses can be found in the open_source_licenses.txt
file, other materials accompanying the software package, the documentation
or corresponding source files available at [http://www.vmware.com/download/open_sources.html](http://www.vmware.com/download/open_sources.html).
Copyrights to the Open Source Software are held by the copyright holders
indicated in the copyright notices in the corresponding source files or
in the open_sources_licenses.txt file or other materials accompanying the
software package.

LICENSE
The Software is licensed, not sold.  Subject to the terms and limitations of
this EULA, VMware hereby grants you a nonexclusive, nontransferable license,
without rights to sublicense, to (i)\uffffmake a number of copies of the Software
less than or equal to the Number of Licensed Users for the purpose of installinga single copy of the Software on an equivalent number of personal computers,
each of which is running a validly licensed copy of the operating system for
which the Software is designed; (ii) use the Software License Key to activate
each copy of the Software made in accordance with sub-clause (i); (iii) have
up to the Number of Licensed Users use the Software (in object code form only)
solely for your own internal information processing services and computing needs;
and (iv) use the documentation accompanying the Software in connection with
permitted uses of the Software.  If you are an entity, each copy of the
Software may be used by one designated individual user only.  The total
number of designated users may not exceed the Number of Licensed Users.
Each copy of the Software may not be used by any other person, whether or
not such person is employed by or otherwise associated with your entity.

LIMITED SHARED USE LICENSE
For shared use computing laboratory environments within academic institutions,
the license grant above shall be modified to permit use of the Software on
a single personal computer without the limitation that such use be limited
to the designated user(s); provided that any such user(s) agree to and abide
by the terms of this EULA; provided further that you must acquire and dedicate
a Software License Key for each separate personal computer on which the Softwareis installed. Under this shared computing laboratory use license, a computing
laboratory at an academic institution having ten personal computers loaded
with the Software on which no more than five users would concurrently access
and use the Software, for example, would require ten Software License Keys.
Unless the computing laboratory is operated and maintained by and within an
academic institution, this limited shared use license does not apply.

LICENSE LIMITATIONS
You may not copy the Software except for a reasonable number of machine-readablecopies of the Software for backup or archival purposes and except as expressly
permitted in the License section above.  You may not share or use concurrently
the Software except as expressly permitted in the Limited Shared Use License
section above.  You may not remove any titles, trademarks or trade names,
copyright notices, legends, or other proprietary markings on the Software.
You are not granted any rights to any trademarks or service marks of VMware.
VMware retains all rights not expressly granted to you.

LICENSE AS UPGRADE OF PREVIOUSLY LICENSED PRODUCT
If you purchased this Desktop software product as an upgrade at the applicable
upgrade price, then you must have previously purchased a prior version of this
Desktop software product at the applicable product (not upgrade) price.  If you
have not purchased a prior version at the applicable product price, then please
contact the vendor from whom you purchased the upgrade, or, if you are unable
to contact your vendor, contact VMware, to make payment for the difference
between the upgrade price and the product price within thirty (30) days of the
date you purchased the upgrade.  If you do not make the appropriate payment
to your vendor or VMware within thirty (30) days, this EULA will automatically
terminate and you must comply with the termination provisions below.

LICENSES REQUIRED FOR THIRD-PARTY SOFTWARE
The Software allows multiple Guest Operating Systems and applications to run
on a single personal computer. You are responsible for obtaining any licenses
necessary to operate any such third-party software, including Guest Operating
Systems.

PROPRIETARY RIGHTS RESERVED BY VMWARE
VMware retains all right, title, and interest in and to the Software and the
Software License Key and in all related copyrights, trade secrets, patents,
trademarks, and any other intellectual and industrial property and proprietary
rights, including registrations, applications, renewals, and extensions of
such rights.

RESTRICTIONS
You may not (i) sell, lease, license, sublicense, distribute or otherwise
transfer in whole or in part the Software or the Software License Key to
another party; (ii) provide, disclose, divulge or make available to, or permit
use of the Software in whole or in part by, any third party without VMware's
prior written consent; (iii) modify or create derivative works based upon the
Software; or (iv) use the Software to provide network, application hosting or
other services to third parties, or otherwise use the Software on a service
bureau or hosting basis for your customers.  Except to the extent expressly
permitted by applicable law, and to the extent that VMware is not permitted
by that applicable law to exclude or limit the following rights, you may not
decompile, disassemble, reverse engineer, or otherwise attempt to derive
source code from the Software, in whole or in part.  You may not disclose
the results of any benchmark test of the Software to any third party without
VMware's prior written approval.

LIMITED SUPPORT AND SUBSCRIPTION SERVICES
VMware may provide limited web-based support services related to the Software
for a period of thirty (30) days after the date of purchase. Upon expiration
of such 30-day period, VMware will not provide any support services under
this EULA.  For a period of eighteen (18) months from the date of shipment
of the Software, VMware will provide you with Update Service, as defined in
the VMware Premium Support Programs and Subscription Services - Terms and
Conditions posted on VMware's Web site at [http://www.vmware.com/support/using/premium.html](http://www.vmware.com/support/using/premium.html)
("Service Terms"), free of charge.  By accepting the terms of this
EULA you are accepting the Service Terms.  Upon expiration of such 18-month
period, VMware will no longer provide you with any Update Service under this EULA.
Thereafter, you may renew the Update Service for a fee in accordance with
the Service Terms.  Notwithstanding the foregoing, if you acquired the
Software as an Update (as defined in the Service Terms) or as part of the
Update Service in connection with a prior purchase of the Software, then
you are not entitled to receive any Update Service or any other support
or subscription services under this EULA.  In either case, you also may
purchase support and subscription services separately.  If you have purchased
VMware support and subscription services with the Software, these services
are provided to you under the Service Terms.   Unless otherwise provided
to you under a separate agreement, any supplemental software code or related
materials that VMware provides to you as part of any Update Service or support
and subscription services are to be considered part of the Software and are
subject to the terms and conditions of this EULA.  VMware may use any technical
information you provide to VMware for any VMware business purposes without
restriction, including for product support and development. VMware will not use
information in a form that personally identifies you.

TERMINATION
VMware may terminate this EULA if you fail to comply with any term of this EULA.In the event of termination, you must destroy all copies of the Software and
Software License Key.  In addition you must remove all copies of the Software
from the personal computer(s) on which it is installed.

GOVERNMENT RESTRICTIONS
You may not export or re-export the Software except in compliance with the
United States Export Administration Act and the related rules and regulations
and similar non-U.S. government restrictions, if applicable.  The Software
and accompanying documentation are deemed to be "commercial computer software"
and "commercial computer software documentation," respectively, pursuant to
DFAR Section 227.7202 and FAR Section12.212(b), as applicable.  Any use,
modification, reproduction, release, performing, displaying, or disclosing of
the Software by the U.S. Government shall be governed solely by the terms of
this EULA.

LIMITED WARRANTY
VMware warrants that the media, if any, on which the Software is delivered
will be free of defects and that the Software will substantially conform to
the description contained in the applicable end user documentation, in each
case for a period of 90 days after the date of shipment of the Software
License Key.  EXCEPT FOR THE PRECEDING EXPRESS LIMITED WARRANTY, TO THE
MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW, VMWARE PROVIDES THE SOFTWARE WITHOUTANY WARRANTIES OF ANY KIND, EXPRESS, IMPLIED, STATUTORY, OR IN ANY OTHER
PROVISION OF THIS EULA OR COMMUNICATION WITH YOU, AND VMWARE SPECIFICALLY
DISCLAIMS ANY IMPLIED WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
PURPOSE, AND NON-INFRINGEMENT.

LIMITATION OF LIABILITY
TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW, IN NO EVENT WILL VMWARE BE
LIABLE FOR ANY LOST PROFITS OR BUSINESS OPPORTUNITIES, LOSS OF USE, BUSINESS
INTERRUPTION, LOSS OF DATA, OR ANY OTHER INDIRECT, SPECIAL, INCIDENTAL, OR
CONSEQUENTIAL DAMAGES UNDER ANY THEORY OF LIABILITY, WHETHER BASED IN CONTRACT,
TORT, NEGLIGENCE, PRODUCT LIABILITY, OR OTHERWISE.  BECAUSE SOME JURISDICTIONS
DO NOT ALLOW THE EXCLUSION OR LIMITATION OF LIABILITY FOR CONSEQUENTIAL OR
INCIDENTAL DAMAGES, THE PRECEDING LIMITATION MAY NOT APPLY TO YOU.

VMWARE'S LIABILITY UNDER THIS EULA WILL NOT, IN ANY EVENT, EXCEED THE LICENSE FEES,
IF ANY, PAID BY YOU TO VMWARE FOR THE SOFTWARE LICENSED BY YOU UNDER THIS EULA.

THE FOREGOING LIMITATIONS SHALL APPLY TO THE MAXIMUM EXTENT PERMITTED BY
APPLICABLE LAW, REGARDLESS OF WHETHER VMWARE HAS BEEN ADVISED OF THE POSSIBILITYOF SUCH DAMAGES AND REGARDLESS OF WHETHER ANY REMEDY FAILS OF ITS ESSENTIAL PURPOSE.

GENERAL
This EULA is governed by the laws of the State of California and the United
States of America, without regard to conflict of law principles. The United Nations
Convention for the International Sale of Goods shall not apply.  This EULA is
the entire agreement between us and supersedes the terms of any purchase orders
and any other communications or advertising with respect to the Software.  If
any provision of this EULA is held invalid, the remainder of this EULA shall
continue in full force and effect.  This EULA may be modified only by written
agreement signed by authorized representatives of you and VMware.

CONTACT INFORMATION
If you have any questions about this EULA, or if you want to contact VMware for
any reason, please direct all correspondence to: VMware, Inc., 3145 Porter Drive,
Palo Alto, CA 94304, United States of America or email [email]info@vmware.com[/email].

VMware and the VMware "boxes" logo and design, as applicable, are registered
trademarks and/or trademarks of VMware, Inc.


Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

***
* Updating MIME database in /usr/share/mime...
***
In which directory do you want to install the mime type icons?
[/usr/share/icons]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by hollywoodb on 2006-04-02
> Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

There's your problem. GCC 3.4 and 4.x can coexist on your system.
```
sudo apt-get install gcc-3.4
```
Then try again.

---

### Post by dmorlow on 2006-04-02
When I do the sudo apt get, I get this error...

dorlow@ubuntu:~$ sudo apt-get install gcc-3.4
Password:
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dorlow@ubuntu:~$

---

### Post by hollywoodb on 2006-04-02
in that case, in terminal:
```
sudo export CC="/usr/bin/gcc-3.4"
sudo ./vmware-install.pl
```

(or you can 'su root' as you were initially doing)

worst case scenario you can change the gcc symlink to gcc-3.4

(as root or using sudo):

```
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
```

**DO NOT** forget to change the links back after vmware is installed by using the above commands but replacing all instances of "3.4" with "4.0"

using the first export command should work and is much safer.

---

### Post by Arandomcow5 on 2006-04-14
i was having the same problems, and
export CC="/usr/bin/gcc-3.4"
solved the problem. Thanks

Except when your in super user, dont type "sudo" before it or it wont work.

---

### Post by krismatth3 on 2006-04-14
FWIW, 

# CC="/usr/bin/gcc-3.4" ./vmware-install.pl 

will work too. Then CC is not changed for subsequent programs in the same shell.

---

### Post by lex1 on 2006-05-22
This may not help but i found this script which tells you how to install vmware on a bb 5-10 server
worked a gem and i am pretty new.

here
[http://www.howtoforums.net/viewtopic.php?t=5](http://www.howtoforums.net/viewtopic.php?t=5)

lx1:D

---

### Post by styven on 2006-05-25
Hi all,

I too am having problems, using this thread i got a lot further than previously, but not quite there yet!

This is where i am, any ideas what i do next?

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

Thanks in advance Steve.

---

### Post by ifokkema on 2006-05-25
[QUOTE=styven]What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include][/QUOTE]

Hi Steve,

You need to install the kernel headers matching your current kernel.

Run:
```
uname -a
```
to find out your kernel version.

Install the headers (change kernel version if needed):
```
sudo apt-get install linux-headers-2.6.12-10
```

Rerun the VMWare installer. Provide this directory (change kernel version if needed):
```
/usr/src/linux-headers-2.6.12-10/include
```

Good luck,

Ivo

---

### Post by styven on 2006-05-25
Hi and thank you for that................

Nearly there but not quite, getting this now!

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-10/include

The directory of kernel headers (version 2.6.12-10) does not match your running
kernel (version 2.6.12-10-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

Steve

---

### Post by twotonz on 2006-05-25
Hi,
I made the same mistake, you must download the headers with the i386 extension there a few header-files matching your kernel ver.), don't worry you are nearly there.

---

### Post by styven on 2006-05-25
[QUOTE=twotonz]Hi,
I made the same mistake, you must download the headers with the i386 extension there a few header-files matching your kernel ver.), don't worry you are nearly there.[/QUOTE]

That did it, great!!

Thanks for your help.

Steve

---

### Post by anjinash on 2006-05-26
Woo hoo!  Thanks for all that info ... I was also having trouble installing VMware, albeit under Dapper.  Am I going to have to do this every time I update the kernel?

---

### Post by ifokkema on 2006-05-26
[QUOTE=anjinash]Woo hoo!  Thanks for all that info ... I was also having trouble installing VMware, albeit under Dapper.  Am I going to have to do this every time I update the kernel?[/QUOTE]

Yup, after upgrading your kernel VMWare will issue a warning the first time it is run on the new kernel. You'll have to install the matching kernel header files and re-run vmware-config.pl.

Ivo

---

