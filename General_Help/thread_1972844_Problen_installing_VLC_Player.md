---
title: "Problen installing VLC Player"
date: 2012-05-03
forum: General Help
---

### Post by Mfkrmfkr on 2012-05-03
I cant install VLC player in ubuntu 12.04   
When I try to install in sofware center it says:

Package dependencies cannot be resolved
The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.1+git20120502+r198-0~r36~precise1) but 2.0.1+git20120502+r198-0~r36~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.1ubuntu1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.1ubuntu1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.1 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.1 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

And if I try to install in terminal it says:
The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.0.1+git20120502+r198-0~r36~precise1) but it is not going to be installed
       Depends: libvlccore5 (>= 2.0.0) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.1+git20120502+r198-0~r36~precise1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.1+git20120502+r198-0~r36~precise1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Pease help!

---

### Post by mc4man on 2012-05-04
You are using this ppa & the new vlc 64 bit packages aren't built yet. The i386 ones are. So if on a 32 bit install try running 
sudo apt-get update
If on a 64 bit install wait till the builds are finished

[https://launchpad.net/~videolan/+archive/stable-daily](https://launchpad.net/~videolan/+archive/stable-daily)

pending
[https://launchpad.net/~videolan/+archive/stable-daily/+builds?build_state=pending](https://launchpad.net/~videolan/+archive/stable-daily/+builds?build_state=pending)

page were yesterdays builds (r198) are if you can't wait
[https://launchpad.net/~videolan/+archive/stable-daily/+builds?build_state=built](https://launchpad.net/~videolan/+archive/stable-daily/+builds?build_state=built)

---

### Post by Mfkrmfkr on 2012-05-04
> **mc4man said:**
> You are using this ppa & the new vlc 64 bit packages aren't built yet. The i386 ones are. So if on a 32 bit install try running 
sudo apt-get update
If on a 64 bit install wait till the builds are finished

[https://launchpad.net/~videolan/+archive/stable-daily]("https://launchpad.net/%7Evideolan/+archive/stable-daily")

pending
[https://launchpad.net/~videolan/+archive/stable-daily/+builds?build_state=pending]("https://launchpad.net/%7Evideolan/+archive/stable-daily/+builds?build_state=pending")

page were yesterdays builds (r198) are if you can't wait
[https://launchpad.net/~videolan/+archive/stable-daily/+builds?build_state=built]("https://launchpad.net/%7Evideolan/+archive/stable-daily/+builds?build_state=built")


Thank You!
Problem fix

Im on a 64bit machine
I try to reinstall but still get the same problem so what I did was:

1- Delete the vlc ppas in System > Administration > Software Sources 
2- Then: sudo apt-get remove --purge vlc
3- install VLC player from the software center

---

