---
title: "DVD Problems &amp; &quot;ldconfig deferred...&quot; errors."
date: 2011-04-30
forum: General Help
---

### Post by ExoGenesis91 on 2011-04-30
Hey, new Ubuntu user here. Just installed Ubuntu onto a new Hard Drive the other day, after my old one with Windows 7 went kaput.

It's been running perfectly fine, been upgraded to 11.04 and I've been dealing fine in regards to updates, installing packages and using the terminal.

Until yesterday when I decided I wanted to watch a DVD. After the DVD was not detected when I inserted it, I Google it, and found out I needed to install several files (libdvdread4 etc) and did so.

This is where the problem branches off a bit though;

Whilst installing it, Terminal works fine, until I get to the point where it says

> ldconfig deferred processing now taking placeAnd then, nothing. Now, I'm not sure if the process ends, or just hangs on that. If I was to install "libdvdread4" this is what I would get;

> michael@Michael-Laptop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2011-04-30 15:32:50--  [http://packages.medibuntu.org/dists/natty/free/binary-i386/Packages](http://packages.medibuntu.org/dists/natty/free/binary-i386/Packages)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7997 (7.8K) [text/plain]
Saving to: `/tmp/dvdcss-xKJ0Vq/Packages'

100%[======================================>] 7,997       --.-K/s   in 0.05s   

2011-04-30 15:32:51 (152 KB/s) - `/tmp/dvdcss-xKJ0Vq/Packages' saved [7997/7997]

--2011-04-30 15:32:51--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-xKJ0Vq/libdvdcss.deb'

100%[======================================>] 38,036      90.5K/s   in 0.4s    

2011-04-30 15:32:51 (90.5 KB/s) - `/tmp/dvdcss-xKJ0Vq/libdvdcss.deb' saved [38036/38036]

(Reading database ... 163035 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-xKJ0Vq/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
And nothing would happen, unless I were to type in another command. I've tried killing Synaptic as several other topics have advised, but nothing. 

At first, I tried playing the DVD thinking, maybe that was the end of the process. But still, the DVD is not appearing whatsoever. It's not like the DVD is appearing but not loading, there is no hint of a DVD or Drive.

Any help would be greatly appreciated, and if any more details are needed just ask.

Thanks.

EDIT** Fixed DVD by entering the BIOS and changing SATA on Optical Drive from IDE to AHCI =)

The other error fixed itself.

---

### Post by ExoGenesis91 on 2011-04-30
Any ideas? Trying to stop this drifting off to the unknown. Really need to get the problem/s sorted.

---

