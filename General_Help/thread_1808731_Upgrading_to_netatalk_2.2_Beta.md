---
title: "Upgrading to netatalk 2.2 Beta"
date: 2011-07-20
forum: General Help
---

### Post by nkonstas on 2011-07-20
Hello,

I'm using Ubuntu 10.04 server for time machine backups (amongst other things). The newly released MacOS Lion version requires netatalk 2.2 (Beta) for time machine backups to work.

Is there a reasonably simple way to upgrade netatalk to the latest 2.2?

Thank you,
Nikos.

---

### Post by jay_cee on 2011-07-20
I am in the same boat. 

Netatalk 2.2Beta4 is in the Ocelot repository, so we may be able to install that with minimal pain. I'm going to give that a try tonight.

---

### Post by nkonstas on 2011-07-21
please let me know how you did it if you succeed :)

cheers,
nikos

---

### Post by ZTuck on 2011-07-21
FWIW, I googled netatalk 2.2 ubuntu 10.04 deb, and installed the deb file I found [here]("https://launchpad.net/~stefanor/+archive/ppa/+build/2455196"). When prompted in the expanded install dialog, I entered N twice to preserve my config files. It probably wasn't necessary, but I rebooted, and Time Machine was working and afpd -V on the command line showed I was using 2.2beta4. Hope this helps.

---

### Post by nkonstas on 2011-07-21
Brilliant! Worked for me too - thanks ZTuck!

Quick note - I had to download this file instead (amd64 arch):

[https://launchpad.net/~stefanor/+archive/ppa/+build/2455195](https://launchpad.net/~stefanor/+archive/ppa/+build/2455195)

and I installed using:

dpkg -i netatalk_2.2~beta4-0~ppa1_amd64.deb

Cheers,
Nikos.

---

### Post by haare on 2011-07-21
Worked for me too, thanks guys!

---

### Post by Sepult on 2011-07-23
=D>=D>=D>=D>=D>=D>=D>

Thanks for the link, saved me from building from scratch.

To build on what's already posted above for anyone looking for a step-by-step guide:
1.  Open a terminal shell.
2.  You need to find what architecture you have to determine what build you need.  You can get the CPU info by typing:
**less /proc/cpuinfo**
I'll assume you're using the Intel i386 build.  If not, you'll have to change the target that you download.
3. In the terminal type
**wget [https://launchpad.net/~stefanor/+archive/ppa/+build/2455196/+files/netatalk_2.2~beta4-0~ppa1_i386.deb](https://launchpad.net/~stefanor/+archive/ppa/+build/2455196/+files/netatalk_2.2~beta4-0~ppa1_i386.deb)**
Assuming, as mentioned, that you want the i386 build. 
4. In the terminal window type:
**sudo dpkg -i netatalk_2.2~beta4-0~ppa1_i386.deb**
When prompted enter your password.
5. When prompted, enter N to keep your existing config files.  Otherwise you'll have to set your shares up again.
6. Reboot the server.
7. Reboot the Mac.  OS X Lion, as reported elsewhere, apparently caches the settings for connected servers and may report that it still doesn't support the necessary "lock stealing" protocol.

_POTENTIAL ISSUES_
a) If you get an error on connection reporting "Something wrong with the volume's CNID DB, using temporary CNID DB instead.Check server messages for details!" check your AppleVolumes.default file (locate which one is being used by running sudo afpd -V).  In particular make sure the cnidscheme is set to dbd

b) If you still get the error edit AppleVolumes.default and make sure that you have tm in the options list for your TimeMachine backup mount point, ie:
/mnt/Terry TerryTM allow:terrytm cnidscheme:dbd options:usedots,upriv,tm  

Edit your /etc/netatalk/afpd.conf to have the following default options:
- -udp -noddp -uamlist uams_randnum.so,uams_dhx.so,uams_dhx2.so -nosavepassword

c) If you tried doing a backup prior to these changes make sure the disk isn't still mounted & hidden by opening Terminal on OS X and typing:
**ls /Volumes**
If you see the backup disk listed there you can unmount with 
**sudo diskutil unmountDisk /Volumes/WHATEVERTHEDISKISCALLED**

