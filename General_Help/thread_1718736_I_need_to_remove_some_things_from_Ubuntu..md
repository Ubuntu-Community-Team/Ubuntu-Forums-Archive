---
title: "I need to remove some things from Ubuntu."
date: 2011-03-31
forum: General Help
---

### Post by pepsifx357 on 2011-03-31
Hey guys, I've been running Linux for about 3 years now.  I still am having difficulties understanding some of the basic unix and linux software and their dependencies.

What I am wanting to do, simply for my own amusement, is to strip the OS down so that I am only running software that I need.  Then I want to build it back up with X and some sort of desktop.

Right now I have a stock Ubuntu 10.04 installation from the alternative DVD.  Right now I sit at 643MB and 14MB of ram.  Of course I would want it to be lower.

Here are the programs currently on the chopping block.  I need to now if I honestly need them or not.  I state next to the software whether or not I know what it is.

Not a clue:        apparmor        
Not a clue:        apparmor-utils
DNS client?        bind9-host
zip:               bzip2
Not a clue:        ca-certificates
A task manager:    cron
Not a clue:        libpam-modules
Not a clue:        libpam-runtime
Some Ubuntu thing: libplymouth2
Not a clue:        dash
Software Language: perl
Software Language: perl-base
Not a clue:        perl-modules
Not a clue:        libsub-name-perl
Not a clue:        libterm-charwidth-perl
Not a clue:        libtext-iconv-perl
Not a clue:        libwww-perl
Not a clue:        dosfstools
Not a clue:        ed
FTP client?        ftp
Encryption:        gnupg
Encryption:        gnupg-curl
Not a clue:        geoip-database
Not a clue:        gpgv
zip:               gzip
Not a clue:        hunspell-en-ca
Not a clue:        hunspell-en-us
Memory test:       memtest86+
Not a clue:        mtr-tiny
Not a clue:        laptop-detect
Not a clue:        ntfs-3g
Partitioner:       parted
Some package thing: popularity-contest
Not a clue:        plymouth
Not a clue:        plymouth-theme-ubuntu-text
Like ssh but crap: telnet
network dump:      tcpdump
Not a clue:        ucf
Not a clue:        wireless-crda
I hate it:         vim-tiny
Hate it:           vim-common
webbrowser:        w3m
Not a clue:        wbritish

So obviously I have not a clue about many things still, and if you've caught an error in my descriptions then I have less of a clue than I thought.

I just need to know what the system needs to run.  I like the basic commands like less, grep, free, df, du, adduser, usermod, apt-get, dpkg, cp, mv, rm, mkdir, ect.  What I don't need are things like w3m telnet(Unless someone knows something I don't), memtest+, and I don't ever use cron, but I also don't know if it does something behind the scenes that is vitally important.  I remember trying to get rid of memtest one time and it wouldn't boot after that.  Any idea why?

Anyway so here it is.

Thanks in advance.

Ben


Edit: Oh, and if possible, I would like to get rid of aptitude in favor of apt-get.  If that is possible.

---

### Post by bodhi.zazen on 2011-03-31
It is easier to start with a minimal install and build up.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by pepsifx357 on 2011-03-31
I never knew....Well, that saves me a load of work.  Thank you VERY MUCH!!!

I can now laugh at myself for spending so much time on this.

Thanks again.

---

