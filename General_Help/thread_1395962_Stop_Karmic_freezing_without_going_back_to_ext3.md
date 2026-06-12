---
title: "Stop Karmic freezing without going back to ext3?"
date: 2010-02-01
forum: General Help
---

### Post by FM1 on 2010-02-01
I've searched and come up with lots of freezing threads, but none exactly like mine. Desktop running a clean install of Karmic with ext4, /home on a separate ext3 partition. If I attempt to use Nautilus to copy a file over 1GB (that seems to be the tipping point) from Desktop to another partition or an external HDD, or if I download anything at the same time as I'm copying any file, the system freezes completely (no mouse, keyboard lights flash and keypresses don't register), and the only thing I can do is hit the reset button. I don't know enough to figure out exactly what's causing it, but I think it's ext4; this very same hardware ran Jaunty with ext3 like a champ, but when I installed Karmic, I formatted that partition to ext4, and that's when the freezing started. In the event that I don't know what I'm talking about and it's actually video drivers, I am using the Nvidia driver (185) on a GeForce 6200 because I use TwinView and don't know how to do a spanned desktop without it. I had used Nvidia drivers in Intrepid and Jaunty, though, with no problems. I have no Compiz effects enabled at all. 

I'm perfectly willing to go back to ext3 (I think I remember how to make the list to "auto-install" applications, and /home is separate anyway), but if it is ext4 causing the problem, I'm still likely to run into it because one of my external HDDs is formatted ext4, and I don't really have anywhere to stick nearly 1TB of photos and video to reformat it ext3. Ultimately, if that's what it takes to fix the freezing, I'll do it, but I'd rather not. I *like* Ubuntu...I've used it since Warty, but this is wearing me out. I will carefully follow instructions and do nearly anything; I just want the freezing to *stop*. :(

---

### Post by QIII on 2010-02-01
I use ext4 with no issues such as yours.

Could you provide a little more information on your hardware setup?

Is your external drive being powered from the USB bus, or do you have a dedicated power supply?

---

### Post by FM1 on 2010-02-01
An old desktop, not a branded system. AMD Athlon 3400+, 2GB RAM, Nvidia 6200, mobo is Abit KU8. Wired connection only. Two internal ATA HDDs. First internal HDD partitioned for XP and Karmic (ext4), swap, and /home on a separate ext3 partition. Second internal HDD is storage; FAT32 and ext3. Two WD "MyBook" external HDDs that have their own power supplies; 320GB partitioned NTFS and ext3, the 1TB is all ext4. Currently, the external drives are plugged into a hub, but I did try plugging the ext4 drive directly into the USB port on the mobo and it still froze when I tried to copy a 4.0GB DVD image.

---

### Post by oshunluvr on 2010-02-01
If you do a little internet searching you may also see that the newest kernels coming out have issues with ext4 (they're calling it a "regression"). If you want better performance than ext3 without the bleeding-edge issues that come with ext4 you might try reiserfs instead.

I've had no problems with it for years, is definitely faster than ext3 (and more stable in my experience) and it works with legacy GRUB which ext4 does not.

---

### Post by FM1 on 2010-02-03
Thanks. I ended up just going back to ext3 (I know--no sense of adventure); with /home separate anyway and the magic of dpkg and dselect, it didn't take long to get everything back as it was. I'm leaving the external as ext4 for now, but if I still get the freezes, I'll bite the bullet, back everything up and reformat it, too.

---

