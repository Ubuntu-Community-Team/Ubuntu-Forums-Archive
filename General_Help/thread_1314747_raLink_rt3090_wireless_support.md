---
title: "raLink rt3090 wireless support"
date: 2009-11-04
forum: General Help
---

### Post by Kamiyama on 2009-11-04
I just bought a MSI laptop and it has a raLink rt3090 wireless card in it. Ubuntu wont recognize it (I'm using 9.10), and after doing some searches I can't seem to find any sites that offer useful instructions on how to get it to work. I have seen a few threads like here:

[http://ubuntuforums.org/showthread.php?t=1313132](http://ubuntuforums.org/showthread.php?t=1313132)

Where people say that they got it to work, but I am a complete newb when it comes to using linux, and I have no clue what they are saying. If someone could provide step-by-step instructions on what to type into terminal, or what to download from where, it would be very much appreciated.

---

### Post by yoshiki2 on 2009-11-15
do u own a msi x320?

---

### Post by beyossi on 2010-01-02
it will be helpful if you will post the output of:
> lshw -C Network

I have a fit-pc2 with the same device and karmic on it and I can use it using NetworManager.
My problem is the lack of ad-hoc network support. Do you have any clue regarding the ad-hoc network?

Yossi

---

### Post by ihtarlik on 2010-02-05
> lshw -c net

 *-network UNCLAIMED
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff

---

### Post by Muhammad Takdir on 2010-05-24
i'm using lucid and got the same problem

i think you must try this packages
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

it's work for me.
:KS

---

### Post by bturig on 2010-08-30
> **Muhammad Takdir said:**
> i'm using lucid and got the same problem

i think you must try this packages
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

it's work for me.
:KS

Worked for me too!

Thanks.

---

### Post by yron87 on 2010-09-30
Worked for me too :) Thanks.

---

### Post by Edric Technology on 2010-10-14
"...you must try this packages.."

I'm with the same problem. Did you mean we just need to download and install the packages?

Thanks!

---

### Post by Edric Technology on 2010-10-26
Are you using 9.10 yet? If you are, you have to know that updating for the current last version of Ubuntu always is the best way to get problems sorted. I just did this and I found that my netbook LG X130 with a Ralink rt3090 wireless card was working fine (with 10.10). I think that update your current version will help you. So, please, try it and let us know if you got the problem solved.

---

### Post by llafar on 2010-10-26
I'm still amazed with the working answer to rt3090 support provided to me by rtomakov in this thread [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498)

It looks to be so general that should fit in any conditions, not only x64 platform. It is based on original ralink driver & compilation of kernel module.

---

### Post by Sven6210 on 2011-05-09
You can have a look on my how-to at [http://ubuntuforums.org/showthread.p...ghlight=RT3090]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090")

It also works for the RaLink RT3090, you just need to replace the "[FONT=Verdana, sans-serif]RT2860" with "RT3090".

Disadvantage of this procedure:
[/FONT]
[LIST]
[*]You need to recompile the driver each time you make a  major kernel-update. The backports I have tried so far did not work very  well
[/LIST]
Advantage of this procedure:

[LIST]
[*]On my EeeBox B202 and my friends EeePC 1015 P it works very well and reliable
[/LIST]

The manual should also work for newer releases of Ubuntu, I am still running Ubuntu 10.04 LTS on my systems.

Good luck

Sven

---

### Post by mikaelcrocker on 2011-09-09
This worked like a charm for me, found it online.  Hope it makes a few less head aches

[COLOR=#C20CB9]**sudo**[/COLOR] add-apt-repository ppa:markus-tisoft[COLOR=#000000]**/**[/COLOR]rt3090
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] update
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR] dkms rt3090-dkms

---

### Post by cirelosborn on 2011-10-14
This also solved the ubuntu 11.10 wireless problem.  Thanks alot!

---

### Post by japetko on 2012-01-27
> **Muhammad Takdir said:**
> i'm using lucid and got the same problem

i think you must try this packages
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")

it's work for me.
:KS

Worked for me too!!!

Thanks.
:popcorn:

---

### Post by hackeron on 2012-03-17
No go :(

> 
root@FitPC4:~# sudo add-apt-repository ppa:markus-tisoft/rt3090
You are about to add the following PPA to your system:
 Ralink 3090 driver
 Driver for the Raling 3090 card from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) packaged as .deb.
 More info: [https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Ckze2jscKJ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 3EE3FD4E1D44163ED06755BAFF370EF786F4C28E
gpg: requesting key 86F4C28E from hkp server keyserver.ubuntu.com
gpg: key 86F4C28E: "Launchpad PPA for Markus Heberling" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@FitPC4:~# sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
W: Failed to fetch [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by hackeron on 2012-03-17
Also, I tried compiling manually, I now see a ra0 interface but...

```

root@FitPC4:~# iwconfig ra0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Invalid argument.

```

:/

---

### Post by gandaran on 2012-03-17
> **hackeron said:**
> Also, I tried compiling manually, I now see a ra0 interface but...

```

root@FitPC4:~# iwconfig ra0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Invalid argument.

```

:/
what brand and model of laptop?
and what ubuntu version?
the ppa:markus-tisoft/rt3090 does not work for 11.10 but your wireless card should work without installing drivers on 11.10, I believe it only needs some minor fix.
see if this thread helps
[http://ubuntuforums.org/showthread.php?t=1849602](http://ubuntuforums.org/showthread.php?t=1849602)

---

### Post by i_am_lost on 2012-05-05
Download kernel source, make, and sudo make install this:

compat-wireless-3.4-rc3-1.tar.bz2

This works 100% with 12.04 LTS kernel 3xx on amd64....

There is only one driver package for the rt5890 that works in client mode for the rt3090:

[B][U][https://launchpad.net/~marko-techytalk.info/+archive/ralink-wireless]("https://launchpad.net/%7Emarko-techytalk.info/+archive/ralink-wireless")
[/U][/B]
This will enable you to connect to wireless.  Note, you will have to **_re-enable 2800 mods_**, and  >_**purge**_< any driver deb package you installed before installing the new .ko 

Do not use the manufacturers website at all... 
 
the card cost me $10... and I still feel ripped off. :KS

---

### Post by ariel on 2012-05-31
> **i_am_lost said:**
> Download kernel source, make, and sudo make install this:

compat-wireless-3.4-rc3-1.tar.bz2

This works 100% with 12.04 LTS kernel 3xx on amd64....

There is only one driver package for the rt5890 that works in client mode for the rt3090:

[B][U][https://launchpad.net/~marko-techytalk.info/+archive/ralink-wireless]("https://launchpad.net/%7Emarko-techytalk.info/+archive/ralink-wireless")
[/U][/B]
This will enable you to connect to wireless.  Note, you will have to **_re-enable 2800 mods_**, and  >_**purge**_< any driver deb package you installed before installing the new .ko 

Do not use the manufacturers website at all... 
 
the card cost me $10... and I still feel ripped off. :KS

do you still find compat wireless 3.4-rc3-1 stable for you? I have a ralink ra2860 based card, removed all linux-backports-modules-cw-* modules (which I was using, but they were unstable), installed 3.4rc3, now every now and then the connection drops and to restablish it I need to rmmod rt2800pci and the modprobe it back. It's kind of annoying.

---

