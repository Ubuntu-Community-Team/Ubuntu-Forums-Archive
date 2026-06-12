---
title: "Maintenance of Ubuntu"
date: 2009-12-06
forum: General Help
---

### Post by stealth_007 on 2009-12-06
Hi,

I am now using Ubuntu 9.10 as the only OS on my Desktop completely switched from Windows, from past 7-8 years I was using Windows.

When using windows I used to install additional softwares to maintain the OS like, Registry Editor, Avast Antivirus, De-fragment Utility for HDD, Zone alarm Firewall, Windows Defender...etc

So what are things I should keep in mind for Linux Ubuntu, or what are the other softwares I should install for all these things.

Specially for De-fragmentation of HDD as I am using 1TB HDD...So don't want to take risk.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-12-06
Back in Time for backup

---

### Post by MelDJ on 2009-12-06
i would say bleachbit. it clears off clutter like ccleaner. its available in the repo

---

### Post by sikander3786 on 2009-12-06
Ubuntu is a world totally different of Windows. Here you do not have to fear any Viruses, Registery Editor, Windows Defender etc. 

One thing to note is never try to log in as "Super User". Just use your normal account to log in. Secondly never trust any software from anyother channel except the repositories as all software is present in the Ubuntu Software Channel. If ever you have to install some other software, do it only if you trust the provider.

You might also hurt your Ubuntu by typing dangerous commands. For a list of dangerous commands look here.

[http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)

In case of antivirus software, you don't need to have one for the security of your system. If you have to oftenly copy files from Windows to Ubuntu, and forward them to your friends, then for the security of other Windows PCs you might like to add ClamAV which is present in the repositories.

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

The firewall is already configured for your safety. Still if you want to configure here is how to do it.

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

Disk defragmentation is a good habit (but I think on NTFS and FAT only). Take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=407889](http://ubuntuforums.org/showthread.php?t=407889)

Hope I was right and helped you.

---

### Post by Shazaam on 2009-12-06
Since ext3/4 are journaling filesystems file fragmentation is not such a problem. You can still defragment but it's not as important with linux as it is with that other "unamed" filesystem...
[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)
There are anti-virus apps for linux. They are mostly used to keep you from accidently passing on bad stuff to Windows users as said bad stuff is usually harmless to linux.
Linux comes with a "firewall" called ufw built in. You can either configure it by command line or with gui "frontends" like gufw, Firestarter, and others. If you really want to get into the nuts and bolts of ufw do a search for iptables.
On my system the only thing I run are the usual privacy/blocking extensions for Firefox such as NoScript and AddBlock Plus.
As far as history/cookie/package/junk cleaners and such there are a few in Synaptic. About the only things that you might want to clean up (if you need the space) are apt's package cache and old log files. I have NOT seen the usual Windows type of slowdown using linux so I just leave it alone.
When linux captures a wider audience the malware threat may change for the worst. As long as you don't set your box up to always run as root you should be fine.

---

### Post by sikander3786 on 2009-12-06
> **Shazaam said:**
> Since ext3/4 are journaling filesystems file fragmentation is not such a problem. You can still defragment but it's not as important with linux as it is with that other "unamed" filesystem...
[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)
There are anti-virus apps for linux. They are mostly used to keep you from accidently passing on bad stuff to Windows users as said bad stuff is usually harmless to linux.
Linux comes with a "firewall" called ufw built in. You can either configure it by command line or with gui "frontends" like gufw, Firestarter, and others. If you really want to get into the nuts and bolts of ufw do a search for iptables.
On my system the only thing I run are the usual privacy/blocking extensions for Firefox such as NoScript and AddBlock Plus.
As far as history/cookie/package/junk cleaners and such there are a few in Synaptic. About the only things that you might want to clean up (if you need the space) are apt's package cache and old log files. I have NOT seen the usual Windows type of slowdown using linux so I just leave it alone.
When linux captures a wider audience the malware threat may change for the worst. As long as you don't set your box up to always run as root you should be fine.

Seems like we both were typing at the same time and were thinking almost the same:D. What a great experience.

---

### Post by stealth_007 on 2009-12-06
Thank you very much for all, information was very useful and I understood that we don't need any thing like, Antivirus, De-fragmentation, Windows Defender...etc. Right? 

Linux Ubuntu is totally the best....

Then I don't understand why people are still paying and using Windows XP, Vista, 7even...

---

### Post by sikander3786 on 2009-12-06
> **stealth_007 said:**
> Thank you very much for all, information was very useful and I understood that we don't need any thing like, Antivirus, De-fragmentation, Windows Defender...etc. Right? 

Linux Ubuntu is totally the best....

Then I don't understand why people are still paying and using Windows XP, Vista, 7even...

The reason why people are using Windows still is I think that they are not willing to go some other route. Switching to some other OS will surely take some of your time to adjust. I know many people who are surprised to see my Ubuntu PC do some tricks like Wobbly Windows, Cool Compiz Effects, all the free software and the productivity of Ubuntu, yet they keep on saying "Oh it is a lot difficult to do this, this and this on Linux". The real problem is that they are familiar to Windows. If they were using Linux since the time they started using computer, then they would've faced the same difficulty in switching to Windows. They don't want to change the route they know very well however they know that it will be a far safer and promising route. It will take some time for those people to shift to Linux.

See my signature? :D

---

