---
title: "How to Install Code::Block v.10.05 on Ubuntu 9.04?"
date: 2010-10-22
forum: General Help
---

### Post by echo9 on 2010-10-22
Hello everybody!

I need to install COde::Blocks IDE v.10.05 but i only got to know that v.8.x is available in jaunty repos.

How can i install v.10.05 of Code::Blocks IDE?? i tried reading the CB's wiki but i am confused a bit now :(

is there any simple way to install CB ? and is it possible if i go for installing v.8 and then try to update it? is there any feature for this?

--
PS: I need CB for a project which i will getting on; its related to socket programming..to be precise its actually a protocol development/customization.

Can anybody suggest me a good IDE for this? (development language has to be C++) & i have netbeans 6.9 with me but a lot of people say that its slow (a mem hog) when it comes to compiling C++ code.

---

### Post by echo9 on 2010-10-23
bump..

anybody..?? :(

---

### Post by echo9 on 2010-10-23
bump.. 
:( anyone..?

---

### Post by matt_symes on 2010-10-23
Hi

I have just managed to install 10.05. These are the steps i took.

1. go to [http://prdownload.berlios.de/codeblocks/codeblocks-10.05-1-debian-i386.tar.bz2](http://prdownload.berlios.de/codeblocks/codeblocks-10.05-1-debian-i386.tar.bz2) and download one of the archives.

2. Create a directory and unpack the archive. You will see a number of *.deb files. You can do this using nautilus or the command line.

3. Open a terminal and type

sudo dpkg -i codeblocks-common_10.05-1_all.deb libcodeblocks0_10.05-1_i386.deb  codeblocks_10.05-1_i386.deb

The other debs are the docs, headers and development and plugins (you may wish to install them). I am using ubuntu 10.04.

Kind regards

---

### Post by Kevin_a_b on 2010-10-23
I just installed all of the .deb packages but it doesn't run when I go to Applications/Programming/Code::blocks IDE. What did I do wrong? I just typed

sudo dpkg -i *.deb

---

### Post by Kevin_a_b on 2010-10-23
When I try to run it from terminal, I get this

./codeblocks: relocation error: /usr/lib/libcodeblocks.so.0: symbol _Z18wxSafeConvertWX2MBPKw, version WXU_2.8.2 not defined in file libwx_baseu-2.8.so.0 with link time reference

---

### Post by matt_symes on 2010-10-23
Hi

Looks like you have an incorrect version of wxwidgets on your machine for code blocks 10.05. I installed code blocks on ubuntu 10.05 and did not get that runtime link error. Will do some research for you.

Kind regards

---

### Post by matt_symes on 2010-10-23
Hi

> If you use the debian packages and are on ubuntu > 9.10, you have to  use wxwidgets-poackages from apt.wxwidgets.org (see [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian) for details).
As  far as I know, the wxwidgets-packages shipped with ubuntu (>9.10)  are still not binary-compatible with the packages provided by  apt.wxwidgets.org I used to build the packages with.
The packages from wxwidgtes.org are wx2.8.11, but should work with the debs also (at least they do it here).

taken from

[http://forums.codeblocks.org/index.php/topic,12662.0.html](http://forums.codeblocks.org/index.php/topic,12662.0.html)

Yes. Looks like you need to update wxwidgets

Kind regards

---

### Post by Kevin_a_b on 2010-10-23
Done. Now it runs. Thank you very much.

---

### Post by echo9 on 2010-10-23
> **matt_symes said:**
> Hi

I have just managed to install 10.05. These are the steps i took.

1. go to [http://prdownload.berlios.de/codeblocks/codeblocks-10.05-1-debian-i386.tar.bz2](http://prdownload.berlios.de/codeblocks/codeblocks-10.05-1-debian-i386.tar.bz2) and download one of the archives.

2. Create a directory and unpack the archive. You will see a number of *.deb files. You can do this using nautilus or the command line.

3. Open a terminal and type

sudo dpkg -i codeblocks-common_10.05-1_all.deb libcodeblocks0_10.05-1_i386.deb  codeblocks_10.05-1_i386.deb

The other debs are the docs, headers and development and plugins (you may wish to install them). I am using ubuntu 10.04.

Kind regards


i get this when i try to install the above mentioned packages using the exact command.. 

```

(Reading database ... 169107 files and directories currently installed.)
Preparing to replace codeblocks-common 10.05-1 (using codeblocks-common_10.05-1_all.deb) ...
Unpacking replacement codeblocks-common ...
Selecting previously deselected package libcodeblocks0.
Unpacking libcodeblocks0 (from libcodeblocks0_10.05-1_i386.deb) ...
Selecting previously deselected package codeblocks.
Unpacking codeblocks (from codeblocks_10.05-1_i386.deb) ...
Setting up codeblocks-common (10.05-1) ...

dpkg: dependency problems prevent configuration of libcodeblocks0:
 libcodeblocks0 depends on libwxbase2.8-0 (>= 2.8.10.1); however:
  Version of libwxbase2.8-0 on system is 2.8.9.1-0ubuntu6.
 libcodeblocks0 depends on libwxgtk2.8-0 (>= 2.8.10.1); however:
  Version of libwxgtk2.8-0 on system is 2.8.9.1-0ubuntu6.
dpkg: error processing libcodeblocks0 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of codeblocks:
 codeblocks depends on libcodeblocks0 (= 10.05-1); however:
  Package libcodeblocks0 is not configured yet.
 codeblocks depends on libwxbase2.8-0 (>= 2.8.10.1); however:
  Version of libwxbase2.8-0 on system is 2.8.9.1-0ubuntu6.
 codeblocks depends on libwxgtk2.8-0 (>= 2.8.10.1); however:
  Version of libwxgtk2.8-0 on system is 2.8.9.1-0ubuntu6.
dpkg: error processing codeblocks (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Processing triggers for menu ...
Errors were encountered while processing:
 libcodeblocks0
 codeblocks


```

:confused:

---

### Post by echo9 on 2010-10-23
now my synaptic says that plz remove these installed/partially packages namely: "libcodeblocks0" & "codeblocks"

also i get a red circle with a white horizontal line in the centre in my system tray menu area (near volume control :) )

---

### Post by matt_symes on 2010-10-23
Hi 

type at the terminal 

sudo apt-get install -f

and enter your password. That should fix your packages.

What version of ubuntu are you using?

Kind regards

---

### Post by echo9 on 2010-10-23
i have removed the packages mentioned above by my synaptic and i checked out my package versions:

libwxbase2.6-0

libwxbase2.8-0

so is there a conflict between the two..?
others are:

libwxgtk2.6-0
ibwxgtk2.8-0
libwxgtk2.8-dev
libwxbase2.8-dev


PS: I have ubuntu v.9.04 (32 bit)  and my ubuntu is running on kernel 2.6.28-17 generic.

---

### Post by matt_symes on 2010-10-23
Hi

Yes. you also have a problem with wxwidgets

> If you use the debian packages and are on ubuntu > 9.10, you have to  use wxwidgets-poackages from apt.wxwidgets.org (see [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian) for details).
As  far as I know, the wxwidgets-packages shipped with ubuntu (>9.10)   are still not binary-compatible with the packages provided by   apt.wxwidgets.org I used to build the packages with.
The packages from wxwidgtes.org are wx2.8.11, but should work with the debs also (at least they do it here). 			 		

Try following the step in the link. That fixed the OP's issue with wx. As i stated before, i did not have to do this to get it working under 10.04 so i have not gone through those steps.

It does work though so keep at it.

Kind regards

---

### Post by echo9 on 2010-10-23
oh..k  i can try that .. :)

will post the results asap.
i feel like there is a conflict b/w the v2.6 and v.28 of wx lib

---

### Post by echo9 on 2010-10-23
YAY! :) 

finally i got it.. 

actually its a version incompatibility issue of wx base library & wx gtk library they have to of 2.8.11.

just having 2.8.xx branch (<2.8.11) won't do the thing.. as was in my case.. puff~

finally i have it .. 

thanks a lot :guitar:

PARTAY!

---

### Post by TAcadia on 2011-06-26
Thanks, 2 years and and this information is still useful :)

Got Code::Blocks 10.05 working on Ubuntu Maverick 10.10.

Thanks loads. Cheers!

---

