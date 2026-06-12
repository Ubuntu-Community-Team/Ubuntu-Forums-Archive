---
title: "Boot Error"
date: 2010-09-14
forum: General Help
---

### Post by ki4jgt on 2010-09-14
[Short and Sweet] My aunt got a computer virus for windows 7. I tried installing Ubuntu and on boot from my flash drive I got Boot error. How can I install Ubuntu so she can use it while she is waiting for her windows restore discs from Dell?

---

### Post by wilee-nilee on 2010-09-14
> **ki4jgt said:**
> [Short and Sweet] My aunt got a computer virus for windows 7. **I tried installing Ubuntu** and on boot from my flash drive **I got Boot error**. How can I install Ubuntu so she can use it while she is waiting for her windows restore discs from Dell?

If W7 is toast and your just waiting for the OEM discs you can pull out stuff needed for saving with the live cd on a thumb .

So how did you load the USB? Are you aware of the f-key prompt to have a choice of boot, mine is f12, this method works better sometimes. Could be esc any number of keys. You just start clicking on it as soon as you power on.

Unetbootin is a good thumb loader it is in Ubuntu but must be installed. Here is a link to their site for a MS version.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

So we want to know does anything need to be salvaged?

This can be done in several ways, from deleting W7 and fully installing Ubuntu until the recovery discs arrive, or resizing W7 then installing in a open space.

At the least if you can get booted and you decide what you want, to do, post a screenshot of gparted in Ubuntu.

It is kind of hard for me to tell if you actually installed and it wont boot or the thumb wont boot.

---

### Post by ki4jgt on 2010-09-14
Thumbdrive wont boot w/ Ubuntu on it. All I get is a black screen with "BOOT ERROR" at the top. I think Dell's chessy hardware doesn't want Linux on the computer.

---

### Post by wilee-nilee on 2010-09-14
> **ki4jgt said:**
> Thumbdrive wont boot w/ Ubuntu on it. All I get is a black screen with "BOOT ERROR" at the top. I think Dell's chessy hardware doesn't want Linux on the computer.

A thumb loaded correctly with a good ISO should boot from the key prompt Dell has a problematic program in W7, possibly, but you would have to have installed Ubuntu to trigger it I think.

Again; how did you load the thumb and did you check the MD5SUM of the ISO?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by BkkBonanza on 2010-09-14
All you should need to do is enter the BIOS during initial system startup and make sure that, under boot options, USB is set for both Mass Storage type, and bootable. It needs to be the first boot device in priority. Some older systems don't have this option. I don't know about Dell. 

It won't work if USB is set as FDD (floppy drive), or Zip drive mode. (These modes can work but only with special boot image configurations that are a lot more complicated to prepare)

If you created the USB flash image with menu item "System, Admin, Startup Disk Creator" then I know it makes a bootable image that works for USB.

---

### Post by ki4jgt on 2010-09-15
I created it with Unetbootin and the ISO is fine. I booted it with my laptop just swell.

---

### Post by cariboo on 2010-09-15
This isn't a security question, moved to General Help.

---

### Post by ki4jgt on 2010-09-19
Sorry LOL. The lights were on, but no one was home :-)

---

### Post by mrinehart93 on 2010-09-19
See if there is an option to enable "BBS Popup" in the BIOS. If that is enabled, whenever you boot, it should ask you what device you want to boot with.

---

