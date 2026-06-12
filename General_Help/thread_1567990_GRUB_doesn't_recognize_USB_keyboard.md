---
title: "GRUB doesn't recognize USB keyboard"
date: 2010-09-04
forum: General Help
---

### Post by Lewian on 2010-09-04
I recently got a new USB-keyboard. Before that, I had a PCI one.
Ubuntu itself is apparently fine with it (beginning from the login screen), but it doesn't do anything in GRUB, i.e., I cannot go up and down to select what I want to boot and confirm using Enter. 
How can I teach GRUB about the keyboard?

Thanks.

---

### Post by oldfred on 2010-09-04
Check BIOS settings. I had the same issue with a new motherboard a year or two ago. I was quickly swapping ps/2 & usb ports to use the grub menu. But you should have a setting in BIOS that windows & Ubuntu ignore but says use ps/2 ports, change to enable USB keyboard & mouse.

---

### Post by coffeecat on 2010-09-04
> **oldfred said:**
> Check BIOS settings.

Agreed. This is a BIOS problem. In some BIOS's the setting is called 'legacy BIOS'. Why? Don't know. You need to enable it.

---

### Post by VoidQ on 2010-09-04
Hi all,

New user on this forum.

I have a similiar problem. I have a Logitech G15 usb keyboard (older one with the hinged LCD) and my computer has a Asus A8N-SLI Premium motherboard.

I'd been using the old Grub for quite a while without any problems, dual booting between earlier versions of Ubuntu 32bit and XP. A while after 10.04 came out I thought I'd go 64bit and so went for a fresh install, getting Grub 2 as part of the change. Since then I've been unable to use my keyboard when on the Grub screen. The keyboard works fine for launching the BIOS (using the delete key) and as soon Grub's countdown has passed the backlighting on the keyboard comes on and the keyboard seems to work fine from then on.

USB Controller, USB 2.0 Controller and USB Legacy options are all enabled in the BIOS.

Has anyone any ideas of things I should check, tests I could perform or possible solutions?

---

### Post by drs305 on 2010-09-04
> **VoidQ said:**
> Has anyone any ideas of things I should check, tests I 
could perform or possible solutions?

VoidQ, welcome to the Ubuntu forums. 

If changing the settings in BIOS doesn't work:

[COLOR="DarkRed"]**Caution: VoidQ tried these suggestions and they did not work! (Post #7)**[/COLOR]

I haven't tried it, but Grub2 has an option which can be added to /etc/default/grub. It may be just what you are looking for, but again I don't know for sure.

Open the following file for editing:
```
gksu gedit /etc/default/grub
```

Here is the line to add:
> 
GRUB_TERMINAL_INPUT="usb_keyboard"


Save the file, run the following command to update the menu, then reboot. 
```
sudo update-grub
```

If that doesn't work, leave the entry alone, but reboot and at the Grub menu, press "c" to get to the Grub prompt, then type:
```
insmod usb_keyboard
```
Note that this command may freeze up your keyboard (although it apparently isn't working anyway). In this case though, you have stopped the automatic boot and will have to poweroff your machine if the keyboard doesn't respond.

This second method is non-persistent - it won't stick the next time you boot and you'll be back to the way things were the last time.

If you try either or both of these suggestions, let us know the result. Especially the second, as we will have to make loading the usb_keyboard.mod permanent.

---

### Post by dcstar on 2010-09-04
> **coffeecat said:**
> Agreed. This is a BIOS problem. In some BIOS's the setting is called 'legacy BIOS'. Why? Don't know. You need to enable it.

Or it is a specific BIOS setting to use a USB keyboard.

In **every** situation like this that I have encountered it is a BIOS issue.

---

### Post by VoidQ on 2010-09-05
Hi, thanks for your reply.

> **drs305 said:**
> 

I haven't tried it, but Grub2 has an option which can be added to /etc/default/grub. It may be just what you are looking for, but again I don't know for sure.

Open the following file for editing:
```
gksu gedit /etc/default/grub
```Here is the line to add:


Save the file, run the following command to update the menu, then reboot. 
```
sudo update-grub
```
I made this change and then rebooted, but after this the Grub screen wouldn't come up. At the point at which it should come up the machine just rebooted and ended up in a continuous loop. I'm currently in a live cd environment, mount/chrooting onto my Ubuntu partition to delete the line and update again.

> **drs305 said:**
> 
If that doesn't work, leave the entry alone, but reboot and at the Grub menu, press "c" to get to the Grub prompt, then type:
```
insmod usb_keyboard
```Note that this command may freeze up your keyboard (although it apparently isn't working anyway). In this case though, you have stopped the automatic boot and will have to poweroff your machine if the keyboard doesn't respond.

This second method is non-persistent - it won't stick the next time you boot and you'll be back to the way things were the last time.

If you try either or both of these suggestions, let us know the result. Especially the second, as we will have to make loading the usb_keyboard.mod permanent.

As the keyboard will not respond at all during the Grub boot screen, pressing C at that point won't do anything, and unfortunately I don't have a spare keyboard to try with.

---

### Post by Lewian on 2010-09-05
Solved, thanks! I changed the BIOS settings. It's funny that even when USB keyboard support is disabled, I can use it in the BIOS settings to enable it, but here we go...

I don't mark the thread as "solved" because VoidQs problem is still there.

---

### Post by VoidQ on 2010-09-05
> **Lewian said:**
> Solved, thanks! I changed the BIOS settings. It's funny that even when USB keyboard support is disabled, I can use it in the BIOS settings to enable it, but here we go...

I don't mark the thread as "solved" because VoidQs problem is still there.

Thanks Lewian, very considerate, and congrats with solving your problem.

---

### Post by drs305 on 2010-09-05
VoidQ,

Thanks for the update. As I said, I'd never tried these settings - I appreciate your testing them out. I don't know why the menu isn't displayed with the first option, but the second should have been apparent since the keyboard doesn't work in the first place.  I apologize for the time you wasted trying this. I'll go back to my post and add a comment at the beginning saying these methods won't work.

---

### Post by VoidQ on 2010-09-05
No problem. That change may be the way to go for somebody else, just not me it seems. I wouldn't use my computer as a benchmark for others; it's old, full of junk and the hardware could give up the ghost at any given moment.

I've seen elsewhere on the net that someone suggested this change, but with the addition of the following line also:
GRUB_PRELOAD_MODULES="ohci uhci" 

Link below:
[http://savannah.gnu.org/bugs/?30429](http://savannah.gnu.org/bugs/?30429)

Grub not being something I am all that familiar with, can you explain what this additional change would do and is it something I should try?

---

### Post by drs305 on 2010-09-05
> **VoidQ said:**
> Grub not being something I am all that familiar with, can you explain what this additional change would do and is it something I should try?

Adding the line to /etc/default/grub will preload modules during boot - in this case the ohci and uhci modules found in the /boot/grub folder. They are USB modules, but I don't know if you can use them both simultaneously - I would first try one, then the other to see if either works separately.

Added Note: I can't find the "GRUB_PRELOAD_MODULES" option in the GNU GRUB manual, which was updated in Jul 2010, so I don't know if the line is active in /etc/default/grub or not. It still shows up in the actual commands run by grub-mkconfig so I assume it still works.

If not you could add an "insmod ohci" or "insmod uhci" command around line 105 of /etc/grub.d/00_header to incorporate the instruction into grub.cfg. Don't forget to update grub to incorporate any changes.

---

### Post by VoidQ on 2010-09-05
Thanks again DRS.

---

