---
title: "Lost GUI after running grub"
date: 2011-02-05
forum: General Help
---

### Post by AlexSV on 2011-02-05
Login in problems:
I was trying to fix the brightness on my toshiba T130 Satellite laptop and found these instruction [Note: I did not try XRANDR option]

[INDENT]If backlight control doesn't work with the 'XRANDR' option above, use this:

Open terminal and run:
sudo gedit /etc/default/grub
Search for 'GRUB_CMDLINE_LINUX' (NOT 'GRUB_CMDLINE_LINUX_DEFAULT'!!)
GRUB_CMDLINE_LINUX=&#8220;nomodeset acpi_backlight=vendor&#8221;

Safe the file, run 'sudo update-grub' and reboot.

Credits: [https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948)[/INDENT][/INDENT]
[http://www.linlap.com/wiki/toshiba+satellite+t130](http://www.linlap.com/wiki/toshiba+satellite+t130)
However after running these instructions and rebooting my laptop I lost the GUI, and do not know how to get it back.
If it helps the loader screen with the 4 dots has gone slightly skewed, and I've downloaded the most recent update changes.

I can get GUI through recovery mode and running it in failsafex, but I don't think this is a good solution. Hope you can help.
Alex
**EDIT: Failsafe boot boots in older version of ubuntu (or at least older GUI)

---

### Post by wilee-nilee on 2011-02-05
If I understand you correctly you added the line to the grub boot. 

You need to give a more clear description, for example what gui? What you actually did rather then a link.

If your getting the grub boot menu at powering on, and you have changed the stanzas, hit **e** for edit and use the arrow keys to get to it and remove it then hit crtl-x to boot in.

---

### Post by Habitual on 2011-02-06
Next time:
Open terminal and run:
```
sudo cp /etc/default/grub /etc/default/grub.org
```

THEN edit to your heart's content.
**Moral of the story**, *[SIZE="4"]MAKE BACKUPS[/SIZE]*

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by AlexSV on 2011-02-07
@Habitual
I tried doing this and nothing happened
(Thanks)

---

### Post by AlexSV on 2011-02-07
@wilee-nilee

Sorry it's my first time posting here trying to take it a little slow in adjusting from windows to Ubuntu.
On the 5th of February I updated my system through the update manager, I believe this changed my my system from 
Ubuntu with linux 2.6.35-24-generic to 2.6.35-25-generic, with this update came new icons in the default top bar, and a new look.

After installing this update the volume control for my laptop disappeared, I decided I would now try to fix this and try to add brightness control, a feature I had lost with my T130 Satellite since switching over. 
I started with brightness and followed the instructions I posted above, I did not try the 'XRANDR' option first though.
After making those changes when I tried to log on next I was unable to reach the login screen, instead I get black and white text asking for my login name, and after password. My short username, and password works here and the system ends up pretty much locked in termal, without ever showing a graphical login screen. 
A work around I am using at the moment allows me to have a graphical interface and I boot it through the (recovery mode boot, with version 2.6.35-25) and choose the failsafex option, a low graphics mode. The resolution of the boot is wrong with my laptop through so it isn't a longterm workaround and would prefer to reinstall ubuntu over maintaining this.

Also, after following the instruction I posted previously the loading screen that has ubuntu with 4 or 5 dots... the dots are spaced out further after making the changes, I don't know if this helps but I find it odd.

Finally, on the recovery boot up, the graphics in the top bar have reverted to their previous iamges. For example the wireless connectivity icon, which I believe switched from a series of arcs to stepping bars is back to arcs. 
In the recovery boot mode I can pretty much follow and post any instructions/information you need. In the normal mode, with the terminal screen I'm not as confident with.
(Thanks!!!)

---

### Post by AlexSV on 2011-02-09
Bump, I'm going to let this set for another 48hours or so and then if I can't find a solution reinstall ubuntu.
If you can decipher the problem, or need any extra information let me know and I'll assist you assist me in any way possible.

---

### Post by vortmax on 2011-02-09
When it boots and drops you to a text terminal, that is a sign that Xorg could not start for some reason.  I'm guessing your video driver does not like the kernel flags you passed on the boot line.

To revert it back to normal:
---------------------------------------------------------------------
Either in the safe gfx mode or logging in through the text terminal:

sudo gedit /etc/default/grub
Search for 'GRUB_CMDLINE_LINUX' (NOT 'GRUB_CMDLINE_LINUX_DEFAULT'!!)
remove "nomodeset acpi_backlight=vendor" from the "GRUB_CMDLINE_LINUX=" line

Save the file, run 'sudo update-grub' and reboot.

On reboot, when you get to the grub screen, hit 'e' and verify that those flags are not present in the boot string, then follow the on screen instructions to proceed (<ctrl>-x I think).

To troubleshoot the issue more:
--------------------------------------------------------------------------
1. Boot the system and when you get to the grub menu, hit e
2. Find and remove "nosplash" from the list of kernel flags
3. Continue to boot and watch the screen for an error to pop up (post what it says)
4. Once you are dumped to the login prompt, log in and go to /var/log
5. Sift through syslog, kern.log and Xorg.0.log for errors.  Post what you discover.

---

### Post by matt_symes on 2011-02-09
Hi

Out of interest, why did you not try the xrandr options first ?

Kind regards

---

### Post by AlexSV on 2011-02-10
@Vortmax [<3], when I ran the code on the terminal I got
(gedit:1389):Gtk-WARNING **:cannot open display:

but when I ran it through the failsafex boot it worked (YAY)

Did more research and found out that the solution is out of date with more recent laptops or distros.

@Matt,the solution was beyond what I know how to do.
I found another solution here [[http://ubuntuforums.org/showthread.php?t=1321403&page=3]](http://ubuntuforums.org/showthread.php?t=1321403&page=3])
but have no ideas how to implement it for brightness control, if someone posted a beginners guide here or there, or msg'd me I would really appreciate it.

Thanks everyone who responded, just confirms why I switched to ubuntu :)

---

