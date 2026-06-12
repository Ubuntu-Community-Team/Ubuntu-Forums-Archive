---
title: "GRUB 2 Windows 7 Microsoft Security Essentials"
date: 2010-02-05
forum: General Help
---

### Post by eshwar_andhavarapu on 2010-02-05
Hi,

I have Ubuntu Karmic 64-bit dual boot with Windows 7. On Windows 7 i have microsoft security essentials for antivirus/antispyware. Recently I noticed GRUB boot failures after having booted to windows but couldn't see why. Just to be clear, I am using GRUB2. Anyway, the failure is as follows:


[LIST=1]
[*]PC is powered on, goes on towards displaying GRUB menu but
[*]it only shows GRUB Loading and restarts, so the list doesn't show.
[*]and the restart keeps happening.
[/LIST]
Now the workaround so far is to boot using a live cd and fix GRUB according to the instructions posted here: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

And after fixing GRUB2, i either have to boot into the desktop or recovery mode, to update GRUB2 menu once again using ```
update-grub
``` command and then everything works.

Now coming to what i think is the cause of the problem. Everytime MSE (microsoft security essentials) is updated be it standalone, or over internet, including failed updates, the boot failure happens.

I've googled microsoft and ubuntu forums but couldn't find a fix :(

So please could somebody help me?

---

### Post by lotharmat on 2010-02-05
Could you try unistalling MSE and replacing it with AVG or Avast

See if you get the same issue.

---

### Post by eshwar_andhavarapu on 2010-02-05
> **lotharmat said:**
> Could you try unistalling MSE and replacing it with AVG or Avast

See if you get the same issue.

well the thing is I am impressed with MSE and its free too, so I would like to keep it. AVG i understand also has a free version but not a fan of it. Just looking for workarounds for this problem. I'm sure it affects Vista too. and possibly other GRUB2 dual boot setups.

---

### Post by Techsnap on 2010-02-05
MSE doesn't affect GRUB2. I know it doesn't. I'm sure it's something else, try running a scan, there might be a reason it's doing this every time if it is MSE.

---

### Post by wilee-nilee on 2010-02-05
I have W7 and lucid and have used MSE periodically with no problems, there is no reason a AV would mess with the grub files or MBR.

---

### Post by eshwar_andhavarapu on 2010-02-05
> **Techsnap said:**
> MSE doesn't affect GRUB2. I know it doesn't. I'm sure it's something else, try running a scan, there might be a reason it's doing this every time if it is MSE.

i'm guessing you're running a similar configuration

---

### Post by eshwar_andhavarapu on 2010-02-05
> **wilee-nilee said:**
> I have W7 and lucid and have used MSE periodically with no problems, there is no reason a AV would mess with the grub files or MBR.

maybe i got you wrong but its only when trying to update. wonder why MSE would have something that affects boot in the updating routine. assuming that's the cause.

but otherwise, the problem stays. I have to occasionally reinstall grub to make things back to way they were.

---

### Post by Techsnap on 2010-02-05
> i'm guessing you're running a similar configurationI was running a similar configuration when I made the Ubuntu rant videos, MSE didn't do anything to GRUB2 at all.

Anyway have you tried running a quick scan on there. Then if you can, try another AV and see if GRUB2 still breaks after a while so we can determine if it really is MSE.

---

### Post by john newbuntu on 2010-02-05
To determine if MBR is being changed by a (malicious?) program and until you find the exact culprit, there is a tool for windows called mbrwiz that will help you backup and restore MBRs.  Download this and backup your MBR.  Restore it via a shutdown script in windows.  If the problem still persists, we can at least rule out MBR being tampered with.

While in windows, take periodic backups of MBR and compare them after running scans to see if it changes.  Keep in mind to keep track of MD5 hashes or some such CRC checks on these files to make sure that the malware did not meddle with these backups (or the mbrwiz program itself).

---

### Post by eshwar_andhavarapu on 2010-02-05
I should try that out!

---

### Post by morphy125 on 2011-03-04
I install ubuntu 10.x on a netbook and MSE thought grub was a dos/alureon.a virus. And Kaspersky tdsskiller said it was root kit.win32.tdss.tdl4 this took out grub. When I rebooted the startup menu was gone and when the drive was rescaned all clear. Any Ideas as I am new to Linux also I still want to dual boot the netbook with xp, it is an eee pc1001ha with windows install on the harddrive. Thanking you for any replies M

---

