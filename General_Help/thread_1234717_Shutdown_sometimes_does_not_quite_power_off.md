---
title: "Shutdown *sometimes* does not quite power off"
date: 2009-08-08
forum: General Help
---

### Post by lethalfang on 2009-08-08
This happens about 10-20% of the time, enough to annoy me, that when I initiate shutdown, my laptop doesn't power off.
It'll get stuck at a point after the "progress bar" has completed, and the screen has a blinking cursor on the top left corner of an otherwise blank screen, but "shutdown progress" stops there. If I unplug the USB mouse, the screen will respond with a message saying that the USB mouse has been unplugged, but it never powers off the computer. I'd have to press down the power button to force power-off. 
Again, most of the time shutdown works fine. This happens about 10-20% of the times.

---

### Post by SuperSonic4 on 2009-08-08
What happens if you run ```
sudo shutdown -hP now
``` from a terminal?

---

### Post by lethalfang on 2009-08-08
> **SuperSonic4 said:**
> What happens if you run ```
sudo shutdown -hP now
``` from a terminal?

It has also happened when I do "sudo halt." I'm not exactly sure if it's exactly the same thing as "sudo shutdown -hP."
I would think it is, that -h stands for "halt," and -P stands for "power off."
Is it?

---

### Post by SuperSonic4 on 2009-08-08
Yeah that's correct.

---

### Post by CatKiller on 2009-08-08
It's a BIOS problem. The automatically-powering-off behaviour is done through [ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface"). When the kernel has finished shutting down, it sends the signal to tell the BIOS to turn the machine off. In your case, the BIOS is occasionally ignoring this signal.

---

### Post by mac-duff on 2009-11-21
Hi,

I having a similar problem with the new Ubuntu 9.10 version, all previous version worked without a problem.

Also sometimes the laptop doesnt come up, it just brings me to a console where I can enter reboot

---

### Post by chandra on 2009-11-21
+1 from me.

This problem did not exist with Jaunty but has surfaced sporadically with Karmic. The mobo and BIOS are unchanged.

---

### Post by willbir on 2009-11-21
Same for me, about 30% of the time the system does not power off since upgrading to 9.10. I disabled splash and took a picture of the last messages displayed, doesn't give too many clues.

---

### Post by willbir on 2009-11-21
It is definitely running the halt script at /etc/rc0.d/S90halt
And executing the command 'halt -d -f -i -p -h' but this just sometimes doesn't seem to work.

---

### Post by dow mathis on 2009-11-22
I'm having the same problem.  Running a Compaq CQ60.  Have been running 9.04 without issues since buying the laptop in June.  Upgraded to 9.10 yesterday, and everything else is working fine, except for the shutdown.

My guess is that something changed in the shutdown script, and that's keeping it from communicating correctly with the bios,

If anybody figures out a solution, please post it.

Thanks.

---

### Post by jithinkr on 2009-11-28
I am having a similar problem in my HP Compaq Laptop CQ50 series. The laptop doesn't power off completely, sometimes. The screen goes blank, but the power is still on and requires me to manually turn it off, but pressing the power button for some time.
No clue of why, wasn't happening with a fresh install.

One observation. Have this trouble, whenever I access files in my NTFS partition. I can access files in NTFS partition (Windows) from Linux. When I do this, I find my laptop not shutting down completely.

---

### Post by cmat on 2009-12-09
Anybody have a possible solution to this issue? I filed a bug report but it make take some time to get resolved (if at all).

---

### Post by chandra on 2009-12-09
I do not know if this is the cause, but the "Leave" button in the menu has a "Suspend to disk" dropdown. Does the incomplete shutdown happen when this dropdown item is accidentally activated, but not otherwise?

In that case, it is simply a question of making sure that the dropdown menu item is not activated.

Can those on this thread take a look to see if this is the cause please?

Thanks.

---

### Post by kcirrab on 2009-12-09
I also have a Compaq CQ60 and i have no problem what so ever. not one time has it not shutdown. thats odd that urs does not shut down. What is ur bios Version?

---

### Post by cmat on 2009-12-11
> **chandra said:**
> I do not know if this is the cause, but the "Leave" button in the menu has a "Suspend to disk" dropdown. Does the incomplete shutdown happen when this dropdown item is accidentally activated, but not otherwise?

In that case, it is simply a question of making sure that the dropdown menu item is not activated.

Can those on this thread take a look to see if this is the cause please?

Thanks.

I've been shutting down via the system menu.

---

