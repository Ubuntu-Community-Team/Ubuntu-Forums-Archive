---
title: "Padre won't start after distro upgrade (lib missing?)"
date: 2011-05-01
forum: General Help
---

### Post by kd7swh on 2011-05-01
Padre (the Perl IDE) won't open now that I have upgraded to 11.04.
Clearly there is a problem with a Wx library but I haven't been able to clear it up.

All the dependencies seem to be accounted for. Here is the output when I try running it  from the terminal: 


```
$ padre
Can't load '/usr/lib/perl5/auto/Wx/Wx.so' for module Wx: /usr/lib/perl5/auto/Wx/
Wx.so: symbol wxDefaultVideoMode, version WXU_2.8 not defined in file libwx_gtk2
u_core-2.8.so.0 with link time reference at /usr/lib/perl/5.10/DynaLoader.pm lin
e 192.
 at /usr/share/perl5/Padre/TaskThread.pm line 23
Compilation failed in require at /usr/share/perl5/Padre/TaskThread.pm line 23.
BEGIN failed--compilation aborted at /usr/share/perl5/Padre/TaskThread.pm line 2
3.
Compilation failed in require at /usr/share/perl5/Padre/Startup.pm line 113.


```

Does anyone have any ideas?

Thanks,


Jon

---

### Post by Supersede on 2011-05-03
I am having the same issue (upgraded to 11.04 as well), with the same results displayed as Jon.

Anyone have suggestions? I'll mess around with it and see what I can come up with.

---

### Post by Supersede on 2011-05-03
Here is a possible *temporary* solution I found in the Padre IRC.
This is above me at the moment so I'm going to take the opportunity to do some learning. 

I was also asked to link to their wiki for the issue so someone can possibly give a user friendly solution.

[http://padre.perlide.org/trac/wiki/DownloadUbuntu](http://padre.perlide.org/trac/wiki/DownloadUbuntu)
&
[http://padre.perlide.org/trac/ticket/1209#comment:6](http://padre.perlide.org/trac/ticket/1209#comment:6)

> 
15:52 **Jake**        question: is Padre broken in ubuntu 11.04? is there a known issue about this and is there an eta? thanks in advance
15:53 **szabgab**     Jake: I have not tried padre in 11.04 yet, I am using 10.10
15:53 **Jake**        there is a bun reported to ubuntu
15:54 **Jake**        im just wondering if the devs of padre are aware of it
15:54 **szabgab**     but if you think it is broken there, then please fill a bug report with ubuntu as they are the distributers, what we can do is document the issue on our wiki
15:54 **szabgab**     and also help you install the latest version of Padre from CPAN
15:54 **szabgab**     Jake: if there is areport already, could you give us the link?
15:55 **Jake**        [https://bugs.launchpad.net/ubuntu/+source/padre/+bug/761782](https://bugs.launchpad.net/ubuntu/+source/padre/+bug/761782)
15:55 **Jake**        i uninstalled the version that comes with natty and installed the one from cpa nand get same results as in this bug issue
15:56 **Jake**        cpan not cpa :P
15:56 **szabgab**     Jake: the issues seems to be in their WxWidgets or in Wx
15:56 **Jake**        new kb doesnt like me
15:56 **szabgab**     so probably you will need to force install those from CPAN
15:56 **szabgab**     it is PITA but that usually works
15:56 **Jake**        any pointers to give me?
15:57 **Jake**        I love padre hehe cant live without it and i cant revert my upgrade to 11.04
15:58 **szabgab**     [http://padre.perlide.org/trac/wiki/DownloadUbuntu](http://padre.perlide.org/trac/wiki/DownloadUbuntu)
16:00 **Jake**        Alien::wxWidgets is up to date (0.51)
16:00 **Jake**        Wx is up to date (0.98).
16:00 **szabgab**     probably, but they were still incorrectly compiled
16:01 **szabgab**     I'd probably insall local::lib to be on the safe side
16:01 **Jake**        ok so u want me to force a reinstall of both these from cpan?
16:01 **szabgab**     and then force install alien::wxWidgets (and tell it to compile)
16:01 **szabgab**     from CPAN
16:01 **Jake**        kk sec
16:01 **szabgab**     an d then force install Wx
16:03 Hyppolit    wiki page [http://padre.perlide.org/trac/wiki/DownloadUbuntu](http://padre.perlide.org/trac/wiki/DownloadUbuntu) changed by szabgab
16:03 **Jake**        hehe
16:03 **Jake**        nice
16:04 **Jake**        installing Wx now
16:06 **Jake**        sorry about the delay
16:06 **Jake**        my work pc is tired and my boss is to cheap
16:06 **szabgab**     it takes time to compile those
16:07 **Jake**        well first 2 took under a minute
16:07 **Jake**        its Wx thats taking a while hehe
16:07 **szabgab**     if it was that fast then you did not compile wxwidgets
16:07 **szabgab**     let's hope that the problem was in Wx only
16:08 **Jake**        well up to now this is what i did
16:08 **Jake**        in order
16:08 **Jake**        sudo cpan
16:08 **szabgab**     Alien::wxWidgets by deafault uses the one you already have installed, I  think
16:08 **Jake**        install local::lib
16:08 **Jake**        force install Alien::wxWidgets
16:08 **Jake**        force install Wx
16:08 **szabgab**     local::lib should not need sudo :(
16:09 **Jake**        well i always launch cpan as sudo then install what i need once in cpan
16:09 **Jake**        im a noob as u can see
16:09 **szabgab**     well, we are all noob in some area
16:09 **szabgab**     in most areas
16:10 **Jake**        im learning perl and loving it and padre is helping me a lot in that learning by being so nice and simple
16:10 **Jake**        ok wx installed
16:10 **Jake**        gonna launch padre now
16:10 **szabgab**     IMHO the main point of local::lib is that you don't install as root and don't mix systme installed stuff with CPAN installed stuff
16:11 **Jake**        oups
16:11 **Jake**        well it works now mate
16:11 **szabgab**     that's great to hear
16:12 **Jake**        i can launch both the cpan version from /usr/local/bin and the ubuntu release that is in /usr/bin
16:12 **Jake**        so thast the steps i would put for natty users till ubuntu fixes there release
16:12 **Jake**        thanks for the quick fix and keep up the good work Padre is awesome
16:12 **szabgab**     thanks
16:12 **szabgab**     please tell others about it


---

