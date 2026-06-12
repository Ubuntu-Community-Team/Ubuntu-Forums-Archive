---
title: "NTLDR message after deleting windows"
date: 2010-03-10
forum: General Help
---

### Post by Bebopsamurai on 2010-03-10
Recently upgraded to latest ubuntu release, dual booting windows and ubuntu. Got the gist of ubuntu quickly, thought to go ahead and delete the windows data in my partition. Evidentally didnt have it partitioned correctly, as the next time I rebooted, I recieved an "NTLDR is missing Ctrl+Alt+Del." message. I cannot reboot from a bootpatch usb/cd, as I took out everything pertaining to windows allready. However, I know that this can't be a hardware problem. Is there a way to fix BIOS to operate from ubuntu? Or did I pretty much hose myself?

---

### Post by eriktheblu on 2010-03-10
Was this a Wubi install?

---

### Post by Brandon Williams on 2010-03-10
It sounds to me like you still have the original code in the MBR. What did you do to get it to dual boot? Did you install grub to the MBR in the original ubuntu installation? If not, then you should boot from a live CD and install grub to the MBR.

[Here](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) is a link that that will help if this is the problem. It talks about fixing the MBR after a windows install overwrites it, but it will also help if you never installed grub to the MBR in the first place.

---

### Post by elliotn on 2010-03-10
This is because ur pc boots into a partition that use to have windows.

---

### Post by Bebopsamurai on 2010-03-11
RE: Brandon Williams;
 
Thanks, this did the trick. I dont know why I didnt make an image disc from the start, and I dont know why I didn't install GRUB either. Ahh, impetuous youth, no? Thanks for the suggestion.

---

