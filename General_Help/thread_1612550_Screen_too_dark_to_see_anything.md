---
title: "Screen too dark to see anything"
date: 2010-11-03
forum: General Help
---

### Post by photographer92 on 2010-11-03
Hello,
 
Yesterday I installed Ubuntu on my Laptop (Acer Aspire 5741). Windows 7 was already on the computer. I am now dual booting Windows 7 and Ubuntu 10.04.
When i boot into windows, everything is fine. I can adjust brightness with Fn+arrow keys and i have total control. When i shut down the computer and boot from Ubuntu, the screen is extremely dark. It is hard to see anything on the screen. I have to get my eyes very close and have a light above the laptop just to see anything. I have read on forums online on how to adjust brightness from system>preferences>appearance, BUT the screen is too dark to get to that point!! I cant see the screen well enough to adjust brightness. Again, when i boot from windows, i can adjust screen brightness from keyboard and from Power Options under Hardware and Sound.
 
Please help! I really want to enjoy linux, but not being able to see the screen is making it very difficult!
 
Thank you!

---

### Post by P4man on 2010-11-03
Sounds like the backlight isnt working. Try this as a temporary workaround: press control+alt+F1. You will get a full screen terminal asking you to log in (you dont have to at this point), is screen brightness normal there? Then press control+alt+F7 or F8 to return to the gui. With some luck the backlight is on now.

---

### Post by photographer92 on 2010-11-03
Just tried that. It didnt do anything. I did not notice a difference in the brightness. 
When you turn it on, it asks for your user name and passwrod. I entered those using a dim flashlight (because a bright flashlight makes it impossible to read). I waited a couple of minutes for things to load ( i never knew if they did cuz i cant see) and then i did those keystrokes.  The computers fan didnt turn on, the little CPU light thing near the power button didnt blink (it normally blinks when its loading something). I got no signs of any type of response out of the OS. Help??

---

### Post by Quackers on 2010-11-03
I've seen people have varying uses for the
backlight=vendor
boot argument. It may be worth a try.

---

### Post by photographer92 on 2010-11-03
1) Im a windows guy. Never used linux before in my life. Can you please explain what you mean? Also, i want to make sure you know that the screen goes totally black after login. Drum sound plays, then the screen is black from there on out. I've tried using a flashlight. Im dual booting with windows7 as the primary OS. The screen works fine on the windows 7 OS. Laptop is less than 6 months old. 

  2) What do you know about the correlation between screen resolution and the backlight?

---

### Post by Quackers on 2010-11-03
If you aren't seeing the grub menu (a choice of operating systems) I don't know what to suggest, as the line you may need to amend will not be viewable.
Is there an update available for your bios? It could possibly be a bios setting. It may be better to wait for more specific directions from somebody who has had a similar problem.

---

### Post by photographer92 on 2010-11-03
Yeah im pretty sure my BIOS and everything is up to date. It seems like Ubuntu has a lot of problems with installation though. Thanks for your help is resolving this!! i think im just gonna download OpenSUSE. It seems to have less problems upon installation.

---

### Post by P4man on 2010-11-04
Its doubtful opensuse will solve the issue. Backlight is controlled by ACPI, which in turn is tied to the bios. If the bios is crappy it will not work with any OS other than the one that was shipped with the laptop, Even a future or older windows may not work properly, because the bios probes for the OS and doesnt initialize certain functions if the OS isnt the one and only one it was designed for. You can blame ubuntu for that if you want, but its not their fault. Its the ones writing the bios.

Now you might be able work around the issue by spoofing window osi, so telling the bios you are running a certain windows version, even when you are not, or by disabling acpi_osi all together. You will need to get in to grub though, and I think this is a wubi install? Did you install ubuntu from within windows, or from a bootable CD or USB stick?

---

### Post by P4man on 2010-11-04
detailed instructions in my signature

---

### Post by niko123456 on 2010-11-24
Did you have any luck? 

I have the same problem. 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10158364#post10158364](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10158364#post10158364)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/653985](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/653985)

Here is a basic workaround (you will be able to switch the screen on by shutting and opening the lid.. but after you have turned off automatic suspend/resume)

"
Switch to another console, (ie, ctrl alt 1), then open and shut the lid (suspend is inhibited). switch back to ctrl alt 7 and then switch off automatic suspend and resume."

---

### Post by niko123456 on 2010-11-24
and just to solve a few mysteries for the OP.

It wasn't a bios issue.

There was no disk activity because the machine had probably suspended or had booted into the OS. 

Newbies shouldn't have to deal with words like 'Grub'. Try more obvious terms like 'boot loader'.

---

### Post by Anks329 on 2010-11-24
I'm having this same problem with my Acer laptop. I've tried the acpi_osi= and the xforcevesa commands and neither work. Does anyone else have a suggestion?

---

### Post by Quackers on 2010-11-24
I was trundling through gconf-editor yesterday and found a backlight setting. I have no idea whether it will help or even if you'll be able to see it but here is the info anyway.
Press Alt + F2 and the run dialogue box appears. Enter gconf-editor and hit enter. In the resulting screen click on the arrow next to Apps, then click on the arrow next to Gnome Power Manager, then click on backlight.
On the right of the screen, 2nd entry down is "brightness_ac" then a percentage to its right. Mine is set at 100. If yours is considerably less right-click on it and select "Edit key" and in the resulting box enter your chosen percentage and click ok. Leave gconf-editor and log out then log in again and the new setting should be applicable. Hopefully :-)

---

### Post by P4man on 2010-11-27
> **Anks329 said:**
> I'm having this same problem with my Acer laptop. I've tried the acpi_osi= and the xforcevesa commands and neither work. Does anyone else have a suggestion?

You could try acpi_osi="Linux" (if you havent already).

Also, while not really a solution, when I encoutered this issue with an older release of ubuntu years ago, I found that hitting control+alt+F1 to open a full screen TTY and then control+altF7 (or F8) to return to the GUI would fix it.

---

