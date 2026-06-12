---
title: "Windows is broken, and can't install linux"
date: 2006-05-28
forum: General Help
---

### Post by justin2021 on 2006-05-28
My friend has a HP computer that had windows xp on it. His windows broke, and now he is trying to install ubuntu breezy. For some reason though, it gives an error before booting. It has a black screen that says something like, NTLDR is missing, hit ctrl+alt+del to restart. He cant get into windows to fix it because it's not working. Live cd's dont work either. How do I fix something like this?](*,)

---

### Post by Sutekh on 2006-05-28
You need a Windows Installation CD.  Boot it, and enter the Rescue Mode.  You eventually end up at the DOS prompt.  There you can use ```
fixmbr
``` to restore the Windows bootloader to the MBR.

Then you can proceed to install Ubuntu.

In any case you should be able to bi-pass the failed Windows bootloader.  You just need to change your PC BIOS settings too boot from CDs before hard drives.

---

### Post by justin2021 on 2006-05-29
there is no windows installation cd... windows came with the HP computer

---

### Post by Sutekh on 2006-05-29
[quote=justin2021]there is no windows installation cd... windows came with the HP computer[/quote]
Ah, classic example of vendor lock-in.  I can't believe there is no Windows CD, I am surprised that it did not come with one.  

There is no recovery partition that you know of?  Do you know anyone who will lend you their CD?  All you need it for is the recovery mode.

---

### Post by gwpritch on 2006-05-29
The problem is that your box is trying to boot from the hard drive and you need it to boot directly from the CD. Are you not able to enter the bios setup?  Usually a message is displayed just before the bootloader takes control telling you how to do this. eg by pressing the delete key or one of the function keys.
From there you should be able to set the computer to preferentially boot from the CD before is moves on the the HD.

---

### Post by Ragazzo on 2006-05-29
Just a note about the cause of this error. Your friend probably deleted the file C:\ntldr which is hidden by default (system file) but can be turned on to show in the file explorer settings and then it's easy to remove this file accidentally (Windows doesn't warn you how important the file is). It happened to me once.

Edit: I think it's enough if you can copy the file ntldr from another Windows XP and put it back in the right place (with a boot disk).

---

### Post by H.E. Pennypacker on 2006-05-29
There is extensive literature on this online.  You'll find this error easily, with solutions, via Google.  It's better to go through Google than wait for replies, and its also best to exhaust all means before seeking forum help.  Because of limited time, its better for users to spend time on problems that don't have as much response as the NTLDR error.

---

### Post by steve.horsley on 2006-05-29
NTLDR problems indicate that it is still trying to boot windows from the hard disk. If you are giving up on windows and intend to install Ubuntu instead, ignore the NTLDR problem - it will go away once Ubuntu is installed.

Why don't live CDs work? Are you able to boot them? What to they say - what error mesage do you get? Maybe the problem is that the BIOS needs reconfiguring to try to boot from CD before hard disk.

---

### Post by crispy_420 on 2006-05-29
Check in bios and see if optical drive is scheduled to boot before hard drive. If hard drive is scheduled to boot first then that would explain why live cd's will not boot. During boot you should see a prompt for setup or something like that. Dig around your bios for boot order.

If you care about Windows but want to recover files from a broken system try using [Ultimate Boot CD for Windows]("http://www.ubcd4win.com/").

With this disc you also get many tools to repair windows or just recover Windows files. The only thing you may need is an external hard drive to recover to.

I have done this before to recover files from a non-bootable laptop.

---

### Post by drpaul on 2006-05-29
Is it going to take 1.5 GB of free disk space?

Paul

Whoops, wrong thread.

---

### Post by justin2021 on 2006-05-29
He configured to bios to load from the cdrom first but still the same problem. We also even tried removing the hard drive and using a live cd but it just says "no operating system found" We even tried using a windows xp cd to see if it would boot that, and no such luck, so im not sure if it will load the Ultimate boot cd 4 windows. We also tried switching out the cd drives and still nothing would boot, just the ntldr screen...

---

### Post by nalmeth on 2006-05-29
hmm, if the BIOS is configured to boot CD-ROM before HDD, then I can't only guess it's a bad CD image, bad burn, or both.

Can you confirm the liveCD's work in another computer?

Did you burn them properly (with burn iso specifically) and at a slow speed? Did you check the image integrity (md5.sum check?)

Is it possible to upgrade (flash) the BIOS, or the firmware for the drive? I have had this correct problem's in the past.

---

### Post by justin2021 on 2006-05-30
Ok, problem solved. What we did was took out his hard drive, and installed it throught his brothers computer. It seems to be running smoothly.

---

