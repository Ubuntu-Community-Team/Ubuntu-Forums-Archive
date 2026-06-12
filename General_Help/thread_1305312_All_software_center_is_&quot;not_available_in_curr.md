---
title: "All software center is &quot;not available in current data&quot;"
date: 2009-10-29
forum: General Help
---

### Post by RyanCoonan on 2009-10-29
I just installed 9.10 netbook remix on my Acer Aspire One.  For some reason, in the Ubuntu Software Center, every thing I could install either says "not available in current data" or "not available for your hardware architecture."  Does anybody know what is up?  It is pretty crucial for me, because I need to install the firefox java plugin to be able to login to my school's network.

---

### Post by ikacer on 2009-10-29
use the Synaptic Package Manager instead. go to:
System -> Administration -> Synaptic Package Manager

---

### Post by RyanCoonan on 2009-10-29
Screenshot attached.  I can't seem to find what I need there...?

---

### Post by jamieleshaw on 2009-10-29
for some reason it's only showing installed stuff
open up a terimal an type 'sudo apt-get update'
then try again

---

### Post by RyanCoonan on 2009-10-29
That seems to have done the trick, thanks.

I can now install things through the Software Center.

---

### Post by carl_pr on 2009-10-30
im having this same issue. i did the update command and it solved the problem. Thanks :D

---

### Post by andreibranescu on 2009-10-30
Damn, you guys are fast!

Thanks a million!

Worked like a charm.

---

### Post by amtur_poet on 2009-10-31
"sudo apt-get update" did not work for me. This is what I got as the output:
> sudo apt-get update
[sudo] password for chris: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (130.239.18.165), connection timed out [IP: 130.239.18.165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release           
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release   
  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources        
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages     
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources      
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages   
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources    
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]
Fetched 378B in 4min 57s (1B/s)
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (130.239.18.165), connection timed out [IP: 130.239.18.165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com http: [IP: 2001:6b0:e:2018::165 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


I am still unable to download programs from the Ubuntu Software Center. However, I am using the standard 32-bit version [non-netbook].

---

### Post by svaru on 2009-11-01
same thing here

W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to be.archive.ubuntu.com http:

I also noticed that programs like movie players are unable to download codecs.

Internet connection works normaly as far as I notice.

---

### Post by P4man on 2009-11-01
> **svaru said:**
> same thing here

W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to be.archive.ubuntu.com http:

I also noticed that programs like movie players are unable to download codecs.

Internet connection works normaly as far as I notice.

svaru, the belgian ubuntu mirror seems down. Go to system > adminstration > software sources and pick another one. Click other and the select best server. Picked one in the netherlands for me that works outstandingly.

---

### Post by Ampi on 2009-11-01
Reload in Synaptic Package Manager also doesn't help?

---

### Post by svaru on 2009-11-01
> **P4man said:**
> svaru, the belgian ubuntu mirror seems down. Go to system > adminstration > software sources and pick another one. Click other and the select best server. Picked one in the netherlands for me that works outstandingly.

that did the trick ... thanks

---

### Post by davoem on 2009-11-09
'sudo apt-get update' worked a charm thanks guys.

---

### Post by shahilhk on 2009-11-13
Thanks a lot my friend. I was having a similar kind of problem and the solution worked great.

---

### Post by pflood on 2009-11-22
Thanks for the help. Changing from the Irish server to the main server worked for me.

---

### Post by m3447737 on 2009-11-30
Thank you for this. I couldn't download anything either. I'm glad I joined this board. Hopefully it will make my ubuntu experience better :-)

---

### Post by thischarmingdan on 2009-11-30
> **jamieleshaw said:**
> for some reason it's only showing installed stuff
open up a terimal an type 'sudo apt-get update'
then try again
  after i type that command in, i am prompted for my password. i try to type it in but nothing comes up as i'm typing. anybody familiar with this problem?

---

### Post by jpetrides on 2010-08-08
that command worked well for me.  thanks a million!

---

