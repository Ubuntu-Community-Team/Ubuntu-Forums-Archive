---
title: "Anyone know of a Firewalk type program for Ubuntu?"
date: 2006-04-09
forum: General Help
---

### Post by RichGags on 2006-04-09
Im looking for a program to help me with Firewalking.  Anyone know of one?  I cant get the actual program Firewalk to work.  It says its for BSD.

Thanks!
Rich

---

### Post by b3nw on 2008-02-26
it works.... i've seen it but I get stuck here:

checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for libnet_build_ipv4 in -lnet... yes
checking for pcap_open_live in -lpcap... yes
checking for arp_get in -ldnet... no
configure: error: No libdnet?  [http://libdnet.sourceforge.net](http://libdnet.sourceforge.net).



after installing both libdnet from sourceforge (1.11) and the newer (1.12) from code.google.com still pulling this error.

---

### Post by Tolaris on 2008-04-11
Maybe this is too late for you, but you can use firewalk with Ubuntu.  The problem is that libdnet on BSD is known as libdumbnet on (at least Ubuntu) Linux.  This works as of gutsy (7.10):

sudo apt-get install libdumbnet1 libdumbnet-dev
cd /usr/lib
sudo ln -s /usr/lib/libdumbnet.so libdnet.so
cd /usr/include
sudo ln -s dumbnet.h dnet.h

Now you can download and compile firewalk 5.0, with one change to the source.  Gutsy installs gcc 4.0 by default, which doesn't like switch statements with no instructions in the default case.  Just insert this line on line 193 of firewalk.c:

old:
                    default:
                        /* empty */

new:
                    default:
                        break;
                        /* empty */

Attached is a patch you can apply to firewalk.c.  Then cd into the firewalk directory, and run:

./configure
make
sudo install firewalk /usr/local/bin
sudo cp man/firewalk.8 /usr/local/man/man8

---

### Post by b3nw on 2008-05-19
ah yes, this does work. I did get this working in a similar manner.
cheers for instructions.

---

### Post by harryman01 on 2008-06-05
Thanks for the help, 

it works!!

---

