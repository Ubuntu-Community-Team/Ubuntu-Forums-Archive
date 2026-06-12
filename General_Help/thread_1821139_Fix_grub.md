---
title: "Fix grub"
date: 2011-08-08
forum: General Help
---

### Post by hulslanderam on 2011-08-08
So I deleted a partition that showed up in windows to get more space (I thought it was one I had accidentally made but it must have been important) and now grub doesn't recognize any of my os's, I get "unknown filesystem grub recovery" I currently am running on a 10.04 live usb. How do I fix the grub? I have even loacted the grub.cfg file in my ubuntu partition if that helps. I have tried several other guides but they didn't seem to help.

---

### Post by Sotanaht on 2011-08-08
I've messed up GRUB 3 or 4 times before and I still don't know how to fix it without help.  GRUB is such a pain ](*,)

You just need to run a few commands from the liveUSB usually.

---

### Post by MG&amp;TL on 2011-08-08
I completely agree...

Reinstall ubuntu over ubuntu; try an 'upgrade' rather than reinstall. If the installer finds anything at all.

---

### Post by garvinrick4 on 2011-08-08
> **hulslanderam said:**
> So I deleted a partition that showed up in windows to get more space (I thought it was one I had accidentally made but it must have been important) and now grub doesn't recognize any of my os's, I get "unknown filesystem grub recovery" I currently am running on a 10.04 live usb. How do I fix the grub? I have even loacted the grub.cfg file in my ubuntu partition if that helps. I have tried several other guides but they didn't seem to help.
Use your live USB and Do this:
Just a guessing game unless we see a boot script as per below:

#Download this Script to DESKTOP:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
#Open a Terminal and use these four commands one at a time. copy and paste if you want
```

cd Desktop
unzip boot_info_script060.zip
chmod +x boot_info_script.sh
sudo ./boot_info_script.sh

```
#There will now be a file called RESULTS  on Desktop copy and paste to this Thread:
Use code tags and will be easier to read: (Highlight all text after pasting and click on # sign in upper right of message box)

This is what you just did below:
1. You are changing directory's to Desktop
2. You are unzipping 
3. You are making script executable
4. You are executing the Script
5. Done Results on Desktop

---

