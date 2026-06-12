---
title: "Urgent help!  Ubuntu does not boot!"
date: 2009-12-06
forum: General Help
---

### Post by zggame on 2009-12-06
Hi, my ubuntu does not boot.  I used to have gnome 9.10, then installed the kde-desktop, I try to switch to kdm login use the command "sudo dpkg-reconfigure gdm", then I reboot, it starts X somehow, but not the login.  I can reboot by alt-ctrl-del.  And the recovery mode does not work either.  I also tried "ctrl-alt-F1/2", and it does not show the login in screen

I tried "apt-get remove gdm" and it did not work.  

[Two days later with a walk-around from reto.ineichen [http://ubuntuforums.org/showthread.php?t=1343261&page=5]("http://ubuntuforums.org/showthread.php?t=1343261&page=5")]
After checking syslog, tt turns out it is the same problems some others have with gdm's failsafe-x and kdm races to die. (They should have raced to work.) 



I boot from a USB, go to the /etc/init and delete the  /etc/init/gdm.conf.  This one should have been removed once I switch to kdm IMHO.  And now everything goes back to normal.

---

### Post by guriinii on 2009-12-06
What are you running it on?

---

### Post by MooPi on 2009-12-06
do you get a command prompt ?

---

### Post by zggame on 2009-12-06
> **MooPi said:**
> do you get a command prompt ?

No.  I cannot get to it.  I am running it on a Compaq CQ60-420us laptop, pentium-dual core T4200, 4G RAM, 250G HDD, with a triple-boot Windows 7/Windows Vista/Ubuntu 64.  I started with 9.0.4 Ubuntu, upgrade to 9.10 and installed kubuntu/xubuntu afterward.

---

### Post by MooPi on 2009-12-06
So you have a blank screen?
Give us something to go with.
Do you see grub at boot?

---

### Post by guriinii on 2009-12-06
This may seem like an idiotic question, but have you got boot priority set up correctly?

---

### Post by zggame on 2009-12-06
The grub runs fine.  I can see the grup option and choose from different kernels or windows.  Windows runs fine.  When choose the linux kernel normal mode, it gets a kubuntu start picture, but then blank screen in the moment where previously the login screen is loaded.  In the recovery mode, it runs in the big text screen, then starts to load the small font text screen and freeze. 
Those are for the latest linux-2.6.31.16 generic.



Interesting, I choose in grub  the old kernel linux-2.6.28-16-generic and things load normally. Hope this helps.

---

### Post by MooPi on 2009-12-06
It may be time to use your install media/Live CD to boot and correct either kdm or gdm config. This is past my level of knowledge and am only suggesting what I would attempt next. I would try to disable kdm as it is hanging and try to get gdm functioning again.If your successful my next step would be to remove gdm and reinstall kdm if that's what you want to use. Hopefully someone else will chime in that know what to do.

---

### Post by zggame on 2009-12-06
I got back in 2.6.28-16-generic.  I switch from gdm back to kdm and everything go back to the normal.  Then I try to remove gdm and kdm is already there.  But now nothing works, even 2.6.28-16 fails.  

I do have a bootable kubuntu 9.10 USB driver, how to I fix it?

---

### Post by MooPi on 2009-12-06
Wow, If you don't have much data to loose in your Ubuntu partition I'd reinstall with your Kubuntu usb drive. Otherwise I'm at a loss for a solution. Reason being I'm not certain what you have done from your posted info. Was really hoping someone else would jump in and help. Have you un-installed gdm or just removed it from the config. I've read similar posts that suggest multiple display managers will screw your system.

---

### Post by zggame on 2009-12-06
> **MooPi said:**
> Wow, If you don't have much data to loose in your Ubuntu partition I'd reinstall with your Kubuntu usb drive. Otherwise I'm at a loss for a solution. Reason being I'm not certain what you have done from your posted info. Was really hoping someone else would jump in and help. Have you un-installed gdm or just removed it from the config. I've read similar posts that suggest multiple display managers will screw your system.

I apt-get remove gdm and sudo dpkg-reconfigure kdm.   It mysteriously come back fine even with kdm for now after a few boots from usb (but had done nothing beyond booting).  I have no idea what I have done. ( I really did not do anything but boot and reboot.)  I really do not want to reinstall, that feels so-WINDOWS.  :(

Thanks for all you help.

---

