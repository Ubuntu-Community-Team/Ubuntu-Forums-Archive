---
title: "Wireshark"
date: 2011-01-22
forum: General Help
---

### Post by Radiokt3k on 2011-01-22
Hi,
I recently installed ubuntu linux on my notebook and it went flawlessly.  I really like it.  I installed Wireshark through the ubuntu software manager and it also installed great.  But it installed version 1.2.7, and version 1.4.3 is out on the ubuntu page.  I'm not a linux expert, and I'm having trouble upgrading the existing version to the latest version and wondered if someone knows how I can make that happen.  The 1.2.7 version, even though it's GTK, won't use the GEOIP option within wireshark, I think it's a wireshark version issue..that's why I'm trying to upgrade it.
Thanks
John[SIZE=5]
[/SIZE]

---

### Post by hakermania on 2011-01-22
Well, strange, I have installed 1.2.11 and still says no new version:
```
root@MaD-pc:/home/alex# wireshark -v
_**wireshark 1.2.11**_

Copyright 1998-2010 Gerald Combs <gerald@wireshark.org> and contributors.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Compiled with GTK+ 2.22.0, (32-bit) with GLib 2.26.0, with libpcap 1.1.1, with
libz 1.2.3.4, with POSIX capabilities (Linux), with libpcre 8.2, with SMI 0.4.8,
with c-ares 1.7.3, with Lua 5.1, with GnuTLS 2.8.6, with Gcrypt 1.4.5, with MIT
Kerberos, with GeoIP, with PortAudio V19-devel (built Aug  3 2010 05:16:18),
without AirPcap.

Running on Linux 2.6.35-23-generic, with libpcap version 1.1.1, GnuTLS 2.8.6,
Gcrypt 1.4.5.

Built using gcc 4.4.5.
root@MaD-pc:/home/alex# apt-get install wireshark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
_**wireshark is already the newest version.**_
The following packages were automatically installed and are no longer required:
  vcdimager gcj-jre gcj-4.4-jre-lib libgcj10 dvdauthor gcj-jre-headless gcj-4.4-base libgcj-common gcj-4.4-jre
  gcj-4.4-jre-headless libgcj10-awt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
root@MaD-pc:/home/alex#
```

---

### Post by matt_symes on 2011-01-22
Hi

Are you talking about

[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Ethereal-1961.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Ethereal-1961.shtml)

or 

[http://www.wireshark.org/download/](http://www.wireshark.org/download/)

You must build it from source.

BTW: That's a silly sized font to use.

Kind regards

---

### Post by matt_symes on 2011-01-22
Hi

I have just managed to build and install it on my machine. These are the steps i took...

Install these.

```
sudo apt-get install build-essential
sudo apt-get install bison
sudo apt-get install flex
```

Goto

[http://www.tcpdump.org/](http://www.tcpdump.org/) 

and dowload libpcap-1.1.1.tar.gz

Extract and navigate to the directory and then

```
./configure
make
sudo make install
```

download wireshark source from here

```
http://www.wireshark.org/download.html
```

extract and follow instructions on here

```
http://www.wireshark.org/docs/wsdg_html_chunked/ChSrcBuildFirstTime.html
```

I.E.

```
./autogen.sh
```

install any dependencies this requires

```
./configure
make
sudo make install
```

That built it for me. Hopefully it will work for you.

EDIT: I actually downloaded the source from [http://linux.softpedia.com/get/Inter...eal-1961.shtml](http://linux.softpedia.com/get/Inter...eal-1961.shtml). 

Kind regards

---

### Post by cjejuni on 2011-01-25
hi:

trying to build per instructions, but glib requirement cannot find!
error:

configure: error: Package requirements (glib-2.0 >= 2.27.3    atk >= 1.29.2    pango >= 1.20    cairo >= 1.6    gdk-pixbuf-2.0 >= 2.21.0) were not met:

Requested 'glib-2.0 >= 2.27.3' but version of GLib is 2.26.1 

2.26.1 is latest. where do you get 2.27.3. last of the libraries needed.
thanks,
cjejuni

---

### Post by uRock on 2011-01-25
Have tried running Wireshark as root?

---

### Post by cjejuni on 2011-01-29
> **uRock said:**
> Have tried running Wireshark as root?

Yes, it worked on the old version. the last wireshark requirement for building/compiling is not found. so where can i find the glib 2.27.3? must be hidden somewhere. if not, i'll just wait till new wireshark version is released.
tnx,
cjejuni

---

### Post by Radiokt3k on 2011-02-07
I haven't tried this yet, but I really appreciate the detailed instructions.  And I'll also check my glib version before I get started.

---

### Post by Radiokt3k on 2011-02-08
II trtied this and got to here:
I.E.
 
  	Code:
 	./autogen.sh 
 I extracted the source and then ran the above command and got the following message:
"no such file or directory"

I'm just not savvy with Linux, so I'm sure it's some misunderstanding I'm having about what exactly to do.

---

