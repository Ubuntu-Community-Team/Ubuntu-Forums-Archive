---
title: "No LTS release for new machines?"
date: 2011-07-23
forum: General Help
---

### Post by spoon_ on 2011-07-23
Tried 10.04.3 live CD on my sandy bridge system. Motherboard network adapter not recognized. So I guess there's no LTS release for new machines. Or am I missing something?

---

### Post by TeoBigusGeekus on 2011-07-23
Go with l/xubuntu natty or choose a rolling release.
Lucid's kernel is quite old...

---

### Post by spoon_ on 2011-07-23
Yeah it's just I have other problems with 11.04. Oh well.

---

### Post by TeoBigusGeekus on 2011-07-23
Have you tried with maverick?

---

### Post by CaptainMark on 2011-07-23
there is a lot of new wireless drivers in the more recent kernel, if you wanted you could [add the kernel ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa"), as it says its up to date but theres a possibilty of instability, if your going to use it i would update the kernel make sure its stable for you and if it works for your wireless and then switch off the ppa to stop un-needed updates to it adding risk, 

EDIT: i used [this kernel ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/pre-proposed") when i was having trouble and it worked great

---

### Post by spoon_ on 2011-07-23
It's a bit of a sad and stupid story.

The stupid part:

Maverick was working fine for me, but I decided to install natty. In natty my audio always dies shortly after boot and I can't get it back without rebooting. There are a few threads around the forums with people reporting the same issue, and even a bug report on launchpad, but no solutions.

The sad part:

I tried to go back to maverick, but maverick no longer recognizes my RAID-0 array that I use for storage. Only natty can mount it. Must be an md version incompatibility, or something. So I'm stuck here. I had some hope that lucid might be able to mount the array, since there are backported kernels all the way up to 2.6.38 (which also might mean my network adapter might work there...?).

---

### Post by TeoBigusGeekus on 2011-07-23
Me thinks it's time for some distro hoppin'...

---

### Post by spoon_ on 2011-07-23
> **TeoBigusGeekus said:**
> Me thinks it's time for some distro hoppin'...

Probably right. Recommendations?

---

### Post by spoon_ on 2011-07-23
> **CaptainMark said:**
> there is a lot of new wireless drivers in the more recent kernel, if you wanted you could [add the kernel ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa"), as it says its up to date but theres a possibilty of instability, if your going to use it i would update the kernel make sure its stable for you and if it works for your wireless and then switch off the ppa to stop un-needed updates to it adding risk, 

EDIT: i used [this kernel ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/pre-proposed") when i was having trouble and it worked great

Is it really necessary to add a ppa? There are official backports of the 2.6.38 kernel for lucid. (Leaving aside the issue of how to download stuff from PPAs when you have no working network card...)

---

### Post by TeoBigusGeekus on 2011-07-23
> **spoon_ said:**
> Probably right. Recommendations?

I use Arch; rolling release, not a glitch in the 12+ months I have it installed.
There is of course Fedora, Mint, Suse, Debian and some hundreds more :P
Visit distrowatch to get some ideas.

---

### Post by spoon_ on 2011-07-23
> **TeoBigusGeekus said:**
> I use Arch; rolling release, not a glitch in the 12+ months I have it installed.
There is of course Fedora, Mint, Suse, Debian and some hundreds more :P
Visit distrowatch to get some ideas.

Thanks. Actually I'm currently on Mint 11.04. Not surprisingly it has the same audio issue as Ubuntu 11.04.

---

### Post by recluce on 2011-07-26
(misquoted, please delete)

---

### Post by recluce on 2011-07-26
> **CaptainMark said:**
> there is a lot of new wireless drivers in the more recent kernel, if you wanted you could [add the kernel ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa"), as it says its up to date but theres a possibilty of instability, if your going to use it i would update the kernel make sure its stable for you and if it works for your wireless and then switch off the ppa to stop un-needed updates to it adding risk, 


This PPA was great. But unfortunately, it is now defunct. Look at your own link above, it no longer contains any packages. 

The demise of the kernel ppa is one more nail in Ubuntu's coffin for me.

> 
EDIT: i used [this kernel ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/pre-proposed") when i was having trouble and it worked great

This does not seem to contain anything recent for Lucid (2.6.32-something), which was the question here.

Does anybody know of an alternative? The current situation is really not acceptable - if you used the kernel ppa, you are now orphaned with a 2.6.38-8 kernel, with no further security updates. Going back to the official kernel (2.6.32 branch) is impossible for some of us (my machine would not work correctly). Daily builds are not an option for any kind of productive environment.

So any alternatives?

---

### Post by Gyokuro on 2011-07-26
If you want to switch and prefer something stable then I recommend to go with CentOS 6. RedHat handle LTS different as Ubuntu. They patch in new hardware support and Intel products are very good supported ;-). Otherwise you can use a backport kernel or roll your one. You can try CentOS live CD but for CentOS 6.1 you have to wait - the last release took some time :-)

---

### Post by pqwoerituytrueiwoq on 2011-07-26
> **recluce said:**
> This does not seem to contain anything recent for Lucid (2.6.32-something), which was the question here.

Does anybody know of an alternative? The current situation is really not acceptable - if you used the kernel ppa, you are now orphaned with a 2.6.38-8 kernel, with no further security updates. Going back to the official kernel (2.6.32 branch) is impossible for some of us (my machine would not work correctly). Daily builds are not an option for any kind of productive environment.

So any alternatives?
linux-image-generic-lts-backport-maverick
linux-headers-generic-lts-backport-maverick
i am using those from the kernel ppa in lucid now those are good through October 2011 this year
i needed it for trim support

---

### Post by recluce on 2011-07-27
> **pqwoerituytrueiwoq said:**
> linux-image-generic-lts-backport-maverick
linux-headers-generic-lts-backport-maverick
i am using those from the kernel ppa in lucid now those are good through October 2011 this year
i needed it for trim support

I found the maverick backports in the regular repositories, thanks for the tip. I had to install 2.6.38-10 manually, for some reason, but at least my main machine is up to a recent kernel again.

I need a 2.6.38 kernel both for trim support and various I/O function of my Core i7 notebook.

---

### Post by recluce on 2011-07-27
> **Gyokuro said:**
> If you want to switch and prefer something stable then I recommend to go with CentOS 6. RedHat handle LTS different as Ubuntu. They patch in new hardware support and Intel products are very good supported ;-). Otherwise you can use a backport kernel or roll your one. You can try CentOS live CD but for CentOS 6.1 you have to wait - the last release took some time :-)

I am considering all routes at this point. For now, Lucid is still viable and may remain so until 2013 - if the kernel support for natty backports should continue (you really never know).

Possible routes I see at this point:

1.) 12.04 LTS - unlikely, if no GNOME2-like desktop exists

2.) Mint (I guess that would be Mint 13), if they keep to the promise of keeping the GNOME 2 "look and feel" alive

