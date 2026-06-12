---
title: "problem with hp pavilion"
date: 2009-10-23
forum: General Help
---

### Post by smoke_banshee on 2009-10-23
hi, i am quite new to ubuntu, but have read these forums for a few months... whenever the troubleshooting need arises

i have been using 9.04 fine on a old pentium 1.2g for 6 or so months but recently wanted to dual boot on a newer pavilion a6157c.

the 9.04 (and also the 8.10 i tried) live CD stops in the initial process of disk reading with a error of...

rc-default main process (4266) terminated with status 127 (something to that effect)

any help will be greatly appreciated and i await the day that wine/cedega/playonlinux is developed enough that my gaming urges does not require any windows dual booting at all

---

### Post by Giblet5 on 2009-10-23
That box (stock, at least) should work just fine with 7.04 and up.

I qualify that with "stock" because a Pavilion case with an Asus x58 motherboard and i7 cpu is, from all appearances, a Pavilion. It won't likely boot a 8.10 CD though.

Did you burn the install image to a Kalamazoo (aka cheap) brand CD?

I have an older HP burner on one machine that can't read Verbatim brand CDs that it created. I fixed that by never creating disks on that machine. ;)

I suspect a bad CD, burn, or corrupted ISO image.

Ubuntu gives you the md5sum of their images. You can verify the image by comparing the md5sum.

---

### Post by smoke_banshee on 2009-10-23
well, the system is not "stock"

i have put in a nvidia 6200 card (that had worked well in the old 1.2) and i pulled the t.v. tuner card and the dial up modem, because i thought them to be useless...

might that be the problem?

---

### Post by smoke_banshee on 2009-10-23
oh and i am not sure about the cd burn theory because 8.10 and 9.04 are on two different types of disks burned different ways and both had the same error

---

### Post by P4man on 2009-10-23
verify the disc for errors (its an option in the cd boot menu)

If that checks out, perhaps check your bios for SATA settings. Ive seen machines not boot when some sata setting was set (dont remember the name... Im afraid. heh). assuming its a sata optical drive

---

### Post by Giblet5 on 2009-10-23
Well, you shot THAT idea down.

I recommend burning a CD from one of the "Alternate" install images.

You can grab a Jaunty (9.04) alternate image from here:
[32-bit 9.04 Alternate]("http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-i386.iso")
[64-bit 9.04 Alternate]("http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-amd64.iso") 

They're not as pretty during the installation, but it avoids many of the possible hardware problems involved in the GUI installer.

Other than this, I got nuthin'

---

### Post by Giblet5 on 2009-10-23
> **P4man said:**
> verify the disc for errors (its an option in the cd boot menu)

If that checks out, perhaps check your bios for SATA settings. Ive seen machines not boot when some sata setting was set (dont remember the name... Im afraid. heh). assuming its a sata optical drive

Yes......and HP likes to default to that, too. Only Windows recognizes it and it provides lousy performance.

It's 'drive access type' (or very similar) on the first screen of BIOS setup. It should be "IDE". Windows likes that better as well.

Thanks again, P4man.

---

### Post by P4man on 2009-10-23
it was named differently on my machine. Something like AHCI ? Dont remember, I just remember I needed to upgrade my bios before the option was even there. Until I did, nothing except vista would work properly with the DVD drive. XP install cd  wouldnt even boot. 

Anyway you can always make a bootable USB stick and try that. Its faster and more convenient too.

---

### Post by Giblet5 on 2009-10-23
> **P4man said:**
> it was named differently on my machine. Something like AHCI ? Dont remember, I just remember I needed to upgrade my bios before the option was even there. Until I did, nothing except vista would work properly with the DVD drive. XP install cd  wouldnt even boot. 

Anyway you can always make a bootable USB stick and try that. Its faster and more convenient too.

The field label is 'drive access type' and one of the options is ahci. It needs to be IDE or SATA (SATA would be a misnomer, but it's HP...they don't hire the sharpest sticks in the bundle).

---

### Post by flipper9 on 2009-10-23
I'm not sure if your computer supports this, but can it boot from a USB Key?  If so, I find that installs are faster and more reliable by using unetbootin to put the install files on the USB key and then boot from the USB key to do the installation.

---

### Post by smoke_banshee on 2009-10-23
i dont have a usb stick big enough (insert bad joke here) or i would try that...

ok, here's what he have so far

tried the different boot order, that was a "no-go" as well

i Do get different 4-digit rc-default main process numbers on that though...

well i am going to try the alternate ISO's and see what that does...

---

### Post by smoke_banshee on 2009-10-23
Oh, and BTW, the error check came out okay as well

---

### Post by P4man on 2009-10-23
> **smoke_banshee said:**
> i dont have a usb stick big enough (insert bad joke here) or i would try that..

You actually have a stick smaller than 1GB? 
They sell for like 10 Euro, go buy one, Or buy 3. Always handy to have around. But yeah in the meanwhile perhaps the alternate cd will work.

---

### Post by Giblet5 on 2009-10-23
> **smoke_banshee said:**
> Oh, and BTW, the error check came out okay as well

Did you change the drive access mode in BIOS? (Restart, hit F2 at the HP boot splash)

The option will appear on that first screen, toward the bottom.

Ubuntu will not install if it's set to AHCI, unless there have been major downgrades in Linux since I had a Pavilion...

---

### Post by smoke_banshee on 2009-10-23
actually no.

what i DID do, was hit ESC and changed the boot order...

i am currently downloading the alternate, (cant have to many ubuntu install disks :) ) then i will try that too.

---

### Post by smoke_banshee on 2009-10-23
alternate disk worked (sort of...)

installation went smoothly, no problems

but, now it crashes upon booting, i turn computer on and it goes through the terminal declarations, then stops almost in the same manner it did when i was using the live CD

---

### Post by P4man on 2009-10-24
in grub, press E on the kernel line you use to boot, then edit the line: remove quiet and splash so the boot is more verbose. then see where exactly it freezes.

---

### Post by smoke_banshee on 2009-10-27
seems like it is a raid sata problem...

looked up some mdadm websites, any pointers towards raid sata and mdadm for someone totally n00b-ish on this subject will be met with much praise and appreciation

---

### Post by P4man on 2009-10-28
Might help if you can quote the boot message or error where it freezes.
But if its related to RAID, then go back to your bios menu and try changing settings there. Like turning off RAID mode for your sata.

---

