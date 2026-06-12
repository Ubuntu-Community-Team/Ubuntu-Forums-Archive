---
title: "Ubuntu 10.10 won't boot after install"
date: 2011-02-12
forum: General Help
---

### Post by dpapathanasiou on 2011-02-12
I'm trying to use 10.10 on an old hand-me-down HP desktop. The CPU is an AMD Athlon 64 3000+ (rev. E6), and the motherboard bios is Phoenix Award Workstation (v. 1.18).

Installing 10.10 from the live cd was no problem, but when I rebooted, nothing happened. All I saw was a flashing cursor in the top left of the screen, and the hd indicator light was off.

After reading this guide about grub2 ([http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)[]("http://ubuntuforums.org/showthread.php?t=1195275")), I went back and reinstalled grub2 from the live cd.

That was successful, but when I tried to reboot off the hd, I got the same result.

Then I saw this post about ACPI ([http://askubuntu.com/questions/15671/ubuntu-usb-startup-disk-doesnt-boot/15674#15674](http://askubuntu.com/questions/15671/ubuntu-usb-startup-disk-doesnt-boot/15674#15674)).

The bios on my machine has both APIC and ACPI enabled by default.

So I disabled both of them, and also went in with the live cd to edit the grub config file, to include acpi=off in the GRUB_CMDLINE_LINUX parameter.

When I reboot from the hd now, I get "Read Error" in the top left corner of the screen, instead of the flashing cursor.

So it seems either ACPI or APIC or both have something to do with the problem, but I'm not sure what to do next.

Any suggestions?

---

### Post by dpapathanasiou on 2011-02-13
I noticed that the installer reported my single hard drive as "SCSI /dev/sda" when in fact it's an IDE drive.

Apparently this is normal ([http://superuser.com/questions/75102/any-reason-why-ide-disk-hda1-shows-up-as-sda1-under-knoppix-live-cd/75498#75498](http://superuser.com/questions/75102/any-reason-why-ide-disk-hda1-shows-up-as-sda1-under-knoppix-live-cd/75498#75498)) but the prior OS I had installed (Debian 5.0) identified the drive correctly as "IDE /dev/hda".

So rather than an ACPI issue, I started to think the "Read Error" grub gave me was due to misidentifying the hard drive.

I tried having grub seek the drive by its UUID as opposed to /dev/sda, as described here ([http://lists.debian.org/debian-user/2009/12/msg01537.html](http://lists.debian.org/debian-user/2009/12/msg01537.html)), but that didn't solve the problem either.

Any ideas what to do next?

---

### Post by oldfred on 2011-02-13
You may be past boot issues. If you hold down shift key from BIOS until menu appears do you get a menu? Then it may be video issue. What video card/chip do you have?

If you cannot get to menu. It may be boot issue.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by dpapathanasiou on 2011-02-13
Fred, many thanks for your reply & suggestions.

Actually, this turned out to be a hardware problem.

The jumper on my IDE drive was set to "Cable Select".

That drive shared an IDE cable with the CD drive, and in the BIOS the hd appeared as "Master", with the CD drive appearing as "Slave".

Since a similar post ([http://ubuntuforums.org/showpost.php?p=1096497&postcount=6](http://ubuntuforums.org/showpost.php?p=1096497&postcount=6)) fixed his problem by changing the cable, I tried the same thing.

Without changing any of the jumpers on either the hd or the CD drive, I replaced the IDE cable.

This time, the BIOS couldn't find either the hd or the CD drive. So I explicitly set the hd jumper to "Master", and rebooted with the new cable.

The BIOS found the hd as "Master", and the CD as "Slave".

So, everything was exactly as before, right?

Well, when I installed the OS again, making no changes to any of the grub defaults (i.e., I let grub install into the MBR), it worked!

In the end, I'm not sure if the old cable was faulty, or why the new cable needed the jumper change so that the BIOS would recognize the hd, but the issue is resolved, and I can boot into my system normally now.

---

### Post by oldfred on 2011-02-13
Are you mixing 40 conductor and 80 conductor cable select cables? Often Cds just have the old 40 conductor cable. Some drives also had a master with slave setting jumper as well as master and cable select.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by dpapathanasiou on 2011-02-14
Interesting, I didn't realize there was a difference in IDE cables.

The original cable was a type 80, and the one I replaced it with is a type 40.

So that explains the jumpers.

But what I don't understand is why grub couldn't find the drive when booting in the original configuration?

Both the BIOS and the installer could identify it, and when I went in to the filesystem via the live cd, I could see that all the files were there.

It seems strange that a cable change had this effect.

---

### Post by oldfred on 2011-02-14
That was part of the reason my last computer build was all SATA. The tiny jumpers were getting too hard to see & manage. 

Even though with BIOS I set any drive as boot drive, it refers to it as primary master when set.

---