3.) Mint Debian Edition (also depending on what the oracles look like next year)

CentOS is an option I will look at, at this point I don't know enough about that distro to even chance a guess whether it might be right for me or not. Thank you for the idea!

---

### Post by Gyokuro on 2011-07-28
> **recluce said:**
> I am considering all routes at this point. For now, Lucid is still viable and may remain so until 2013 - if the kernel support for natty backports should continue (you really never know).

Possible routes I see at this point:

1.) 12.04 LTS - unlikely, if no GNOME2-like desktop exists

2.) Mint (I guess that would be Mint 13), if they keep to the promise of keeping the GNOME 2 "look and feel" alive

3.) Mint Debian Edition (also depending on what the oracles look like next year)

CentOS is an option I will look at, at this point I don't know enough about that distro to even chance a guess whether it might be right for me or not. Thank you for the idea!

1.) Unlikely as Gnome2 is somehow dead and all developers are jump on Gnome3 and Unity get pushed but it's very new. I'm no fan of Gnome3 neither Unity.

2.) Mint was always a more polished release of ubuntu

3.) That's interesting as nobody knows whether debian devs think Gnome3 is stable enough for their next release ;-) 

4.) Intel Sandy Bridge systems are supported in RHEL 6.1 so someone have to wait for CentOS 6.1.

---

