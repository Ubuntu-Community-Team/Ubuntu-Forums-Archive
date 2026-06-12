---
title: "Problem with PCMan File Manager and File Browser"
date: 2010-05-26
forum: General Help
---

### Post by javarunner on 2010-05-26
Sorry if this is not the appropriate forum for this question.  I am unable to open any folders after displaying them for some drive on my PC.  So I cannot access the contents.  The permissions are set to read/write/execute.
I can see both my hard drives with PCMan. However, I can open folders if I use the Ubuntu File Browser.  Unfortunately, the File Browser does not show the primary drive - the one that has Ubuntu (v10.4) installed.  Any ideas?

---

### Post by VastOne on 2010-05-26
> **javarunner said:**
> Sorry if this is not the appropriate forum for this question.  I am unable to open any folders after displaying them for some drive on my PC.  So I cannot access the contents.  The permissions are set to read/write/execute.
I can see both my hard drives with PCMan. However, I can open folders if I use the Ubuntu File Browser.  Unfortunately, the File Browser does not show the primary drive - the one that has Ubuntu (v10.4) installed.  Any ideas?

Having this same issue with PCMan File Manager.  It will not let me open any child directories at all. This is only with Lucid.

---

### Post by javarunner on 2010-05-26
I hope it gets fixed quickly!  I'm fairly inexperienced with Ubuntu so thought it might have been some setting - but I guess not.
Thanks.

---

### Post by rjb-356 on 2010-05-27
I'm having the same problem with Ubuntu 10.04, but found I can access deeper folders/files by "right clicking" and selecting "open in new tab".  This is a work-around, that is not very satisfactory, but does work.

RJB

---

### Post by VastOne on 2010-05-28
> **rjb-356 said:**
> I'm having the same problem with Ubuntu 10.04, but found I can access deeper folders/files by "right clicking" and selecting "open in new tab".  This is a work-around, that is not very satisfactory, but does work.

RJB

I have found with the latest series of updates, I no longer have the problem

---

### Post by rjb-356 on 2010-05-28
Thanks VastOne.  You are correct.  The latest version works without problems.  It took me a while to find a deb version of pcmanfm v0.9.5.  Prior to finding it I was playing with the source and "make" and I just got confused with all the errors.  The I was lucky and found:

[http://packages.debian.org/sid/i386/pcmanfm/download](http://packages.debian.org/sid/i386/pcmanfm/download)

I'm running Ubuntu 10.04.  My Ubuntu warned me that an earlier version was available through the "normal" distribution channels.  I ignored the warning and installed the "latest" version.  

I hope the above saves others some time and frustration.

RJB

---

### Post by PCMan on 2010-05-30
> **rjb-356 said:**
> Thanks VastOne.  You are correct.  The latest version works without problems.  It took me a while to find a deb version of pcmanfm v0.9.5.  Prior to finding it I was playing with the source and "make" and I just got confused with all the errors.  The I was lucky and found:

[http://packages.debian.org/sid/i386/pcmanfm/download](http://packages.debian.org/sid/i386/pcmanfm/download)

I'm running Ubuntu 10.04.  My Ubuntu warned me that an earlier version was available through the "normal" distribution channels.  I ignored the warning and installed the "latest" version.  

I hope the above saves others some time and frustration.

RJB
It's already packaged for Ubuntu in Lubuntu ppa.
[https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

The latest 0.9.7 just came out last night.
More detail and HOWTO: [http://blog.lxde.org/?p=727](http://blog.lxde.org/?p=727)

---

### Post by VastOne on 2010-05-30
> **rjb-356 said:**
> Thanks VastOne.  You are correct.  The latest version works without problems.  It took me a while to find a deb version of pcmanfm v0.9.5.  Prior to finding it I was playing with the source and "make" and I just got confused with all the errors.  The I was lucky and found:

[http://packages.debian.org/sid/i386/pcmanfm/download](http://packages.debian.org/sid/i386/pcmanfm/download)

I'm running Ubuntu 10.04.  My Ubuntu warned me that an earlier version was available through the "normal" distribution channels.  I ignored the warning and installed the "latest" version.  

I hope the above saves others some time and frustration.

RJB

RJB,

When I said I found the latest updates helped PCManFM, I was referring to the Ubuntu System updates that corrected my issues with the old version of PCManFM.

Bu thanks to your diligence, I am now running the latest PCManFM. :guitar:

Thanks!

---

### Post by VastOne on 2010-05-30
> **PCMan said:**
> It's already packaged for Ubuntu in Lubuntu ppa.
[https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

The latest 0.9.7 just came out last night.
More detail and HOWTO: [http://blog.lxde.org/?p=727](http://blog.lxde.org/?p=727)

Do you an idea of how long it will take 0.9.7 to hit the ppa?

---

### Post by RingoFyre on 2010-07-04
I found the getting 0.9.5 from the [ppa]("https://launchpad.net/~lubuntu-desktop/+archive/ppa/+packages") worked better rather than 0.9.7 from the [debian archives]("http://packages.debian.org/sid/amd64/pcmanfm/download") as the latter ver. crashed when I clicked on the side pane. on that subject - how can I get rid of the side pane as the functionality under the View menu has gone?
Good to have pcmanfm back - I was missing it.

---

### Post by RingoFyre on 2010-07-04
I found that getting 0.9.5 from the [ppa]("https://launchpad.net/~lubuntu-desktop/+archive/ppa/+packages") worked better rather than 0.9.7 from the [debian archives]("http://packages.debian.org/sid/amd64/pcmanfm/download") as the latter ver. crashed when I clicked on the side pane. On that subject - how can I get rid of the side pane as the functionality under the View menu has gone?
Good to have pcmanfm back - I was missing it.

---

### Post by Devi 710 on 2010-08-28
Thanks for letting me know about the PPA for the newest version 0.9.7. It's great!

I have two issues with PCManfm:

1.) When I insert a disk, nautilus will open up. Nautilus will also open up if I double click the icon for the disk/usb on the desktop. Is this because nautilus is still writing the desktop?

2.) When I click on the dropbox icon on my panel, it will also open nautilus.

It would be great if anyone can help me out. Though it isn't a major issue.

---

