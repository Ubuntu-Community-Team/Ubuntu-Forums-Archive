---
title: "Installation failure: .deb package"
date: 2011-04-12
forum: General Help
---

### Post by fantab on 2011-04-12
I am having problem installing** .deb package for my wireless Broadband Modem**. I have downloaded the linux package (ZTE_AC2776_linux.zip) from the service provider's website, [http://www.reliancenetconnect.co.in/downloads.html](http://www.reliancenetconnect.co.in/downloads.html), and inside the .zip package is UBUNTU.deb.

I have tried to install this **.deb package through GDEBI**, however the installation was NOT successful. I have _attached the Screen Shots _of the reported error in hope that it will help us understand what is going wrong with the installation.

Please help me install my Wireless Broadband Modem and use it on Ubuntu 10.10. (32-bit)

Regards.

---

### Post by earthpigg on 2011-04-12
ill take a look at that .deb, i have a feeling it is something with that.

---

### Post by earthpigg on 2011-04-12
are you on 64-bit ubuntu, or 32? the .deb is for 32-bit only.

---

### Post by earthpigg on 2011-04-12
that package is wonky/broken.

gdebi returned no errors on my on my system, but check this out:

```
[chris: ~]$ sudo apt-get remove --purge crossplatformui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  crossplatformui
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
**1 not fully installed or removed.**
**After this operation, _*0B*_ of additional disk space will be used.**
Do you want to continue [Y/n]? 
```

when i eventually figure out how to repair the damage done by this package, i'll let you know. ha.

---

### Post by earthpigg on 2011-04-12
paying more attention to the error, as expressed by synaptic:(Reading 

```
database ... 356347 files and directories currently installed.)
Removing crossplatformui ...
***ztemtvcdromd: no process found***
dpkg: error processing crossplatformui (--purge):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

so, yup, i have no idea besides the already established "the package is broken". i also don't suggest anyone else mess with this package unless they really mean it.

---

### Post by fantab on 2011-04-12
> **earthpigg said:**
> so, yup, i have no idea besides the already established "the package is broken". i also don't suggest anyone else mess with this package unless they really mean it.

**Thank You earthpigg** for your effort.

Can somebody else please look into it... without my wireless BROADBAND MODEM I cant use the Internet while using ubuntu. :sad:  :sad:

---

### Post by earthpigg on 2011-04-12
right, hadn't run this one till just now (update manager suggested it, after the partial upgrade dialog):

```
[chris: ~]$ sudo apt-get install -f
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  simgear1.9.1 libftgl2 gettext libboost-signals1.40.0 libunistring0
  libboost-filesystem1.40.0 libboost-system1.40.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  crossplatformui
0 upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 356347 files and directories currently installed.)
Removing crossplatformui ...
ztemtvcdromd: no process found
dpkg: error processing crossplatformui (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)
[chris: ~]$ 

```

---

### Post by bodhi.zazen on 2011-04-12
Looks like a very bad .deb =)

Do you know how to manually fix that ?

See this blog for some hints, post back if you can not fix it.

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by earthpigg on 2011-04-12
thanks.

```
[chris: /var/lib/dpkg/info]$ ls | grep crossplatform
crossplatformui.conffiles
crossplatformui.list
crossplatformui.md5sums
crossplatformui.postinst
crossplatformui.postrm
[chris: /var/lib/dpkg/info]$ sudo rm crossplatformui.*
[chris: /var/lib/dpkg/info]$ sudo dpkg --remove --force-remove-reinstreq crossplatformui
(Reading database ... 
dpkg: warning: files list file for package `crossplatformui' missing, assuming package has no files currently installed.
(Reading database ... 356338 files and directories currently installed.)
Removing crossplatformui ...
[chris: /var/lib/dpkg/info]$ 

```

let's hope that worked.

---

### Post by bodhi.zazen on 2011-04-12
Looks as if that solved your problem.

---

### Post by earthpigg on 2011-04-12
apt-get update && apt-get upgrade ran fine and returned no errors. ill call this solved for me. thank you, bodhi.zazen.

@fantab:

i believe the solution for you is to:

[LIST]
[*]when i googled initially, i think i found some people saying this piece of hardware worked OOB for them. try having it plugged in when you first turn on your computer, see if the kernel detects it and loads needed module. (i should have suggested this earlier, but was distracted. :P ) if that doesn't work...

[*]create a new thread, specifically soliciting a "packaging guru" here on the forums to see if they can fix this broken package for you and others with this hardware. i'd put the term "packaging guru" in the thread title - try to get the attention of someone that wants a challenge. point them back to this thread.

[*]e-mail the company, ask **them** to fix **their** broken .deb package. truly, any company ought to regard officially supported software having a fundamentally broken installer as an embarrassment. 
[/LIST]

it is also unfortunate that you where perhaps led into purchasing hardware that claimed to support ubuntu, when that was clearly misinformation (intentional or otherwise).

---

### Post by bodhi.zazen on 2011-04-12
> **earthpigg said:**
> apt-get update && apt-get upgrade ran fine and returned no errors. ill call this solved for me. thank you, bodhi.zazen.


You are most welcome. Thank you for trying to assist with this. Breaking apt-get often a bit of an inconvenience ;)

---

### Post by fantab on 2011-04-13
Thank you all for your valuable support.

I have myself googled for the problem and found this [http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html](http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html)

What I have figured out so far is that its got something to do with the **usb-modeswitch**, the version that is supplied with the ZTE-AC2726 modem is 1.0.2-1 (i386) while the version which is packed with Ubuntu 10.10 is 1.1.4-1 (i386).

The following is what I found from the above link....

[HTML]Anonymous said...   I have recently successfully installed ZTE AC2726 in my UBUNTU 10.10  Netbook edition in CityCell network of Bangladesh. It is working nicely.  Used below simple method:

1. Plugged the device in USB.
2. Opened the Terminal and typed lsusb
3. I found the name ":fff1" ZTE modem in one of the listed usb's. (means it is detected!)
4. Then again typed wvdialconf in the terminal.
5. Whether it says wvdialcof is installed/not installed, I just typed and tried several times.
6. Than I found the "Mobile Broadband" in the wirless network listing.
7. When I clicked that a dialogue came showing list of countries and list of service providers. I just selected.
8. But still user name and pass not asked!
9. To correct this I went to "Network connections" from the menu.
10. There I found Mobile Broadband tab again. I have clicked the edit and found the user name and pass options. Just provided.
11. Then again from wireless menu, I clicked to connect the mobile broadband. And it started working!![/HTML]
Also I am having problem removing "zteusbserial 1.0.1"---

Request: I am a Linux(Ubuntu) noob. So please treat me as one when Posting and explaining codes. I will greatly appreciate and will find if very useful if help can be provided in simple steps which I can easily follow and implement.

Thank you for your patience and time.

---

