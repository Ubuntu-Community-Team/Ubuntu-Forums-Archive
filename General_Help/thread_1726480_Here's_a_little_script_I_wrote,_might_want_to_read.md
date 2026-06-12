---
title: "Here's a little script I wrote, might want to read it note for note..."
date: 2011-04-11
forum: General Help
---

### Post by amn108 on 2011-04-11
I wrote a small Bash script I call 'humble' that lets me start a process that is as idle with regards to both CPU and I/O resources as possible. I would appreciate if someone with *nix experience would review my humble [sic] idea and tell me if I am reinventing the wheel here. The reason I wrote it is because whenever I use Transmission, my Ubuntu desktop almost comes to a halt, desktop-usability wise, that is. Even mouse cursor staggers occasionally, something I never thought would be possible :)

Usage is simple - 'humble <binary path>'. F.e. 'humble transmission' and it will spawn Transmission with altered CPU and I/O "niceness", which makes sure that the process only uses the resources when they're well, idle. The script is rudimentary really:

```

#!/bin/bash
$1 &
pid=$!
ionice -c 3 -p $pid
renice 20 -p $pid

```

I put in my ~/bin directory so that I can type 'humble' from wherever in my shell. I'd call it 'bg' but 'bg' is already reserved for something else...

The reason I am sharing this here, is because I am surprised to not having found already existing facility to do this. I know one can always invoke 'ionice' and 'renice' directly, but IMO this is a bit more convenient, no?

-l33t hax0r

---

### Post by 3Miro on 2011-04-11
The idea is not bad, but I am not sure this is the source of your trouble. Unless you have a very old CPU, Transmission shouldn't bother you at all.

What is your file-system, if you are using wubi, you may be a victim of windows NTSF fragmentation.

A more sinister possibility is a failing HDD, although this behavior then would be observed in other places of the system (unless you have two HDD, one for system and one for torrents with only the torrents one failing).

Try lowering the download/upload speed of Transmission, it can easily hog your entire connection and make any Internet access slower than a crippled turtle.

You can manually adjust the "priority" of a process form System Monitor (System -> Admin). Although the script would automatically do that (actually I don't know much about bash scripting, so I am not 100% sure).

---

### Post by Jouke74 on 2011-04-11
Just run and test it. There is not much that can go wrong. It looks ok to me.

---

### Post by amn108 on 2011-04-11
It's an IBM Thinkpad T43 with an Intel Pentium-M 2.0Ghz CPU, which although is part of 6 years old technology, is a really snappy thing.

I have just checked S.M.A.R.T. records for my hard drive disk, and it's completely healthy. I have also not observed any kind of errors, so I think that's out of question.

I am also not complaining of Transmission hogging my network, the laptop and all the software stack seems to handle the bandwidth and connection count just fine. The trouble starts when Transmission itself needs to pipe and assemble all those scattered network-inbound file parts into a file, or so it seems. Even CPU 'nicing' has much less effect than I/O nice, so I am guessing it's the file subsystem stack.

I am not running on WUBI. It's an ext4 system with the entire 80GB Seagate Momentus mobile drive split into dedicated partitions for each of /boot, /usr, /tmp, /var and /home, respectively.

I don't rule out the possibility that I might benefit from an updated kernel (although I do run the quite modern version 2.6.38.*) or disk drivers or stack, but it's only Transmission that bothers me like this, and the script is generic in case others might need it.

I am using the script, and everything seems much snappier, although I have to admit that there is some loss of interactivity compared to not running Transmission at all. But compared to what things were like without the renicing, it's hell of a lot better.

Pardon for being so brief )

---

### Post by ajgreeny on 2011-04-11
I am interested to hear that you are running 2.6.38- kernel, and I wonder if your problem is a symptom of that.

I tried the same kernel version from the kernel ppa repository on my 10.04 box and found that anything transferring to or from a usb disk was appallingly slow; down to a few kb/sec.  It even took about an hour to make a bootable USB drive with startup-disk-creator instead of the usual 5 minutes.  Running the standard kernel for 10.04 got back to the expected  ~20MB/sec that I had previous to the new kernel.

Could you have the same problem with your system?  Try running with the normal kernel next time you boot and check it out; it could be that simple.

---

### Post by amn108 on 2011-04-11
I've had this problem since Ubuntu 9 versions. I have also tried booting with kernel 2.6.32 and it is exactly the same story.

---

