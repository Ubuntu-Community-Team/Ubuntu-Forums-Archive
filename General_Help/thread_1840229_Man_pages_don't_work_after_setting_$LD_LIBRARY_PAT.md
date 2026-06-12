---
title: "Man pages don't work after setting $LD_LIBRARY_PATH"
date: 2011-09-07
forum: General Help
---

### Post by LegendaryLegume on 2011-09-07
Greetings!  I have installed Ubuntu 10.04 Lucid Lynx on what was formerly a Windows XP machine
(I wiped the drive).  I have been trying to get my development environment up and running, but have
encountered some odd problems.  I installed XAMPP, rvm, and both Ruby and Rails.  I discovered
that I could not run the Rails server, WEBrick, unless I set

LD_LIBRARY_PATH="/opt/lampp/lib"

so that it could find the MySQL library.  So far, so good.  But then I discovered that setting
$LD_LIBRARY_PATH causes gvim to fail:

 zatoichi:~$ gvim: /opt/lampp/lib/libz.so.1: no version information available (required by /usr/lib/libpython2.6.so.1.0)
gvim: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

I was able to get gvim to function (eliminating the second error but not the first) by setting

LD_LIBRARY_PATH="/usr/lib:/opt/lampp/lib"

(I presume the first error only matters if I want to use Python from within Vim.)

What is more disturbing is that for either setting of $LD_LIBRARY_PATH, man pages don't work.
If I try to do a command like

$ man man

I get the error

Manual page man(1) line ?/? (END)

If I unset $LD_LIBRARY_PATH, the problem goes away and man pages work normally again.
Why is this?  How many other things are likely to be broken because I had to set a value for
$LD_LIBRARY_PATH?  Do I somehow need to define a value for $MANPATH?  If so, why,
since Ubuntu doesn't seem to define it at all by default?  Thanks for any suggestions you can
offer.

---

### Post by haqking on 2011-09-07
> **LegendaryLegume said:**
> Greetings!  I have installed Ubuntu 10.04 Lucid Lynx on what was formerly a Windows XP machine
(I wiped the drive).  I have been trying to get my development environment up and running, but have
encountered some odd problems.  I installed XAMPP, rvm, and both Ruby and Rails.  I discovered
that I could not run the Rails server, WEBrick, unless I set

LD_LIBRARY_PATH="/opt/lampp/lib"

so that it could find the MySQL library.  So far, so good.  But then I discovered that setting
$LD_LIBRARY_PATH causes gvim to fail:

 zatoichi:~$ gvim: /opt/lampp/lib/libz.so.1: no version information available (required by /usr/lib/libpython2.6.so.1.0)
gvim: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

I was able to get gvim to function (eliminating the second error but not the first) by setting

LD_LIBRARY_PATH="/usr/lib:/opt/lampp/lib"

(I presume the first error only matters if I want to use Python from within Vim.)

What is more disturbing is that for either setting of $LD_LIBRARY_PATH, man pages don't work.
If I try to do a command like

$ man man

I get the error

Manual page man(1) line ?/? (END)

If I unset $LD_LIBRARY_PATH, the problem goes away and man pages work normally again.
Why is this?  How many other things are likely to be broken because I had to set a value for
$LD_LIBRARY_PATH?  Do I somehow need to define a value for $MANPATH?  If so, why,
since Ubuntu doesn't seem to define it at all by default?  Thanks for any suggestions you can
offer.


reinstall

sudo apt-get install man manpages

---

### Post by LegendaryLegume on 2011-09-07
Unfortunately, re-installing the man pages did nothing to solve the problem.  In fact, it
brought to light a new one:

zatoichi:~$ sudo apt-get install man manpages
[sudo] password for zatoichi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting man-db instead of man
man-db is already the newest version.
manpages is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libboost-thread1.40.0 libboost-date-time1.40.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

zatoichi:~$ apt-get autoremove
apt-get: /opt/lampp/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

As you can see, doing the suggested autoremove gives an error, which is also apparently
due to the value of $LD_LIBRARY_PATH.  I'd really like to get a better understanding of why
setting $LD_LIBRARY_PATH screws up Ubuntu's behavior even for its built-in applications.

---

