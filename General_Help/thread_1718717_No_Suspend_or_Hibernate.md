---
title: "No Suspend or Hibernate"
date: 2011-03-31
forum: General Help
---

### Post by defensorfedei on 2011-03-31
So here is the latest problem I am dealing with.  Actually it is quite an old problem for me that started in [this]("http://ubuntuforums.org/showthread.php?t=1659089") post, when I was running Karmic.  Not one person posted anything.  I am hoping that I have better luck this time.

Machine is a Dell Optiplex GX260, Pentium 4 with ATI Radeon RV200 QW [Radeon 7500].  I believe this is an AGP graphics card.  I also believe that the graphics card is the root of my problem.  Feel free to correct me if you feel otherwise.

In Karmic, I could get the computer to suspend. but it would not resume. The monitor would not initiate and it seemed as though the system froze.  Only way out was a hard reboot.  Hibernate worked for me without any problems, so it was no deal breaker.

Now in Meerkat, Suspend behaves exactly as before.  However, I can not get the system to go into hibernation.  The monitor goes down, but the system seems to freeze and never go down.  This to me is a problem.

I have tried editing the options in the acpi-support file to no avail.  I have tried disabling compiz (which works amazingly well with this card), to no avail. I am using the open-source drivers and I have not tried the closed-source drivers in this system.  I tried the closed-source drivers in Karmic and they made no difference.  I may try un-installing the ATI card and fall back on the on-board Intel chipset to see if that solves the problem.  Only then, I will loose 3d effects, etc.... 

Does anyone use this graphics card?

Does anyone have this same issue?

Does anyone have any ideas on how to trouble shoot this?

Any help at all would be greatly appreciated.  Thanks

---

### Post by Krytarik on 2011-03-31
First, your video card isn't covered by the proprietary driver anymore. The best available option now, is to use the Open Source Edge Driver (OSED), provided by Xorg-Edgers' PPA. If you want to install it, run these commands:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

As for your primary issue, you may find it odd (me either), but you should try installing the package "hibernate". It isn't installed by default.

Greetings.

---

### Post by defensorfedei on 2011-04-01
Thanks Krytarik,

I installed the xorg-edgers ppa and installed the new drivers.  That did not seem to make any difference.  I also installed hibernate, which pulled uswsusp as a dependency.  If I remembered correctly, uswsusp is not linked to the gnome hibernate/suspend buttons in the gnome shutdown menu.  Therefore I ran 'sudo s2disk' in a terminal and got the same problem.  The monitor goes down but the computer seems to hang, forcing a hard reboot.

It seems to me that there is something about this card that A) Will not initiate when coming out of suspend, and B) Will not power down when going into hibernation.  This leaves me at a total loss.

I refuse to believe that nobody else using Ubuntu or any other distro does not have this same graphics card. I do believe that somebody out there is using this card, and has had success with it. 

Thanks again for help Krytarik.  Any other ideas?

---

### Post by age6racer on 2011-04-01
The script in this link has solved my suspend/hibernation issues in the past.

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

---

### Post by defensorfedei on 2011-04-01
Ok I will give this a try and post back with the results.  First...its Clonezilla time!


Edit: I tried this solution and it did not work.  I wonder what was different in Karmic, that would allow hibernate to work, that changed in Meerkat?

---

### Post by defensorfedei on 2011-04-01
Hey guys.  I made the decision to un-install the ati rv 200 Radeon 7500 GPU and rely on the built-in intel graphics.  Suspend and hibernate work flawlessly now, but I lost my cube. :(

I will leave this thread open for a while and see if anyone else comes upon it who has the same problem, or better yet, has the solution.  I am still baffled that I am the only person with this chipset yielding these results.  Oh well.  For now this box will be rockin it 2d.

Thanks for you help guys.

---

### Post by ranger12 on 2011-04-02
Yeah, I am running 11.04 beta 1 on a Dell Latitude D600 and it has an ATI Mobile Radeon 9000 and it has the same problem with Suspend and Hibernate. I think these ATI drivers just are not very good.

---

### Post by ranger12 on 2011-04-03
I did try the solution at thecodecentral. It wakes up the laptop but it does not turn the display back on but I think it was doing that exact thing before I tried putting that script in. I just think it is this ati driver. They need to do more work on this driver.

---

### Post by defensorfedei on 2011-04-03
I agree Ranger.  However, I use the open-source driver in my MSI laptop with ATI 3650HD chipset, and it works great.  I think they are dropping off support for the older cards which is a shame.  One of the great hallmarks of Ubuntu, and Linux in general, is that older hardware gains new life.  Really is too bad.

---

### Post by ranger12 on 2011-04-03
Well I am not going to make a big deal over it since I will seldom have a need to put this laptop into suspend or hibernation but still since it is a "basic" function of all laptops; as far as I can tell anyways, they should test this on older cards and make sure it works - but whatever. Like I said, I am not going to make a big fuss over it  - it's not worth it.

---

### Post by techunit on 2011-04-03
I am running a more recent card and downloading the package files from AMD solved my problem. I hope you figure it out. 

If its not your graphics card it could be you just lack swap space.

---

### Post by defensorfedei on 2011-04-03
As far as I could find out, the card I am using (radeon 7500) is not supported in the proprietary drivers package anymore.  It may be a different story for Ranger.  Like I said before, I un-installed my card and went back to the integrated intel chip, and all is working perfectly.  Swap space is not the issue here.....for me anyway.

---

### Post by Krytarik on 2011-04-03
> **defensorfedei said:**
> As far as I could find out, the card I am using (radeon 7500) is not supported in the proprietary drivers package anymore.  It may be a different story for Ranger.
It's the same for *ranger12*.

---

### Post by ranger12 on 2011-04-04
Like I said it is not a big deal but just to clarify, I am not using the proprietary drivers but the ati open source driver. I'll check the swap partition - it could be the source of the problem but I am not going to make a big fuss over though but I will check out the swap file just for kicks and giggles.

---

### Post by ranger12 on 2011-04-04
After checking Disk Utility this is what it reports:

80 Gb hard drive
79 Gb partition /dev/sda1
1.1 Gb partition /devsda2 Extended partition
1.1 Gb partition /dev/sdaS Swap space

This is what was installed by the install program, not by me. The laptop has 1 Gb of memory.

---

### Post by ranger12 on 2011-04-06
I think what I will do is when 11.04 goes final, download it onto my flash drive and when I install it on this laptop, I will set up the partitions manually and configure a 2 Gb swap partition and then see what that does.

---

### Post by ranger12 on 2011-05-15
Well when I tried to setup 11.04 final fresh on this laptop - I could not setup the partitions manually. It kept telling me I needed to specify a startup filesystem on the primary partition and I could not find a way to do this so I was forced to let the install utility do it automatic so I am back to a 1 mb swap partition and the same issue so I am going to let it go. I don't know what Canonical's issue with this suspend/hibernate issue is over the last few versions but I have noticed a lot of people have had issues with it.

---

