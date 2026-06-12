---
title: "HELP!!! I screw up the startup manager.. really new pls help."
date: 2011-06-07
forum: General Help
---

### Post by thydeus on 2011-06-07
I accidentally set the grub startup manager's time to 0 secs and windows xp as the default OS. (I have windows xp and ubuntu on this laptop.)

Now when I turn on or restart my computer, it boots up straight to windows, I can no longer access the grub boot selection screen or my ubuntu OS.

What should I do? :(

~sorry for my bad english.

---

### Post by matt_symes on 2011-06-07
Hi

Reboot your PC and when you see the POST test (the very first text on your monitor screen after a reboot) press and hold the shift key. 

This will show the Grub menu.

Kind regards

---

### Post by pastalavista on 2011-06-07
Did you try press and hold shift key while booting?

---

### Post by thydeus on 2011-06-07
> **matt_symes said:**
> Hi

Reboot your PC and when you see the POST test (the very first text on your monitor screen after a reboot) press and hold the shift key. 

This will show the Grub menu.

Kind regards

> **pastalavista said:**
> Did you try press and hold shift key while booting?


Hi, thanks for your input.

I rebooted and waited for the POST test screen and then I pressed and hold the shift key but nothing happens? :(

My Ubuntu version is 9.10 karmic kuala

---

### Post by quinntar on 2011-06-07
Hi, well i think the best think to do if only grub is screwed up is to go  on google searching for Super Grub Disk, it will allow you to repair grub. It's a boot cd. So you have to download the iso image then burn it on a cd with your favorite image burner. Finally boot on it and follow the instruction to repair/restore your grub. It should be fine afterwards with your karmic.

Let me know if it worked and mark the post as solved if it's the case :KS
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by matt_symes on 2011-06-07
Hi

If you don't want to use grub super disc and you have a LiveCD/USB handy, you can fix grub using that.

If you want to do that and need instructions then post back.

Kind regards

---

### Post by Bucky Ball on 2011-06-07
> **thydeus said:**
> Hi, thanks for your input.

I rebooted and waited for the POST test screen and then I pressed and hold the shift key but nothing happens? :(

My Ubuntu version is 9.10 karmic kuala

In that case it is the escape key, *not* shift.

I would suggest you install 10.04 LTS (smooth ride for a newcomer and long-term support) before you get too involved. 9.10 is no longer supported. You can install it straight over the top of 9.10.  ;)

---

### Post by thydeus on 2011-06-07
> **quinntar said:**
> Hi, well i think the best think to do if only grub is screwed up is to go  on google searching for Super Grub Disk, it will allow you to repair grub. It's a boot cd. So you have to download the iso image then burn it on a cd with your favorite image burner. Finally boot on it and follow the instruction to repair/restore your grub. It should be fine afterwards with your karmic.

Let me know if it worked and mark the post as solved if it's the case :KS
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


I'm gonna give this a try, will post back in a couple of mins. thanks!


> **matt_symes said:**
> Hi

If you don't want to use grub super disc and you have a LiveCD/USB handy, you can fix grub using that.

If you want to do that and need instructions then post back.

Kind regards


I have the Ubuntu LiveCD and a USB, please let me know how I can fix this.


> **Bucky Ball said:**
> In that case it is the escape key, *not* shift.

I would suggest you install 10.04 LTS (smooth ride for a newcomer and long-term support) before you get too involved. 9.10 is no longer supported. You can install it straight over the top of 9.10.  ;)

Still, nothing happens. :(

---

### Post by Bucky Ball on 2011-06-07
Try pressing repeatedly rather than holding it down.

---

### Post by nzjethro on 2011-06-07
With mine, I press F12 to access the boot menu. Try that instead of shift or esc?

---

### Post by matt_symes on 2011-06-07
Hi

> **nzjethro said:**
> With mine, I press F12 to access the boot menu. Try that instead of shift or esc?

That is the BIOS boot menu and not the Grub boot menu ?

Kind regards

---

### Post by thydeus on 2011-06-07
[http://www.supergrubdisk.org/category/download/supergrubdiskdownload/](http://www.supergrubdisk.org/category/download/supergrubdiskdownload/)

CRAP! All I have are blank DVD's, I don't have blank CD's and I don't have a floppy drive.  :/

I do have a USB but I don't know how to boot it?


> **Bucky Ball said:**
> Try pressing repeatedly rather than holding it down.

Thanks but it still didn't worked. 


> **nzjethro said:**
> With mine, I press F12 to access the boot menu. Try that instead of shift or esc?

Thanks but pressing F12 brings up the bios boot menu, not the GRUB menu.

---

### Post by nothingspecial on 2011-06-07
Use unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by thydeus on 2011-06-07
I went out and bought a blank CD, I burned Super Grub and booted it up but now I'm clueless on what to do, it has too many options. I'm confused. :/

---

### Post by mike555 on 2011-06-07
Just use Super Grub to boot Ubuntu ,then go and set startup manager to set Grub to something like 4 seconds

---

### Post by nzjethro on 2011-06-07
D'oh, my bad!

---

### Post by thydeus on 2011-06-07
Woot! I successfully booted up my linux partition with super grub and I have now adjusted the grub startup manager settings, all has been fixed now.

Thank you all for your help!! :D

---

### Post by Bucky Ball on 2011-06-07
Excellent news! Please mark as 'solved'. Enjoy. ;)

---

### Post by quinntar on 2011-06-08
OK well you can mark it as solved then and THANK SUPER GRUB DISK héhéhéhé  :-D

You can cheer up now

Quinnt

---