d) Make sure you don't have a share set up that overrides the defaults for your timemachine backup, eg. if you have a user account with the home directory set to the timemachine backup directory and also have a AppleVolumes.default general user entry that precedes your backup entry and doesn't include tm in the options then it will supercede your preferred settings and won't work. (Ask me how I know :( )

---

### Post by wjanik on 2011-07-23
Supposedly, a non-beta version of 2.2.0 will be [hitting Sorceforge soon]("http://www.netafp.com/open-letter-to-the-netatalk-community-501/").  How hard is it to build a package like this and produce a deb?

---

### Post by salty10is on 2011-07-24
Great work **Sepult** and **nkonstas**!!!

Works great for me.  Sepult, your troubleshooting section came in handy since nothing worked until I added the TM.

One other quick note is that if Time Machine does not see your share, make sure permissions are setup correctly on the remote folder.  I just created the folder, so I accidentally still had mine set to root.  Whoops.

Overall, pretty painless setup!  Thank you!

:guitar:

---

### Post by rbm0307 on 2011-07-31
> 3. In the terminal type
wget [https://launchpad.net/~stefanor/+arc...~ppa1_i386.deb](https://launchpad.net/~stefanor/+arc...~ppa1_i386.deb)
Assuming, as mentioned, that you want the i386 build. 
I need a URL for an AMD64-based target.  The i386 build won't install on my Ubuntu 10.04 obviously.  Is there someone out there that can post a pointer to such a debian package?  Thank you very much.

EDITED:  I found the package.  Helps a lot to read previous postings more closely than I did.  As nkonstas points out in post #5 above, It's at:

[https://launchpad.net/~stefanor/+archive/ppa/+build/2455195/+files/netatalk_2.2%7Ebeta4-0%7Eppa1_amd64.deb]("https://launchpad.net/~stefanor/+archive/ppa/+build/2455195/+files/netatalk_2.2%7Ebeta4-0%7Eppa1_amd64.deb")

Installed this version of the package and got TimeMachine on OS X Lion functioning properly.

P.S.  I guess I'm getting too old for this crap.

---

### Post by hammas on 2011-08-04
Sweet! Great work **Sepult**! 

Kinda have to agree with **wjanik**. How hard could it be for source forge to package their latest release in .deb? 

But! Just struck me, perhaps they only want people who knows what they're doing to install their beta SW? :)

Anyway my TimeMachine backup is working now, finally, and I can rest assured my data is safe.

---

### Post by Sepult on 2011-08-06
2.2.0 is now released.  You can get it at [http://netatalk.sourceforge.net](http://netatalk.sourceforge.net)  To install:
1. Backup your current configuration files, if you already have netatalk installed - they'll be located at either /etc/netatalk or /usr/local/etc/netatalk, depending on how you installed.
2. Download the netatalk source from above
3. Uncompress the files somewhere, open a terminal session, and cd into the source directory.
4. Type the following commands:
**./configure --enable-debian --enable-zeroconf**
**make**
**sudo make install**
5. When finished copy the backed-up configuration files to /usr/local/etc/netatalk
6.  To start netatalk run 
**sudo /etc/init.d/netatalk start**

Alternatively I built a .deb for i386 that should work.  You can download it from:
[http://autodidaktos.com/wp-content/uploads/2011/07/netatalk_2.2.0-1_i386.deb](http://autodidaktos.com/wp-content/uploads/2011/07/netatalk_2.2.0-1_i386.deb)

**IMPORTANT**: Note that for some reason 2.2.0 isn't providing a valid /etc/init.d/netatalk file, meaning that you won't be able to start or stop it as per normal through init.d  So if yours is referencing files in /usr/local/sbin modify it to point to /usr/sbin instead.

---

### Post by Michael Wayne on 2011-08-08
Hi,
Did anyone in this thread update to the now stable Netatalk 2.2 on Ubuntu 8.04 LTS?
Thanks

Michael

---

### Post by Cantello on 2011-08-10
Is there a .deb available for AMD64 architecture somewhere?

When trying to compile it does not find zeroconf capabilities although everything should be installed for that.

---

### Post by Glycerine1 on 2011-08-14
> **Cantello said:**
> Is there a .deb available for AMD64 architecture somewhere?

When trying to compile it does not find zeroconf capabilities although everything should be installed for that.

You likely need to install the Avahi dev libs.  

```
apt-get install libavahi-client-dev
```

Now configure again and it should work.

---

### Post by Jayphen on 2011-08-16
> **Sepult said:**
> 
Alternatively I built a .deb for i386 that should work.  You can download it from:
[http://autodidaktos.com/wp-content/uploads/2011/07/netatalk_2.2.0-1_i386.deb](http://autodidaktos.com/wp-content/uploads/2011/07/netatalk_2.2.0-1_i386.deb)


I tried using your deb, but get 

```
trying to overwrite '/usr/include/netatalk/at.h', which is also in package libc6-dev 2.13-0ubuntu13
```

---

### Post by wjanik on 2011-08-17
Has anyone tried Stefano Rivera's latest builds ([https://launchpad.net/~stefanor/+archive/ppa]("https://launchpad.net/~stefanor/+archive/ppa"))?  They were posted on the 15th, but there isn't one for Natty.  I've been having Time Machine troubles on one of my Macs that I'm pretty sure are due to 2.2.0Beta4 flakiness.  I'd like to move to 2.2.0, but fear putting in a package that wasn't built for the version I'm running.  Anyone know if the 10.10 or 11.10 packages are compatible with 11.04?

---

### Post by desq on 2011-08-17
I second that. 

Could somebody with more skill than me provide a Netatalk 2.2 (Release) 
AMD64 Package for Natty. I´m having also Issues with 2.2Beta4 and Time Machine.

Thank you!

desq


> **wjanik said:**
> Has anyone tried Stefano Rivera's latest builds ([https://launchpad.net/~stefanor/+archive/ppa]("https://launchpad.net/~stefanor/+archive/ppa"))?  They were posted on the 15th, but there isn't one for Natty.  I've been having Time Machine troubles on one of my Macs that I'm pretty sure are due to 2.2.0Beta4 flakiness.  I'd like to move to 2.2.0, but fear putting in a package that wasn't built for the version I'm running.  Anyone know if the 10.10 or 11.10 packages are compatible with 11.04?

---

### Post by kyleh0000 on 2011-08-17
> **desq said:**
> 

Has anyone tried Stefano Rivera's latest builds ([https://launchpad.net/~stefanor/+archive/ppa)?](https://launchpad.net/~stefanor/+archive/ppa)?) They were posted on the 15th, but there isn't one for Natty. I've been having Time Machine troubles on one of my Macs that I'm pretty sure are due to 2.2.0Beta4 flakiness. I'd like to move to 2.2.0, but fear putting in a package that wasn't built for the version I'm running. Anyone know if the 10.10 or 11.10 packages are compatible with 11.04?

desq

ok I got the above ppa version installed (I'm using 10.04 Server) and it all installed fine, however the afpd won't start, I have been trying to find any info in the logs about it but the log files all look fine, its just the daemon doesn't start and i can't telnet to the afp port on the machine

has anyone got this working?

Thanks all!

---

### Post by Cantello on 2011-08-18
> **Glycerine1 said:**
> You likely need to install the Avahi dev libs.  

```
apt-get install libavahi-client-dev
```

Now configure again and it should work.

Yep, worked, thanks!

Now off to solve the remaining problems with TimeMachine and netatalk... :-/

---

### Post by Jayphen on 2011-08-18
I managed to install 2.2, but Time Machine still gave the same error…

---

### Post by wjanik on 2011-08-19
I gave the Maverick build (even though I'm running Natty) from Stefano Rivera's PPA a go, and so far so good.  Earlier in the week I had to "bootstrap" Time Machine by backing up to a store on another Mac, then transferring the sparse bundle to my netatalk share.  It's been happy since then, so I can't tell if the upgrade to 2.2.0 from 2.2.0beta4 made a difference or not.  The good news is, it hasn't (yet) caused any new problems ;)

---

### Post by mobodo on 2011-08-21
Thanks all for the info.  I got it Time Machine working again on Lion and an x64 build of Ubuntu 11.04 by following these steps:

 - I tried to install the 2.2.0 package from [https://launchpad.net/~stefanor/+archive/ppa](https://launchpad.net/~stefanor/+archive/ppa) (direct link for amd64: [https://launchpad.net/~stefanor/+archive/ppa/+files/netatalk_2.2.0-0ppa2_amd64.deb](https://launchpad.net/~stefanor/+archive/ppa/+files/netatalk_2.2.0-0ppa2_amd64.deb))

There were two missing dependencies: libgcrypt11 and libdb5.1 which were installed but not at the correct version.  libgcrypt11 was at 1.4 and 1.5 was required.

- I installed libgcrypt11 1.5.0-1 from here: [http://ubuntu.wallawalla.edu/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.5.0-1_amd64.deb](http://ubuntu.wallawalla.edu/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.5.0-1_amd64.deb) since it could not be obtained using apt-get (only 1.4 was available)

- I tried to get libdb5.1 using apt-get, but it failed on the dependency for libgcrypt11-dev (version 1.4 installed, 1.5 required)
- Installed libcrypt11-dev 1.5.0-1 from here [http://ubuntu.wallawalla.edu/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11-dev_1.5.0-1_amd64.deb](http://ubuntu.wallawalla.edu/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11-dev_1.5.0-1_amd64.deb)

After that, libdb5.1 installed without any problem (apt-get) and the netatalk 2.2.0 package also installed without problem.  Time Machine immediately recognized the network drive.

---

### Post by jhd121 on 2011-08-23
I am truly at a loss.  Everything appears to be installing correctly (AMD64) and I've updated  but I am still getting the same Time Machine error.  Here is the output from afpd -V:

```
afpd 2.2-beta4 - Apple Filing Protocol (AFP) daemon of Netatalk

This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 2 of the License, or (at your option) any later
version. Please see the file COPYING for further information and details.

afpd has been compiled with support for these features:

        AFP3.x support:    Yes
        TCP/IP Support:    Yes
DDP(AppleTalk) Support:    No
         CNID backends:    dbd last tdb 
           SLP support:    No
      Zeroconf support:    No
  TCP wrappers support:    Yes
         Quota support:    Yes
   Admin group support:    Yes
    Valid shell checks:    Yes
      cracklib support:    Yes
        Dropbox kludge:    No
  Force volume uid/gid:    No
           ACL support:    No
            EA support:    ad | sys
          LDAP support:    No

             afpd.conf:    /etc/netatalk/afpd.conf
   AppleVolumes.system:    /etc/netatalk/AppleVolumes.system
  AppleVolumes.default:    /etc/netatalk/AppleVolumes.default
    afp_signature.conf:    /etc/netatalk/afp_signature.conf
      afp_voluuid.conf:    /etc/netatalk/afp_voluuid.conf
         afp_ldap.conf:    not supported
       UAM search path:    /usr/lib/netatalk/
  Server messages path:    /etc/netatalk/msg/
              lockfile:    /var/run/afpd.pid

```

---

### Post by t.moro on 2011-08-28
Hi, i've tried to compile the final version, also the link for the 2.2beta4 package is broken (file deleted?)

I run the command
```
./configure --enable-debian --enable-zeroconf
```

and this is the error

```

checking whether to enable Zerconf support... no
configure: error: Zeroconf installation not found
```

what i've to do? thanks

---

### Post by neptune39 on 2011-08-28
> **t.moro said:**
> Hi, i've tried to compile the final version, also the link for the 2.2beta4 package is broken (file deleted?)

I run the command
```
./configure --enable-debian --enable-zeroconf
```

and this is the error

```

checking whether to enable Zerconf support... no
configure: error: Zeroconf installation not found
```

what i've to do? thanks

I believe you can fix this by installing libavahi-client-dev and then compiling again

These are the things I install before compiling
libdb4.8-dev libcrack2-dev libssl-dev libgcrypt-dev libavahi-client-dev

My big problem was not having libgcrypt-dev which allows the security required in lion, otherwise when trying to connect it will tell you the service is out of date. Most tutorials i've tried miss this package.

---

### Post by neptune39 on 2011-08-28
> **Jayphen said:**
> I managed to install 2.2, but Time Machine still gave the same error&#8230;

Try:
sudo apt-get install libgcrypt-dev 

and then go through the 2.2 install again.

The key is that the output from ./configure shows that DHX2 (SHADOW) will be available:

Configure summary:
    Install style:
         debian

    AFP:
         AFP 3.x calls activated: 
         Extended Attributes: ad | sys

    CNID:
         backends:  dbd last tdb

    UAMS:
         DHX     ( SHADOW)
         **DHX2    ( SHADOW)**
         RANDNUM ( SHADOW)
         passwd  ( SHADOW)
         guest
    
Its that extra security that was added to Lion I believe.

---

### Post by vukers on 2011-08-29
I upgraded to the newest version, but every time I do a restart on the netatalk service, I see the following error in the log:

```
Aug 28 22:51:47.464892 afpd[13536] {status.c:707} (I:AFPDaemon):  "ComputerName"'s signature is  XXXXXXXXXXXXXXX
Aug 28 22:51:47.465230 afpd[13536] {dsi_tcp.c:346} (I:DSI): dsi_tcp_init: bind: Address already in use

Aug 28 22:51:47.465266 afpd[13536] {dsi_tcp.c:346} (I:DSI): dsi_tcp_init: bind: Address already in use

Aug 28 22:51:47.465279 afpd[13536] {dsi_tcp.c:360} (E:DSI): dsi_tcp_init: no suitable network config for TCP socket
Aug 28 22:51:47.465293 afpd[13536] {afp_config.c:361} (E:AFPDaemon): main: dsi_init: Address already in use
Aug 28 22:51:47.465514 afpd[13536] {auth.c:1165} (I:AFPDaemon): uam: uam not found (status=-1)
Aug 28 22:51:48.512281 afpd[13536] {fault.c:122} (S:Default): ===============================================================
Aug 28 22:51:48.512327 afpd[13536] {fault.c:123} (S:Default): INTERNAL ERROR: Signal 11 in pid 13536 (2.2-beta4)
Aug 28 22:51:48.512337 afpd[13536] {fault.c:124} (S:Default): ===============================================================
Aug 28 22:51:48.512679 afpd[13536] {fault.c:96} (S:Default): BACKTRACE: 7 stack frames:
Aug 28 22:51:48.512694 afpd[13536] {fault.c:102} (S:Default):  #0 /usr/sbin/afpd(netatalk_panic+0x1c) [0x7ff70533d88c]
Aug 28 22:51:48.512704 afpd[13536] {fault.c:102} (S:Default):  #1 /usr/sbin/afpd(+0x4e98c) [0x7ff70533d98c]
Aug 28 22:51:48.512714 afpd[13536] {fault.c:102} (S:Default):  #2 /lib/libc.so.6(+0x33c20) [0x7ff703eaec20]
Aug 28 22:51:48.512723 afpd[13536] {fault.c:102} (S:Default):  #3 /usr/sbin/afpd(configinit+0x1d4) [0x7ff705302c34]
Aug 28 22:51:48.512733 afpd[13536] {fault.c:102} (S:Default):  #4 /usr/sbin/afpd(main+0x2f1) [0x7ff705300211]
Aug 28 22:51:48.512742 afpd[13536] {fault.c:102} (S:Default):  #5 /lib/libc.so.6(__libc_start_main+0xfe) [0x7ff703e99d8e]
Aug 28 22:51:48.512752 afpd[13536] {fault.c:102} (S:Default):  #6 /usr/sbin/afpd(+0x11775) [0x7ff705300775]
```

Prior to installing, I did an "apt-get --purge remove netatalk" on the previous version, and after installing I confirmed the installed version using "dpkg -s netatalk | grep -i version". Any ideas?

Thanks!

---

### Post by vukers on 2011-08-30
**Update:**
Fixed by using:
```
netstat -a | grep 548
```
to find the process that was listening, and kill it.

---

### Post by drowsyhaze on 2011-09-19
Hi! I installed 2.2 using stefanor's ppa but am still having no joy on my lion installation (error 45 time machine lock sealing is what my mac's console says)... any thoughts?

---

### Post by skyplex on 2011-10-05
I updated to Netatalk 2.2.0 [ Not Beta] from this site [http://www.andypeace.com/netatalk.html](http://www.andypeace.com/netatalk.html)
this download opened in Ubuntu Software Centreand I pressed the Update button. I also checked the BerkeleyDB 4.8 update.
The update went smoothly. My thanks to Andy Peace.
This is the print out of afpd -V in the terminal.
```
~$ afpd -V
afpd 2.2.0 - Apple Filing Protocol (AFP) daemon of Netatalk

This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 2 of the License, or (at your option) any later
version. Please see the file COPYING for further information and details.

afpd has been compiled with support for these features:

      AFP3.x support:    Yes
       TCP/IP Support:    Yes
DDP(AppleTalk) Support:    Yes
        CNID backends:    dbd last tdb
          SLP support:    No
     Zeroconf support:    Yes
 TCP wrappers support:    Yes
        Quota support:    Yes
  Admin group support:    Yes
   Valid shell checks:    Yes
     cracklib support:    Yes
       Dropbox kludge:    No
 Force volume uid/gid:    No
          ACL support:    No
           EA support:    ad | sys
         LDAP support:    No

            afpd.conf:    /etc/netatalk/afpd.conf
  AppleVolumes.system:    /etc/netatalk/AppleVolumes.system
 AppleVolumes.default:    /etc/netatalk/AppleVolumes.default
   afp_signature.conf:    /etc/netatalk/afp_signature.conf
     afp_voluuid.conf:    /etc/netatalk/afp_voluuid.conf
        afp_ldap.conf:    not supported
      UAM search path:    /usr/lib/netatalk/
 Server messages path:    /etc/netatalk/msg/
            lockfile:    /var/run/afpd.pid
```
I have 5 AFP shares.

When I mount the shares on the Mac Lion I now get an error message:
> "Something wrong with the volume's CNID DB, using temporary CNID DB
instead.Check server messages for details. Switching to read-only mode."

How can I fix this problem?

I am not sure how to: "Check server messages for details"

I am using CNID backend dbd.

Thanks, &#8230;Jeremy K Sellors

---

### Post by skyplex on 2011-10-05
Ah, I see use the Log File Viewer to read Logs.
The volumes do not support Extended Attributes.
```
iBuntu afpd[2725]: volume "NAS4" does not support Extended Attributes, using ea:ad instead
```The volumes are formatted ext4
.
Can I change the volumes to support Extended Attributes without losing the data?

Thanks again,  Jeremy

---

### Post by dmovad on 2011-10-06
I followed the instructions on this blog:

[http://langit.wordpress.com/2011/09/14/share-folder-in-ubuntu-11-04-for-mac-osx-lion/](http://langit.wordpress.com/2011/09/14/share-folder-in-ubuntu-11-04-for-mac-osx-lion/)

The author is using the ext4 filesystem and he seems pretty up on this stuff so you may wish to post your question to him if you don't get any good replies here.

I am using xfs and following this blog worked perfectly in my case.

Good Luck...

---

### Post by EGJason on 2012-04-18
> **Sepult said:**
> =D>=D>=D>=D>=D>=D>=D>


_POTENTIAL ISSUES_
a) If you get an error on connection reporting "Something wrong with the volume's CNID DB, using temporary CNID DB instead.Check server messages for details!" check your AppleVolumes.default file (locate which one is being used by running sudo afpd -V).  In particular make sure the cnidscheme is set to dbd



I simply wanted to follow up on this error message (as this thread is one of the first to pop up in search engines).  If you receive this error (which can happen with an upgrade as did mine:

Simply remove or re-name the .AppleDB in the root directory of the share.  it will simply rebuild upon next restart of netatalk.

rm -rf .AppleDB

---

