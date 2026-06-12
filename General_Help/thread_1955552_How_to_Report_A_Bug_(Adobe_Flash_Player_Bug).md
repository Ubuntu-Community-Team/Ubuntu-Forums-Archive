---
title: "How to Report A Bug (Adobe Flash Player Bug)?"
date: 2012-04-09
forum: General Help
---

### Post by tokyo-joe on 2012-04-09
I have just noticed that colors in YouTube movies played on Firefox are strange for this couple of days. This is seen on my multiple Ubuntu systems (including Lucid and Oneiric), but never seen on Windows and OpenSUSE systems.

I am afraid this is an adobe flash player plugin bug, but I don't know where and how to report this.

Where and how can I report the bug?

---

### Post by oklokl on 2012-04-09
blue skin?

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968647http://ubuntuforums.org/showthread.php?t=1075830](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968647http://ubuntuforums.org/showthread.php?t=1075830)

[https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.2.202.228-0oneiric1](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.2.202.228-0oneiric1)
[https://launchpad.net/ubuntu/+source/adobe-flashplugin](https://launchpad.net/ubuntu/+source/adobe-flashplugin)

---

### Post by tokyo-joe on 2012-04-09
> **oklokl said:**
> blue skin?
Yes, exactly.

Do you suggest perform all these command sequentially?

And, where can I get adobe flash plugin in the 2nd command("/home/*/Downloads/adobe-flashplugin-11.2.202.228/amd64/*")? From the Adobe website?

---

### Post by lovinglinux on 2012-04-09
Please don't complicate things. All you need is to disable hardware acceleration. See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

I have removed your instructions because they were incomplete and had a redundant step, since it suggests replacing the current version of flash from the repos with the same version downloaded from that PPA, which probably won't help.

---

### Post by oklokl on 2012-04-09
[https://launchpad.net/ubuntu/+source/adobe-flashplugin](https://launchpad.net/ubuntu/+source/adobe-flashplugin)
[https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.2.202.228-0oneiric1](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.2.202.228-0oneiric1)

this.. 
[https://launchpad.net/ubuntu/+archive/partner/+files/adobe-flashplugin_11.2.202.228.orig.tar.gz](https://launchpad.net/ubuntu/+archive/partner/+files/adobe-flashplugin_11.2.202.228.orig.tar.gz)

[http://forum.ubuntu-fr.org/viewtopic.php?id=604581](http://forum.ubuntu-fr.org/viewtopic.php?id=604581)

ex> sudo cp -rf..
~/Downloads/adobe-flashplugin-11.2.202.228/amd64/
?
/home/*/Downloads/
~/Downloads/..

It's ...

 Is an example.

[http://cafe.daum.net/candan/I4Zh/8](http://cafe.daum.net/candan/I4Zh/8)


[http://ubuntuforums.org/showthread.php?t=1075830](http://ubuntuforums.org/showthread.php?t=1075830)
I did not work this way

Conclusion
 My files are missing


The most recommended way.
 Try This at first.
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

sudo mkdir /etc/adobe
echo -e "EnableLinuxHWVideoDecode=1\nOverrideGPUValidation=true" | sudo tee /etc/adobe/mms.cfg > /dev/null

---

### Post by tokyo-joe on 2012-04-09
> **lovinglinux said:**
> Please don't complicate things. All you need is to disable hardware acceleration. See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)


Sorry for the confusion. I have confirmed disabling hardware acceleration works on Ubuntu 11.04. So I make this thread "solved".

---

### Post by lovinglinux on 2012-04-09
I still don't see how downloading 11.2.202.228 and replacing the same version can help. Additionally, the EnableLinuxHWVideoDecode=1 step causes flash to become unstable. The only command I see could possible help is the ffmpegcolorspace, but I can' test it, because I don't have a nVidia chipset.

The simplest solution is to disable hardware acceleration in flash.

---

### Post by lovinglinux on 2012-04-09
> **oklokl said:**
> The most recommended way.
 Try This at first.
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

sudo mkdir /etc/adobe
echo -e "EnableLinuxHWVideoDecode=1\nOverrideGPUValidation=true" | sudo tee /etc/adobe/mms.cfg > /dev/null


That fixes the blueish color but causes flash to become unstable:


> **pqwoerituytrueiwoq said:**
> There is a known issue with flash 11.2 and Nvidia on youtube (and possibly other sites)

works: unchecked + EnableLinuxHWVideoDecode=0
color fail: checked + EnableLinuxHWVideoDecode=0
unstable: checked + EnableLinuxHWVideoDecode=1 
unstable: unchecked + EnableLinuxHWVideoDecode=1

the checked status revers to this
[IMG]http://i.imgur.com/1ZBra.png[/IMG]

color fail refers to the inversion of red and blue colors

This will info will be useful for your flash add addon

Adobe has basically said they will not fix it cause they don't support linux anymore (even though they officially do for this version)

adobe bug report ids 3097844, 3077076, and 3109467

---

### Post by oklokl on 2012-04-09
bug..   -> In my case the file was not created normal.
Thank you. Advice

---

