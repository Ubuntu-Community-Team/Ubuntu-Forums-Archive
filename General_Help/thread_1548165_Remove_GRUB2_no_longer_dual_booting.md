---
title: "Remove GRUB2 no longer dual booting"
date: 2010-08-07
forum: General Help
---

### Post by Thomas Garman on 2010-08-07
I was dual booting on my netbook with Lucid and Windows XP, so the computer starts with the GRUB2 menu.  I deleted the windows partition and now I only use Lucid on the netbook.  I want to know how can I get the computer to simply boot into Ubuntu like a normal computer would do if it was not set up as a dual boot system?

How can I get the computer to go directly into the ONLY operating system rather than taking a detour through the GRUB menu?

---

### Post by chopinhauer on 2010-08-07
> **Thomas Garman said:**
> 
How can I get the computer to go directly into the ONLY operating system rather than taking a detour through the GRUB menu?


Grub only shows the menu if it finds multiple operating systems in its configurations. An ```
sudo update-grub
``` should delete the Windows entry and cut the Grub menu short.

---

### Post by Thomas Garman on 2010-08-08
I am not trying to "cut the menu short"...  I am trying to bypass the menu entirely so that the computer boots into Ubuntu directly rather than taking a detour through grub.  How?  I am not dual booting anymore so there is no reason for the computer to go into grub and offer any options AT ALL.

Yes, I already know "sudo update-grub"

---

### Post by QIII on 2010-08-08
You can set the time out to 0.  

I would recommend strongly against this for the reasons that follow.  Still, if you had quick fingers and clicked an appropriate key (I don't remember what that is currently, since I haven't worried about it for some time) you can raise the GRUB menu when you wanted to.

I understand that you want to boot to Ubuntu. But there** *certainly* *are*** good reasons to go through the GRUB menu:

1.  You might want to use memtest.

2.  You might update to a new kernel, find it doesn't work and then wish you had the GRUB menu to choose the previous working kernel to start up and sort out what went wrong.

3. You might want to enter recovery mode.

So, with the strong recommendation against doing this in mind...

Please read through the following guide.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Theft42 on 2010-08-08
> **QIII said:**
> You can set the time out to 0.  

I would recommend strongly against this for the reasons that follow.  Still, if you had quick fingers and clicked an appropriate key (I don't remember what that is currently, since I haven't worried about it for some time) you can raise the GRUB menu when you wanted to.

I understand that you want to boot to Ubuntu. But there** *certainly* *are*** good reasons to go through the GRUB menu:

1.  You might want to use memtest.

2.  You might update to a new kernel, find it doesn't work and then wish you had the GRUB menu to choose the previous working kernel to start up and sort out what went wrong.

3. You might want to enter recovery mode.

So, with the strong recommendation against doing this in mind...

Please read through the following guide.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I strongly agree with QIII. You never know if something bad will happen with the kernel. So I would keep it just for a safety.

---

### Post by chopinhauer on 2010-08-08
> **Thomas Garman said:**
> I am not trying to "cut the menu short"...  I am trying to bypass the menu entirely so that the computer boots into Ubuntu directly rather than taking a detour through grub.  How?  I am not dual booting anymore so there is no reason for the computer to go into grub and offer any options AT ALL.


If 'os-prober' doesn't find any other operating system, the 'grub' timeout is greatly shortened (to 3 seconds, instead of 10), so actually running 'update-grub' will shorten the boot time.

