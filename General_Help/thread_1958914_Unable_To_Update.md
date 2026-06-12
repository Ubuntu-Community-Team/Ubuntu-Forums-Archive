---
title: "Unable To Update"
date: 2012-04-15
forum: General Help
---

### Post by closlikescocoa on 2012-04-15
Total Noob 
can't figure out why I can't update, I've followed multiple forums, and I feel like I might end up making things worse if I don't seek assistance.

I'm having trouble installing updates and updating. I receive this message
[INDENT]The package system is broken
[/INDENT][INDENT]Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
[/INDENT]I type in apt-get install -f and receive this:
[INDENT]The following packages will be upgraded:
  libbind9-60
1 upgraded, 0 newly installed, 0 to remove and 271 not upgraded.
3 not fully installed or removed.
Need to get 23.0 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libbind9-60 i386 1:9.7.3.dfsg-1ubuntu4.1 [23.0 kB]
Fetched 23.0 kB in 0s (38.1 kB/s)      
(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libbind9-60' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/INDENT]don't know where to go from there... help?


Running, 11.10 32bit

---

### Post by xyzzyman on 2012-04-17
If you've followed other instructions, is it safe to assume you've already tried a 'sudo apt-get clean'?? And then a 'sudo apt-get update' after that? Maybe you should try downloading it directly:

[http://mirror.pnl.gov/ubuntu//pool/main/b/bind9/libbind9-60_9.7.3.dfsg-1ubuntu4.1_i386.deb](http://mirror.pnl.gov/ubuntu//pool/main/b/bind9/libbind9-60_9.7.3.dfsg-1ubuntu4.1_i386.deb)

And at a command prompt, install it via the command:

```

sudo dpkg -i libbind9-60_9.7.3.dfsg-1ubuntu4.1_i386.deb
```

---

