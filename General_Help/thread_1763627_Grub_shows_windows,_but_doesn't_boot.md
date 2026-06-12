---
title: "Grub shows windows, but doesn't boot"
date: 2011-05-20
forum: General Help
---

### Post by footclan on 2011-05-20
Hi,

I have windows 7 installed, and I installed Ubuntu 11.04 after it. There was no grub, so I used an alternate cd of ubuntu 10.04 to repair it. 

Now, I have grub and windows is displayed, but I can't boot into it.

Windows is on sda2. I went into grub.cfg and found the entry....it said sda, so I changed it to sda2. I then ran update-grub. Windows still didn't work. At grub2, I chose to edit the command. Again, it said sda, not sda2. I kept changing it to sda2 and booting but windows doesn't start up.

Any ideas? I'm relatively inexperienced with ubuntu so I'm not sure what I'm doing wrong.

---

### Post by linuxinstalledfromhdd on 2011-05-20
You can try again by following this step-by-step

[http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/](http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/)

Might be a different way for you.

---

### Post by oldfred on 2011-05-20
Please post this so we can make specific recommendations if the above chroot does not work:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V56 has improved formating and requires code tags to make it legible.

---

### Post by footclan on 2011-05-20
It didn't work. I got an error at the gedit command. I tried it in my installed ubuntu and I know I got the GTK warning. I then booted up a live cd like it said and it said this.

> No protocol specified

(gedit:5756): Gtk-WARNING **: cannot open display: :0.0

Anything else I can try?

---

### Post by oldfred on 2011-05-20
If you are using the alternative installer, it is not a liveCD. You need to have a liveCD version.

---

### Post by footclan on 2011-05-20
I used the same cd for install as I did for the live cd, which was 11.04. I used the alternate to repair and bring back grub. And I get the same error and warning when I tried again not using the live cd.

---

### Post by oldfred on 2011-05-20
Can you boot into the recovery mode from the grub menu?

---

### Post by footclan on 2011-05-20
I'm not sure. How do I do that? I don't know much relating to ubuntu.

---

### Post by oldfred on 2011-05-20
Are you getting a grub menu when you boot from your install on the hard drive? The second entry is the recovery mode. 

If you do not get a menu, try holding shift key from BIOS until menu appears.

Did you run liveCD in liveCD mode before installing to make sure your system worked with Ubuntu?
Sometimes on initial boot of CD when tiny icons are at bottom of screen you have to hit a key, then press f6. Try nomodeset.

You have to get one or the other working enough to be able to repair it.

---

### Post by linuxinstalledfromhdd on 2011-05-20
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by footclan on 2011-05-21
> **oldfred said:**
> Are you getting a grub menu when you boot from your install on the hard drive? The second entry is the recovery mode. 

If you do not get a menu, try holding shift key from BIOS until menu appears.

Did you run liveCD in liveCD mode before installing to make sure your system worked with Ubuntu?
Sometimes on initial boot of CD when tiny icons are at bottom of screen you have to hit a key, then press f6. Try nomodeset.

You have to get one or the other working enough to be able to repair it.
 I do get a grub menu when I boot from my hdd and recovery mode works. 

I've used various live cds and had various ubuntu versions installed on this pc before without any prior problems. Ubuntu and the live cd seem to run without any problem, it's just I can't access windows.

---

### Post by oldfred on 2011-05-21
If you are in Ubuntu on hard drive or in liveCD download and run the bootinfo script. We cannot help if we cannot see the details of your system.

New version of script downloads as a zip file which you have to extract to get the .sh file that you run per the instructions.

---

### Post by footclan on 2011-05-21
I got into windows. I forgot to mention that what was showing in grub was the windows 7.  I put in the windows 7 disc annd went to recovery. Instead of startup repair, I went to the command line and entered I /FixBoot and /fixmbr. I can't get into ubuntu right now but I'm sure I'll figure it out with easybcd.


I had tried the bootinfo script and compared my info to another forum post seeking help but it didn't solve the problem.

Thanks for all your help.

---

