---
title: "embedded youtube not working"
date: 2009-11-26
forum: General Help
---

### Post by extendedping on 2009-11-26
Hi I cut the cord recently and am just using ubuntu 9.10, having a very good experience overall (even got my firepod soundcard working). one issue is youtube, so I don't really know if its a youtube, ubuntu or firefox issue. anyway when I go to play embedded video's they just don't play. I have centos 5.4 running on my laptop and I have no issues there. also in youtube on my ubuntu 9.10 desktop I cannot enter full screen. here is my uname -a 

brad@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64 GNU/Linux

and my firefox version is 3.5.5

thanks I have to imagine I am not the only one having an issue, also as you can see it is a rt kernel. thanks in advance.

---

### Post by extendedping on 2009-11-27
no thoughts?

---

### Post by extendedping on 2009-11-27
removed and reinstalled flash plugin installer and now can run embedded videos. go figure.

---

### Post by extendedping on 2009-11-28
I take it back, it works on some sites not on most. my laptop dual booting xp and centos can play all embedded youtube video's, how annoying, rusty old centos  works but ubuntu does not :(

btw here is an example, this guitar video works on both xp and centos but not on ubuntu/firefox 3.5.5
[http://markweinguitarlessons.com/index.php?option=com_content&task=view&id=145&Itemid=40](http://markweinguitarlessons.com/index.php?option=com_content&task=view&id=145&Itemid=40)

---

### Post by tuberculo on 2009-11-28
I think the problem is the nsplugin. I solved uninstalling nspluginwrapper in synaptic and installing 64-bit flash from this deb: [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/pool/main/f/flashplugin64-nonfree/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/pool/main/f/flashplugin64-nonfree/)

More info: [http://ubuntuforums.org/showthread.php?t=1307331](http://ubuntuforums.org/showthread.php?t=1307331)

---

### Post by wojox on 2009-11-28
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by extendedping on 2009-11-28
> **tuberculo said:**
> I think the problem is the nsplugin. I solved uninstalling nspluginwrapper in synaptic and installing 64-bit flash from this deb: [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/pool/main/f/flashplugin64-nonfree/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/pool/main/f/flashplugin64-nonfree/)

More info: [http://ubuntuforums.org/showthread.php?t=1307331](http://ubuntuforums.org/showthread.php?t=1307331)

I read the thread and instead of uninstalling/reinstalling stuff I tried system-preferences-appearance-visual effects-none and it at least appears to have worked (I have only tested on the one video I posted above). thanks.

---

### Post by tuberculo on 2009-11-28
OK, but I think 64-bit version works much better. There are some others problems with nspluginwrapper. At least for me.

---

### Post by SocratesTNR on 2009-12-10
Huzzah! Thanks :o)

AMD 64 Opetron Dual Proc.
Ubuntu Karmic
Chrome Dev. Rel.
FF 3.5


(ps it really hurts when something works on Windoze but not Ubuntu)




> **tuberculo said:**
> I think the problem is the nsplugin. I solved uninstalling nspluginwrapper in synaptic and installing 64-bit flash from this deb: [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/pool/main/f/flashplugin64-nonfree/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/pool/main/f/flashplugin64-nonfree/)

More info: [http://ubuntuforums.org/showthread.php?t=1307331](http://ubuntuforums.org/showthread.php?t=1307331)

---

### Post by The Beej on 2009-12-14
I'm having the same problem as above except no matter what flash site I visit, it doesn't load.  ](*,)
Can someone please give a step-by-step, command-by-command on the process previously mentioned/that seemed to work?  

Thanks!

---

### Post by eduardo451 on 2009-12-20
I use SUSE, but for me it worked inserting the following line:

```
export GDK_NATIVE_WINDOWS=1
```

before the final line in the npviewer file, which for me was in /usr/lib/nspluginwrapper/i386/linux, so the contents of the file when done are as follows:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

After making this change, I was able to view embedded YouTube files without having to right-click to view on YouTube, as mentioned earlier in this post.  I hope this helps in Ubuntu land!

---

### Post by vgrisham on 2010-01-24
> **eduardo451 said:**
> I use SUSE, but for me it worked inserting the following line:

```
export GDK_NATIVE_WINDOWS=1
```before the final line in the npviewer file, which for me was in /usr/lib/nspluginwrapper/i386/linux, so the contents of the file when done are as follows:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```After making this change, I was able to view embedded YouTube files without having to right-click to view on YouTube, as mentioned earlier in this post.  I hope this helps in Ubuntu land!

Thanks eduardo451. That did the trick.

---

### Post by ubeautu on 2010-02-21
> **extendedping said:**
> I read the thread and instead of uninstalling/reinstalling stuff I tried system-preferences-appearance-visual effects-none and it at least appears to have worked (I have only tested on the one video I posted above). thanks.

This fixed it for me too. Had the same problem with 9.10, having set at simple gui was a solution. Embedded videos now run without a hitch. I assume there is a bug in Firefox?

---

### Post by Chris_cur on 2010-02-23
> **wojox said:**
> [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Thanks this worked great for my laptop! Trying it out on my wife's.

---

### Post by Phobbes on 2010-03-19
Thanks! The GDK_NATIVE_WINDOWS solution worked for me!

---

### Post by neu5eeCh on 2010-05-11
Thanks from me too. I'd be interested to know, if anyone can explain, why this worked? Just trying to educate myself.

---

### Post by whoey on 2010-06-19
> **eduardo451 said:**
> I use SUSE, but for me it worked inserting the following line:

```
export GDK_NATIVE_WINDOWS=1
```before the final line in the npviewer file, which for me was in /usr/lib/nspluginwrapper/i386/linux, so the contents of the file when done are as follows:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```After making this change, I was able to view embedded YouTube files without having to right-click to view on YouTube, as mentioned earlier in this post.  I hope this helps in Ubuntu land!

This worked great for me in 10.04 x64 thanks!

---

### Post by nstenz on 2010-07-22
> **whoey said:**
> This worked great for me in 10.04 x64 thanks!

Same here.  Has anybody filed a bug report on this?

The only extension I'm using that could conceivably touch Flash is AdBlock Plus, but since this fixed it, I don't think it's to blame.

---

### Post by saengch on 2010-08-21
It seems the special visual effects are having some conflict with FF Youtube embed. This works for me: In System>Preferences>Appearance, click Visual Effect tab, option None.

---

### Post by angus73 on 2010-09-08
workaround from saengch also worked for me on ubuntu lucid x64
Thanks!
A.

---

### Post by Edsilva on 2011-12-21
I notice that youtube's old embed code is the one not working. If you use the iframe code it works, however the size of the video is the default size not the customized one.

I have two examples:

WITH OLD CODE: [http://www.mynextfreebmw.com/presentation/](http://www.mynextfreebmw.com/presentation/)

WITH NEW CODE: [http://www.mynextfreebmw.com/page6-2/](http://www.mynextfreebmw.com/page6-2/)

I'm using Ubuntu 11.10

Until now I still don't know how to have it working with the customized size, any suggestions are really appreciated.

Regards,
[www.EduardoSilva.biz]("http://www.EduardoSilva.biz")

---

### Post by Edsilva on 2011-12-21
I found the solution and now both the OLD and the NEW youtube codes are working normally, even the video's customized size works OK.

THE SOLUTION: I removed GNASH and restarted the computer.

GNASH is located at:

Ubuntu Software Center > Installed > Sound & Video

Good luck,
[www.EduardoSilva.biz]("http://www.EduardoSilva.biz")

---

