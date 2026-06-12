---
title: "Ubuntu ate Windows"
date: 2010-11-01
forum: General Help
---

### Post by -Fenrir on 2010-11-01
I had **only** Windows Vista installed and attempted a dual-boot install of the latest version of Ubuntu.
 
I went through the install process fine until I hit the part where you enter your username and password. I didn't know that the username needed to be captialized, so when I hit that problem, I did a hard reset.
 
Found the problem, came back and when through the installation process again. This time I **delete**d the linux swap partition and Ubuntu's partition with the installation disc's software and went through the installation, but got the I/O error after the disc was ejected mentioned here: [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)
 
I didn't know that everything was fine and that I just needed to hit enter, so I did another hard reset, deleted linux swap and Ubuntu's partitions, went through the install again--same error. Another hard reset. Found out what the problem was, but didn't need to do another install because Ubuntu was working fine.
 
Now Windows is broken. After booting, I got the option to start up Ubuntu, memtest, Windows XP, and Windows Recovery Environment. Thinking that Vista was either having an identity crisis or trying to placate me by masquerading as his ancestor, I chose Windows XP. I get a recovery menu. I try to use my Windows recovery discs. They go through the process of recovery, but nothing was different upon reboot. No magic.
 
Obviously not in my right mind, I figure that installing Ubuntu without the hard reset will somehow do something. I'm a blind man stumbling about in a dark room. I reboot with the Ubuntu installation disc in the drive, and delete the swap partition and Ubuntu's little slice of the hard drive again. Now I try to use the "install alongside" option as before, but now Ubuntu is not content with having its own partition. No, it wants to live with Vista, or at least that is what I thought at the time, but now I realize that what I'm typing doesn't make sense. Anyway, suffice to say: another HARD RESET. Now the boot loader is totally confused, because I just screwed with its innards, and it's saying:
 
Verifying DMI Pool Data.....
error: no such partition
grup rescue>_
 
I hope this explanation isn't as stupid as the way I managed to break it. This is clearly not my day for clear thinking.

---

### Post by Mark Phelps on 2010-11-02
Your post says it "ate Windows" -- which normally means that MS Windows is GONE.

Have you confirmed that?  Try booting from the LiveCD, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one) and confirming that your Vista NTFS partitions are still there.  IF they are, while still in the LiveCD, go into Places and confirm that you can mount the NTFS partitions and see files on them.

If those both work, then Ubuntu did NOT eat Windows -- that's the good news.  What it did do is replace the Vista MBR with GRUB -- which because it will NOT boot into Vista, and apparently will not boot into Ubuntu either, has turned your PC into an electric brick.

You mention using Recovery Disks.  If these are more than one disk, they generally go through the process of completely reformatting and repopulating the hard drive -- which would wipe out everything on it, but would then leave you with a working machine.  The fact that you said this did not change anything is what I find confusing.

If all you have is a single Recovery CD (not DVD), and your machine came preloaded with Vista, what it most likely did was try to do a recovery from a (now missing) recovery partition and -- since that failed -- did not change anything.

An alternative, which you should consider, is to go to the proper link below, download and burn the proper Vista Repair CD image, boot from that, and run Startup Repair three times -- that's right, three times.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by coreyscx on 2010-11-02
haha i think ubuntu got fat :P

---

