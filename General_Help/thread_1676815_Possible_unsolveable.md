---
title: "Possible unsolveable"
date: 2011-01-27
forum: General Help
---

### Post by fzzy25 on 2011-01-27
Hello all,

I've been given the task of trying to setup a Ghost cast server (don't ask) on Ubuntu 10.10 to "see if it will work"

     Originally I thought I'd be smart and use wine along with ghost, and tftpd32 to handle the process like it does on a windows box. Unfortunately I was too smart for my own good, and it failed miserably. the tftpd32 won't do the handout for PXE booting through wine on Ubuntu. It doesn't seem to like the 3rd party software-ish aproach. It wants to be native on a windows box. So I decided to go with a purely Ubuntu approach to the DHCP, and TFTP part of the process. So I installed Dhcp3, and tftpd-hpa for DHCP hand out and PXE booting my clients. 
     OH.. and just a point of fact, yes, we do know about fog... in fact, we have 2 fog servers already... Like I said, the "boys upstairs" wanted to know if it works... nothing more than that.
     So now I'm at the point of having the client machines get an ip address on boot, but give the dreaded PXE-T01 file not found, for the tftp handout of the boot file.
I've pored through a myriad of forums looking for my answer, to include re-checking my work to make sure I didn't "fat finger" the file location. That part, at least, is correct. 

Wit all of the forums, and "solutions" that I've found, here are the files I've changed, and their contents:

----------------------------------------------------
**Multiple PXELINUX.0 files:**

root@DeploymntSRVR:~# find / -name "pxelinux.0"
/root/.wine/drive_c/Linuxboot/pxelinux.0
/root/.wine/drive_c/users/Public/Application Data/Symantec/Ghost/Template/common/linux/pxe/pxelinux.0
/tftpboot/pxelinux.0
/usr/lib/syslinux/pxelinux.0
root@DeploymntSRVR:~# ^C
root@DeploymntSRVR:~# 

------------------------------------------------------
**/etc/network/interfaces.conf**

auto lo
iface lo inet loopback

auto eth0
    iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0


--------------------------------------------------
**/etc/default/xinetd**

# Default settings for xinetd. This file is sourced by /bin/sh from
# /etc/init.d/xinetd

# enable xinetd Inetd compat mode
INETD_COMPAT=Yes

# Options to pass to xinetd
#
# -stayalive comes by default : it can be removed if xinetd is expected
# not to start when no service is configured
#
XINETD_OPTS="-stayalive"

----------------------------------------------
**/etc/dhcp3/dhcpd.conf**

    # The ddns-updates-style parameter controls whether or not the server will
    # attempt to do a DNS update when a lease is confirmed. We default to the
    # behavior of the version 2 packages (’none’, since DHCP v2 didn’t
    # have support for DDNS.)
    ddns-update-style ad-hoc;

    # option definitions common to all supported networks…
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
    option domain-name SOMENAME;
    option domain-name-servers 192.168.1.1;

    default-lease-time 60;
    max-lease-time 1800;

    # If this DHCP server is the official DHCP server for the local
    # network, the authoritative directive should be uncommented.
    authoritative;

    subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.250;
    filename "/tftpboot/pxelinux.0";
    
    }

If anyone, or everyone, can see where I messed up... and wants to smack me in the back of the head, point to the type-o and say, "there it is stupid".. I'd be most appreciative.

---

### Post by mdshann on 2011-01-27
You have to add the boot server option to your dhcpcd.conf file. It tells the PXE client what system to request the boot files from. I think.


edit:
err try this link - [http://linux-sxs.org/internet_serving/pxeboot.html](http://linux-sxs.org/internet_serving/pxeboot.html)

You need to remove the "/tftpboot/" from the filename option, assuming that your tftp server uses /tftpboot as it's root directory. You also need to set up the pxelinux.cfg file to point to the image you want to boot.... that is if the image is a linux OS. If it's a DOS or Windows OS then you need to do something different... maybe along the lines of - [http://wiki.contribs.org/PXE_booting_to_BARTPE](http://wiki.contribs.org/PXE_booting_to_BARTPE)

That link talks about using a windows tftp server but the files in the tftpboot folder should be the same or similar.

Probably not much help but hopefully I was able to give you some direction!

---

