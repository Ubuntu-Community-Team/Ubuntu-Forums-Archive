---
title: "SANE + HPLIP + Tomato + F300 hangs with large scan areas"
date: 2011-05-05
forum: General Help
---

### Post by darthwissen on 2011-05-05
First of all, sorry if I am posting in the wrong area, but this seemed the most appropriate one.

SANE + HPLIP 3.11.3a-1 + Tomato v1.28.8754 ND USB Std + Hp Deskjet F380 (F300 series) only works with small scan areas.

This error is affecting SANE runing on my tomato router, this affects all computers that try to use that scanner, regardless of platform, in fact, it affects scans originating from the router itself.

I believe that it could also happen on ubuntu if I had the same configuration as the router, it seems to be an error that would happen on any platform with the same SANE/hplip settings and hardware (HP Deskjet F380).

The problem is also related to DPIs, but I can't manage to get one full page with 75 DPI, which is the lowest possible.

If i get a small area (around 1/4 of the full glass) it will scan at some times, if i increase the DPI, it won't scan. I will get an **[COLOR="Red"]Error during device I/O[/COLOR]**, even if I try to scan directly from scanimage.

I would like to have the scanner function of my AiO printer working, at least to scan the full glass in low resolutions (<=150).

I can't load previews as well.

I thought it could be a memory problem, since it does scan small areas, but it is not, in fact, the memory usage doesn't increase much during the scan, I even created a 128MB swap partition in my flash drive (was afraid of doing so, since it would wear it quickly, will probably remove now), but it didn't change anything, it still doesn't scan with more than 55% of the router's memory (16MB) free and more than 97% of the swap memory free.

I would also like to know where else should I look for a solution to this issue, already googled for hours and hours... Maybe someone could recommend me another forum or place to ask for help.

Thanks all in advance for your effort in helping me out,

Igor Campos

Here are my configuration files:

/opt/etc/sane.d/dll.conf
```

hpaio

```

/opt/etc/sane.d/saned.conf
```

192.168.0.0/24

```

/opt/etc/xinetd.d/saned
```

service saned
{
        port = 6566
        socket_type = stream
        server = /opt/sbin/saned
        protocol = tcp
        user = root
        group = root
        wait = no
        disable = no
}

```

/opt/etc/xinetd.conf
```

# Copyright 1999-2004 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2
# Sample configuration file for xinetd

defaults
{
        only_from      = localhost 192.168.0.0/24
        instances      = 60
        log_type       = FILE /opt/var/xinetd.log
        log_on_success = HOST PID
        log_on_failure = HOST
        cps            = 25 30
}

includedir /opt/etc/xinetd.d

```

Everything is configured properly, I got the **dbus and cups installe**d since **both are required for hplip** to work properly.

Here are some other files, that shows what happens:

sane-find-scanner
```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x03f0 [HP], product=0x5511 [Deskjet F300 series]) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

scanimage -L
```

device `hpaio:/usb/Deskjet_F300_series?serial=CN6BSGK1M104KH' is a Hewlett-Packard Deskjet_F300_series all-in-one

```

hp-probe
```

root@white:/opt/bin# ./hp-probe -busb
warning: python-dbus not installed.
warning: hp-probe should not be run as root/superuser.

HP Linux Imaging and Printing System (ver. 0.0.0)
Printer Discovery Utility ver. 4.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


--------------------
| DEVICE DISCOVERY |
--------------------
                                                                                                                                                                                                                                             Device URI                                         Model
  -------------------------------------------------  ----------------------
  hp:/usb/Deskjet_F300_series?serial=CN6BSGK1M104KH  HP Deskjet F300 series

Found 1 printer(s) on the 'usb' bus.


Done.

```

scanimage > test.jpg
```

scanimage: sane_start: Error during device I/O

```

saned -d5
```

[saned] main: starting debug mode (level 5)
[saned] read_config: searching for config file
[saned] read_config: done reading config
[saned] saned (AF-indep+IPv6) from sane-backends 1.0.22 starting up
[saned] do_bindings: trying to get port for service "sane-port" (getaddrinfo)
[saned] do_bindings: " sane-port " service unknown on your host; you should add
[saned] do_bindings:      sane-port 6566/tcp saned # SANE network scanner daemon
[saned] do_bindings: to your /etc/services file (or equivalent). Proceeding anyway.
[saned] do_bindings: [0] socket () using IPv6
[saned] do_bindings: [0] socket failed: Address family not supported by protocol
[saned] do_bindings: [1] socket () using IPv4
[saned] do_bindings: [1] setsockopt ()
[saned] do_bindings: [1] bind () to port 6566
[saned] do_bindings: [1] listen ()
[saned] run_standalone: waiting for control connection
[saned] handle_connection: processing client connection
[saned] check_host: access by remote host: 192.168.0.10
[saned] check_host: remote host is not IN_LOOPBACK nor IN6_LOOPBACK
[saned] check_host: local hostname: white
[saned] check_host: local hostname(s) (from DNS): c0a8:2:1862:ff7f::
[saned] check_host: local hostname(s) (from DNS): c0a8:2:1862:ff7f::
[saned] check_host: local hostname(s) (from DNS): c0a8:2:1862:ff7f::
[saned] check_host: local hostname(s) (from DNS): white
[saned] check_host: local hostname(s) (from DNS): white
[saned] check_host: local hostname(s) (from DNS): white
[saned] check_host: remote host doesn't have same addr as local
[saned] check_host: opening config file: /etc/hosts.equiv
[saned] check_host: can't open config file: /etc/hosts.equiv (No such file or directory)
[saned] check_host: opening config file: saned.conf
[saned] check_host: config file line: `192.168.0.0/24'
[saned] check_host: subnet with base IP = 192.168.0.0, CIDR netmask = 24
[saned] check_host: access granted from IP address 192.168.0.10 (in subnet 192.168.0.0/24)
[saned] init: access granted
[saned] init: access granted to darthwissen@192.168.0.10
[saned] process_request: waiting for request
[saned] process_request: got request 1
[saned] process_request: waiting for request
[saned] process_request: got request 2
[saned] process_request: access to resource `hpaio' granted
[saned] process_request: sane_open returned: Success
[saned] process_request: waiting for request
[saned] process_request: got request 4
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 7
[saned] start_scan: trying to bind data port 0
[saned] start_scan: using port 2111 for data
[saned] process_request: waiting for request
[saned] process_request: got request 8
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 5
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request
[saned] process_request: got request 6
[saned] process_request: waiting for request

```

saned doesn't report any error, but starts waiting for another request.

---

### Post by darthwissen on 2011-05-11
Bump!

---