You can find a lot of information and how to customize your Grub on the [Ubuntu Wiki](https://wiki.ubuntu.com/Grub2).

BTW it is not possible to bypass Grub, just like it is not possible to bypass ntldr.exe on a Windows machine. Unless you use some alternatives to the BIOS (like coreboot), Grub is a compulsory stop.

---

### Post by ubu_lin on 2010-08-08
this thread is very informative, thanks to all.

---

### Post by Thomas Garman on 2010-08-08
So, as I understand it from the various posts, there is NO WAY AT ALL to make Ubuntu boot directly into the OS without taking a detour through GRUB?

I think that the idea that Ubuntu 10.04 was ever going to achieve a 30 second boot time is therefore absurd because...

I most certainly DID run sudo update-grub after I deleted my Windows partition and yes I have removed all of the previous kernels from old upgrades and...

When I boot up it sits there offering ubuntu or memtest for what seems like an eternity.

What a waste of time.

---

### Post by jroa on 2010-08-08
Grub is not the only boot-loader program.  I am sure that at least one of the hundreds out there will have an option to boot directly into a particular OS.

---

### Post by 3Miro on 2010-08-08
> **Thomas Garman said:**
> So, as I understand it from the various posts, there is NO WAY AT ALL to make Ubuntu boot directly into the OS without taking a detour through GRUB?


Grub is not a detour, Ubuntu needs Grub to boot. Grub is not just something to let you dual-boot and/or enter memtest/recovery, Grub is integral part of the Ubuntu system, without Grub Ubuntu will not run.

Like everything else in Linux, there is probably an alternative to Grub, however, it will only be another boot-loader that may work better for you, but it will not bypass that stage.

---

### Post by chopinhauer on 2010-08-08
> **Thomas Garman said:**
> So, as I understand it from the various posts, there is NO WAY AT ALL to make Ubuntu boot directly into the OS without taking a detour through GRUB?


Technically Grub is always there: the BIOS (first software that runs on your computer) is unable to boot the Linux kernel. The Grub menu, however, doesn't have to appear. What do you have in your /boot/grub/grub.cfg. Mine (single OS) contains:
```

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

```
meaning that unless I press SHIFT while booting the Grub menu doesn't appear at all and the system is booted after 3 seconds. This a very good compromise, IMHO, between the time you wait during the boot and the possibility to boot into recovery mode or memtest.

---

### Post by Thomas Garman on 2010-08-08
I am sorry to belabor the point but I fear that I have not been clear enough because many of the replies are literally ridiculous.  Here is my situation:

I have one operating system on my computer:  Lucid 10.04.  When I start my computer instead of loading the OS into the login screen the computer hangs for at least 10 seconds and then goes into  GRUB2 where it offers me three boot options:
Ubuntu
Ubuntu recovery
Memtest

Now, I have removed all Operating Systems and Linux Kernels other than the Kernel I got on my last update of Ubuntu.

There is no reason AT ALL for the machine to boot into an option to memtest or anything.  I feel like this detour through GRUB is a residue of my having dual booted the machine in the past.

From the posts and replies I am getting the sense that there is NO WAY to avoid the detour through GRUB?  When you boot into windows it does not take a detour through various options for how you want to boot... it just gives you the login screen.  Is this not possible with Ubuntu?

---

### Post by 3Miro on 2010-08-08
@Thomas Garman: windows is not as different as you would think. In XP, you have a period of 1 - 3 seconds when you could hit F8 (or was it F5) and enter into a menu that lets you choose different recovery options for boot. This is essentially windows' version of Grub.

On one of the older versions of Ubuntu, if you did not have any other OS installed, it did not showed a menu, instead it gave you three seconds to press a button (I think it was shift) and enter into the menu. If nothing happens during those 3 seconds, it boots the default option. If you follow some of the posts, you can do something similar by making the time down to 1 second, in which case you will get only a flash of the Grub menu screen.

If you have a 10 second delay between the post screen and Grub menu, then this might be a different problem. It may be the case that Grub is still looking for windows, if you removed/reformatted the windows partition without updating Grub, then it may be taking extra time to look for something that isn't there. Perform a Grub update to see if it will help (it should, especially if the problem did not exist before). If it takes 10 seconds anyway, then it is probably a hardware issue.

---

### Post by chopinhauer on 2010-08-08
> **3Miro said:**
> 
On one of the older versions of Ubuntu, if you did not have any other OS installed, it did not showed a menu, instead it gave you three seconds to press a button (I think it was shift) and enter into the menu. If nothing happens during those 3 seconds, it boots the default option. If you follow some of the posts, you can do something similar by making the time down to 1 second, in which case you will get only a flash of the Grub menu screen.


Lucid also blanks the screen for 3 seconds and then boots.

**Thomas**: if you keep waiting for 10 seconds, post your /boot/grub/grub.cfg to see why it doesn't blank the screen and shortens the delay.

---

### Post by QIII on 2010-08-08
> **3Miro said:**
> Grub is not just something to let you dual-boot  and/or enter memtest/recovery, Grub is integral part of the Ubuntu  system, without Grub Ubuntu will not run.

I didn't say it was "just".  I said those are three good reasons not to set the timeout to 0.  I didn't even mention getting rid of GRUB.  I did mention the GRUB menu.

You can, in fact, make Ubuntu boot without ever seeing the GRUB menu, although it will still go through GRUB.  You just won't ever see the menu.

Although you can use a keystroke to raise the menu, the general case is that when the timeout is set to 0, the first entry on the menu is used, regardless of whatever other OSes or previous kernels are available.

If you choose to change that timeout later, you can modify the config files.

However, this might be of little use if your current OS has been rendered unbootable and you can't modify the files.

You would be left with using the LiveCD to make the changes.

---

### Post by deserthowler on 2010-08-08
> **Thomas Garman said:**
> I am sorry to belabor the point but I fear that I have not been clear enough because many of the replies are literally ridiculous.  Here is my situation:

I have one operating system on my computer:  Lucid 10.04.  When I start my computer instead of loading the OS into the login screen the computer hangs for at least 10 seconds and then goes into  GRUB2 where it offers me three boot options:
Ubuntu
Ubuntu recovery
Memtest

Now, I have removed all Operating Systems and Linux Kernels other than the Kernel I got on my last update of Ubuntu.

There is no reason AT ALL for the machine to boot into an option to memtest or anything.  I feel like this detour through GRUB is a residue of my having dual booted the machine in the past.

From the posts and replies I am getting the sense that there is NO WAY to avoid the detour through GRUB?  When you boot into windows it does not take a detour through various options for how you want to boot... it just gives you the login screen.  Is this not possible with Ubuntu?

NO, IT IS NOT POSSIBLE TO BYPASS GRUB!!!!!!
Yes, it is possible not to see GRUB.  

Open /etc/default/grub as root.

You will see a line something like:

GRUB_TIMEOUT=-1

Change -1 to 3

Change:
#GRUB_HIDDEN_TIMEOUT=0
to:
GRUB_HIDDEN_TIMEOUT=0
and save.
Run:
sudo update-grub
Reboot and check grub.  It should be gone.

GRUB will run whether you multi-boot or not.  The answers you are getting are only ridiculous because of your limited understanding of how computers boot.

Earl

---

### Post by Thomas Garman on 2010-08-09
I just set the time out to zero.  I have no problem with using the live cd to boot if there is a problem with my OS some day.

---

