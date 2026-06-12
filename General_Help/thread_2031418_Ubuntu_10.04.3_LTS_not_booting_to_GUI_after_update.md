---
title: "Ubuntu 10.04.3 LTS not booting to GUI after update"
date: 2012-07-21
forum: General Help
---

### Post by Grumblebum on 2012-07-21
I tried to resurrect this old thread that was closed on October 31st, 2011.  No replies, so I guess I need to restart it as a new thread.  It was at [http://ubuntuforums.org/showthread.php?t=1872247](http://ubuntuforums.org/showthread.php?t=1872247)

I have the same problem as that listed there. I run an old HP Compaq P4 2.8Ghz. dual booting with Windows 7. Booted to Ubuntu two days ago and got the same message deadlytackler got. Can't find the feature in BIOS, upgraded the BIOS and still can't find the feature. Tried all the suggestions at [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures), to no avail. Also tried the suggestion by oldfred. Everything went smoothly, but still have no desktop, only a command prompt. This was always a smooth running system and I only lost the desktop when I got the security message. Any assistance given would be much appreciated. Distro is 10.04 if I remember correctly....

---

### Post by CharlesA on 2012-07-22
That message just means your CPU doesn't support the NX.

What model of CPU do you have?

---

### Post by Grumblebum on 2012-07-22
Then why does it say "'This CPU is family 15, model 3, and has NX capabilities but is unable to use these protective features because the BIOS is configured to disable the capability. Please enable this in your BIOS. For more details, see: https://wiki.ubuntu.com/Security/CPUFeatures"?

CPU is listed as Intel Pentium4 CPU 2.8Ghz in W7 Control Panel and it shows two of them, so I guess it's a dual core.  I don't have any more detail than that.  What is confusing is that I didn't get the message until a few days ago and that is when I lost my desktop.  The OP got his message 12 months ago!  How do I get my desktop back?

---

### Post by CharlesA on 2012-07-22
It could be you had the error all along but never saw it cuz the GUI loaded.

Try booting into a previous kernel by holding down shift to get the grub menu and see what happens.

In any case, moved to General Help cuz the GUI isn't loading.

---

### Post by Grumblebum on 2012-07-22
Reverted from 41 to 38 and got the desktop back, but with greatly enlarged screen resolution.  Thanks for your assistance in that regard.  However I'm still not sure about the processor.  How is it that I only lost the GUI when I got the error message?  If I upgrade tp the latest LTS, will I still get the error?  I was trained in Microsoft, but as you can see, although I've been dabbling for a while I'm still very inexperienced in Linux.....

---

### Post by CharlesA on 2012-07-22
It might have been a botched kernel upgrade.

If you want to upgrade to 12.04, I'd suggest booting a livecd to make sure your hardware works with it before upgrading.

---

### Post by Grumblebum on 2012-07-23
Downloading ISO for 12.04 broke down half way through.  Is the ISO the same as a purchased CD?  Will report back when I get things sorted.

---

### Post by CharlesA on 2012-07-23
> **Grumblebum said:**
> Downloading ISO for 12.04 broke down half way through.  Is the ISO the same as a purchased CD?  Will report back when I get things sorted.
It is. Try to use a torrent, as it checks the ISO for errors while it is downloading, so you don't get a bad ISO.

---

### Post by Grumblebum on 2012-07-25
OK, finally downloaded 12.04, upgraded and updated, got my GUI back and all is running smoothly.  Using a torrent was a challenge on its own, because I'm using OpenDNS and they didn't want me going to torrent sites!

My only issue now is that the best screen resolution I can get is 1024 X 768, whilst on Windows (on the same machine) I get 1280 X 1024.  And yes, I have updated the Nvidia drivers....  Any suggestions?  Thanks heaps for your help thus far.

---

### Post by CharlesA on 2012-07-25
Are you using the drivers from the additional drivers applet? You could try using those.

---

### Post by Grumblebum on 2012-07-25
I went into the Display/Drivers section and changed the driver from the default used by Pangolin to the updated, upgraded proprietary offered for better performance.  I then rebooted, but noticed no difference in the presentation by Ubuntu.  However, it DID make a difference to my Windows interface, which seemed strange.  I would have thought the drivers would have been talking to the OS, rather than the BIOS, or the video card itself.

---

### Post by CharlesA on 2012-07-25
It should only affect your Ubuntu install.

In any case, it might be a good idea to create a new thread about the resolution problem since you are running 12.04 now.

Maybe someone else has run into that before.

---

### Post by Grumblebum on 2012-07-26
OK, thanks for your advice so far.

---

