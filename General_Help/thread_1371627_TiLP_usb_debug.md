---
title: "TiLP usb_debug?"
date: 2010-01-03
forum: General Help
---

### Post by VirusCollector on 2010-01-03
I got a TI-89 Titanium for Christmas, yay. But TiLP isn't working at all.

I've installed tilp2 from the repos, and then run "sudo tilp". It gives me this error: "tilp: symbol lookup error: /usr/lib/libticables2.so.2: undefined symbol: usb_debug"

Compiling TiLP from source has issues too; when compiling libticables, this happens:

../src/.libs/libticables2.so: undefined reference to `usb_debug'
../src/.libs/libticables2.so: undefined reference to `usb_error_type'
../src/.libs/libticables2.so: undefined reference to `usb_error_str'

So I want to know what this means. I've installed every permutation of "libusb" there is, including libusb-dev. Shouldn't installing from repos satsify every dependency?

---

### Post by octocpp on 2010-02-21
I have tryed it in opensuse 11.2 and i have the same exact problems you do.  I wonder if it was a change in the kernel ? I currently have 2.6.31.12-0.1-defualt in suse 11.2 32 bit.  Looks like ill have to use the windows ver for now :(, I wonder if it works in WINE ?:confused:

---

### Post by linuxman94 on 2010-02-21
Here is a workaround from the bug page for this.

> 
[https://bugs.launchpad.net/ubuntu/+source/tilp/+bug/49251](https://bugs.launchpad.net/ubuntu/+source/tilp/+bug/49251)

Here is a workaround, and a fairly painless one at that. This will work for now, and may help in finding the issue in the future. Basically I just installed the deb packages for tilp2 from the calcforge repos.

This is what I did to get tilp2 working on my Intrepid (32bit) install...

First, if you still have the tilp2 (and dependencies) installed from the repos, open synaptic and remove them.

Then goto this site and get the packages needed...

[http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/](http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/)

(for a description of each package, click on the 'Packages' link in the directory at this site, you
can download the description file by downloading 'Packages.gz' file)

download the following packages...

libticonv3_1.1.0-1_i386.deb
libtifiles2-5_1.1.1-1_i386.deb
libticalcs2-7_1.1.3-1_i386.deb
libticables2-1_1.2.0-1_i386.deb

gfm_1.02-1_i386.deb
tilp2_1.12-1_i386.deb

NOTE: I installed all of these in the order listed above

After successful install of the above packages you will have to open a terminal and run tilp as sudo

$ sudo tilp

also gfm will run as normal, just type 'gfm' in a term (no quotes :) ). It is a file grouper/ungrouper for the TI backups

When I get a moment, I will try to compare packages from the calcforge to the intrepid repos. I know that two of the Intrepid packages are older versions. Tilp2 and I think the other was libticables (which I suspect is the prob. anyway).


oops that link is dead. disregard

---

