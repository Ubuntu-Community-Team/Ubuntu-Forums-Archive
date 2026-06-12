---
title: "Installing lib32stdc++ on Ubuntu 11.04 64-bit Server"
date: 2011-07-19
forum: General Help
---

### Post by Using Debian on 2011-07-19
I am attempting to get a Brother HL-2270DW B&W Laser Printer working (USB/LAN/Wifi Capable) and on my journey of instructions from the brother website, it stated there are a few "Pre-required Procedures"

> 
# Pre-required Procedure (4)
    Related distributions
    **Debian, Ubuntu**
    Related products/drivers
    **printer/PC-FAX drivers**
    Requirement (superuser authorization is required to run the command) 
    **"mkdir /var/spool/lpd" command is required if the folder does not exist.**


# Pre-required Procedure (5)
    Related distributions
    **Debian 64 bit version, Ubuntu 64 bit version**
    Related products/drivers
    **printer/PC-FAX drivers**
    Requirement
    **ia32-libs or lib32stdc++ is required to be installed. **
I created that suggested folder and I installed the **ia32-libs** package and it listed **lib32stdc++** as one of the other packages that would be installed as well.


when I attempted to run:
> 
user@domain:~$** sudo dpkg  -i  --force-all cupswrapperHL2270DW-2.0.4-2.i386.deb**
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 53674 files and directories currently installed.)
Preparing to replace cupswrapperhl2270dw:i386 2.0.4-2 (using cupswrapperHL2270DW-2.0.4-2.i386.deb) ...
Unpacking replacement cupswrapperhl2270dw:i386 ...
dpkg: dependency problems prevent configuration of cupswrapperhl2270dw:i386:
 cupswrapperhl2270dw:i386 depends on libc6 (>= 2.3.4-1).
dpkg: error processing cupswrapperhl2270dw:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupswrapperhl2270dw:i386
user@domain:~$
... that was the result.  

I did a test with this command:

> 
[IMG]http://www.goldcoast-affiliates.com/ubuntuforums/cli-ref-2011-07-19-00001.jpg[/IMG]
... those were the results

So, next I thought I would attempt to install **lib32stdc++** by itself, and the following resulted:

> 
user@domain:~$ **sudo apt-get install lib32stdc++**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'lib32stdc++6' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.5-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.4-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.0-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.1-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.2-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.3-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-dbg' for regex 'lib32stdc+'
lib32stdc++6 is already the newest version.
lib32stdc++6 set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
** [COLOR=Red]lib32stdc++6-4.5-dbg : Conflicts: lib32stdc++6-4.4-dbg but 4.4.5-15ubuntu1 is to be installed[/COLOR]**
E: Broken packages
user@domain:~$
and with that, I am at a standstill on next-best-move

I love struggling and learning or basically "failing my way to the top" :) but I figured this would be a good time to ask for a little direction.

---

### Post by Using Debian on 2011-07-20
So, installing 11.04 Server 64-bit on another system to see if I can duplicate the issue on the fresh install, hopefully I will see the same results, or even better, no issues at.

Any suggestions while I go experiment?  Thanks

---

### Post by Using Debian on 2011-07-22
*bumped*

---

### Post by Ars Poetica on 2011-09-02
*bump*

edit: Similar problem here

but here is something that I don't really understand to well


> :~/Downloads$ sudo rpm -ihv --nodeps mfc9560cdwlpr-1.1.1-5.i386.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
Preparing...                ########################################### [100%]
        package mfc9560cdwlpr-1.1.1-5.i386 is already installed

:~/Downloads$ sudo rpm -e --nodeps mfc9560cdwlpr-1.1.1-5.i386.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: package mfc9560cdwlpr-1.1.1-5.i386.rpm is not installed

:~/Downloads$ rpm -qa | grep mfc
mfc9560cdwlpr-1.1.1-5.i386
:~/Downloads$

---

### Post by jimijames on 2011-11-21
I don't know if anybody still needs help with this, but the brother site says that you can install "ia32-libs" *or* "lib32stdc++"

I haven't set it up yet, but when I do I'll edit this post if it works.

In the meantime, ```
sudo apt-get install ia32-libs
``` worked.

Edit: Okay, got it working.

Step 1: Turn on and plug in the printer (I'm using one connected via a home network, so I just had to turn it on)

Step 2: Install ia32-libs (above)

Step 3: Download the brother drivers here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

Get both the cupswrapper driver and the lpr driver - the 'deb' ones because we're using debian I believe.


Step 4:  Open terminal, navigate to the directory

 - What I did here is create a folder in 'downloads' titled 'drivers'

To navigate to the directory, you type in 'cd' and the name, so in this example ```
cd Downloads/drivers
```

Step 5:  install the drivers (using dpkg), lpr first

```
sudo dpkg -i --force-all hl2270dwlpr-2.1.0-1.i386.deb
```

 - for me, the driver was called 'hl2270dwlpr-2.1.0-1.i386.deb, so if you have a different one, just change the part in front of the .deb

 - then install the cupswrapper driver - command would be the same code as above, but again with the part directly in front of the .deb changed to the name of the driver.

Step 6:  If your printers are on a wireless network, open up the printing app, go to 'properties', then 'settings', then 'Device URI'

I know this is probably obvious for most of you guys, but I figured if anything it should come up on a google search and help people like me who are technology illiterate.  There are also instructions on the Brother site, but not as dumbed down as these.

Also, this is for oneric ocelot, so YMMV just to be safe.

---

