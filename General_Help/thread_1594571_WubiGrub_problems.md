---
title: "Wubi/Grub problems"
date: 2010-10-12
forum: General Help
---

### Post by RHogskin on 2010-10-12
This is going to sound bizarre, at least it seems so to me. I previously installed 10.04-64 on a Vista-Home 64 system using Wubi. Ran it successfully for some time until my Wubi install somehow became corrupted.
I decided to take the plunge and resize my partition and do a dual boot (using this tutorial: [url]http://apcmag.com/how_to_dualboot_vista_with_linux
_vista_installed_first.htm[/url])
I started by using Revo-Uninstaller to uninstall Wubi. To make a long story short, I download 10.10-64, burn the iso image to cd using "Infrarecorder" Somehow, the cd I burn, instead of being a Ubuntu Live Install disc, is a Wubi install disc! Obviously there is still an (active) remnant of Wubi/Grub somewhere in my Windows system.
I am a relative Linux newbie, but I am quite familiar with Windows and what I am describing should not be possible. My immediate plan is to burn the image on a different computer, but I really want to purge this gremlin from my system. Has anyone else seen anything like this?

---

### Post by Rubi1200 on 2010-10-12
In order for us to see what may be left of an old install, please boot the computer with a LiveCD and post the results of the boot-script linked at the bottom of my post.

Additionally, are you able to boot into Windows? What about Ubuntu?

---

### Post by RHogskin on 2010-10-12
I haven't been able to boot into Ubuntu or other Linux using LiveCDs. I have 32-bit versions of Mandriva and Fedora, in addition to Ubuntu that I have tried.

I can boot into Windows without any problem. Everything seems to be working normally while in Windows. I only discovered that the new LiveCDs I have been burning were actually being burned as WUBI-install discs this morning. I initially thought the problem with the LiveCD was a corrupted iso image.

---

### Post by bcbc on 2010-10-12
There is no such thing as a wubi install disk. The standard ubuntu CD image contains the file wubi.exe that allows you to install ubuntu under windows, but it uses exactly the same image as for a normal install (wubi just modifies it on the fly to allow you to run Ubuntu from a virtual disk.)

---

### Post by RHogskin on 2010-10-12
I just figure that out. I didn't realize it was part of the standard LiveCD. I still have the problem of not being able to boot into the LiveCD, but the other part is just non-sense. Sorry about that.

---

### Post by bcbc on 2010-10-12
> **RHogskin said:**
> I just figure that out. I didn't realize it was part of the standard LiveCD. I still have the problem of not being able to boot into the LiveCD, but the other part is just non-sense. Sorry about that.

No need to apologize :) 

Generally... if you burn a live cd you want to do it on the slowest speed. I haven't had a bad burn except on a rewritable CD. Then you just find the key to get the bios boot options (on my comp it's F12, then select CD-ROM) or enter the bios setup and set it to boot from cdrom first.

---

### Post by drs305 on 2010-10-12
I don't think you'll be able to remove 'remnants' of a Wubi install via Windows at this point, but normally you remove Wubi via the Window's Control Panel Add/Remove option.

---

### Post by 1Dagars1 on 2010-10-12
Just an FYI - the link goes to a blank page with only "Bad Request" echoed

---

### Post by 1Dagars1 on 2010-10-12
> **RHogskin said:**
> 
I decided to take the plunge and resize my partition and do a dual boot (using this tutorial: [URL="http://apcmag.com/how_to_dualboot_vista_with_linux%3Cbr%20/%3E%0A_vista_installed_first.htm"]http://apcmag.com/how_to_dualboot_vista_with_linux
_vista_installed_first.htm[/URL])

Just an FYI - the link goes to a blank page with only "Bad Request" echoed

---

### Post by bcbc on 2010-10-12
> **1Dagars1 said:**
> Just an FYI - the link goes to a blank page with only "Bad Request" echoed

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

