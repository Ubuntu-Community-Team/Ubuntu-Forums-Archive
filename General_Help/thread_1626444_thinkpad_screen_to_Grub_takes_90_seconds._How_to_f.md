---
title: "thinkpad screen to Grub takes 90 seconds. How to fix it?"
date: 2010-11-20
forum: General Help
---

### Post by newboyo on 2010-11-20
Hi all,

I use a T410 with lucid LTS 32 bit and win 7 (which is rarely used). Till last night, GRUB would load up 5 seconds after the Lenovo welcome screen.

This morning onwards it takes exactly 90 seconds. i've tried rebooting several times - exactly 90 seconds.

I can't understand what or where to look for solutions - so am posting this weird problem.

Thanks for your help.

rgds

New

---

### Post by oldfred on 2010-11-20
Does your NTFS partition need a chkdsk. Sometimes Ubuntu will not mount the NTFS partition if it needs chkdsk run. Not sure if it would slow grub down also or not.

Did you change any BIOS settings?

Have you plugged in any new external devices. One user had a CD in the tray and the system wanted to run fsck on the CD?? USB devices may require grub to check and it takes extra time?

Double check hardware, did a connection come loose, in laptops it probably is not the issue, but..

---

### Post by newboyo on 2010-11-20
> **oldfred said:**
> Does your NTFS partition need a chkdsk. Sometimes Ubuntu will not mount the NTFS partition if it needs chkdsk run. Not sure if it would slow grub down also or not.

Did you change any BIOS settings?

Have you plugged in any new external devices. One user had a CD in the tray and the system wanted to run fsck on the CD?? USB devices may require grub to check and it takes extra time?

Double check hardware, did a connection come loose, in laptops it probably is not the issue, but..

Hi Oldfred,

Checked your suggestions (except for the hardware connections - it is a new laptop). No luck at all. there is no hard disk activity once the lenovo screen comes on. At the 90 second mark - hard disk activity lights up and GRUB loads. Seems as though there is a sleep for 90 seconds command somewhere. Even going into the BIOS makes me wait for 90 seconds.

---

### Post by oldfred on 2010-11-20
It sounds like BIOS is doing an extended memory check or issues mounting drives.

Does your BIOS let you hide BIOS logo and see the BIOS boot tasks?

---

### Post by newboyo on 2010-11-20
> **oldfred said:**
> It sounds like BIOS is doing an extended memory check or issues mounting drives.

Does your BIOS let you hide BIOS logo and see the BIOS boot tasks?

Hi there,

I'm afraid i can't make this out - probably not. i tried viewing the various options in BIOS, but couldn't see one for either memory check or hiding the bios logo.

There was an option for quick boot which is enabled.

---

### Post by oldfred on 2010-11-20
Not a BIOS setting but as the BIOS boots. Mine pops up immediately with a logo and the keys to open BIOS, choose boot drive and see what BIOS is doing (behind logo) is also an F key. It may show something.

---

### Post by newboyo on 2010-11-20
Hiya Oldfred,

Thanks vm. I changed the bios from quick boot to enable test and it works fine now. the Lenovo welcome screen is gone and I can see what is going on behind.

thanks once again.

---

### Post by oldfred on 2010-11-21
Glad it is working. 

It is very strange that turning off quick boot speeds up boot.

---

