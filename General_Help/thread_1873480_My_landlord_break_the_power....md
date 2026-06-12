---
title: "My landlord break the power..."
date: 2011-11-01
forum: General Help
---

### Post by Azyx on 2011-11-01
....Twice with a few seconds between, so first shut the computer down (i have auto-start after powerfailur) started and then during boot, he break the power again.

Now the disk will not boot, but I can boot with an Ubuntu CD (8.04)  there I choose to boot from first harddisk. When I try to boot the BIOS is wainging after:
"Verifying DRI data pool........."

Any idea how I can fix it? Using 10.04LTS, but don't have any CD and USB-boot don't work on the old motherboard (USB-hdd are not an option in BIOS). I have a swap-space, / and /home on the hdd.

/Cheers

---

### Post by WasMeHere on 2011-11-01
Tough luck Azyx,

but I think there are several people at the Ubuntu Forums, that are willing to help :-)

First of all, don't panic! Collect information and do things that are safe (***only*** necessary writing to the hard drive, that is not writing at all before you are pretty sure).

It is probably enough to boot from the hardy live CD. For example, it has gparted. You might alsp be able to boot from a USB drive letting the system think it is an internal hard drive (just reset the boot order in your bios). Do you have a spare hard drive to backup your system or at least your private files?

Good luck
Olle

---

### Post by oldos2er on 2011-11-01
Please watch your language, Azyx.

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> Tough luck Azyx,

but I think there are several people at the Ubuntu Forums, that are willing to help :-)

First of all, don't panic! Collect information and do things that are safe (***only*** necessary writing to the hard drive, that is not writing at all before you are pretty sure).

It is probably enough to boot from the hardy live CD. For example, it has gparted. You might alsp be able to boot from a USB drive letting the system think it is an internal hard drive (just reset the boot order in your bios). Do you have a spare hard drive to backup your system or at least your private files?

Good luck
Olle

I made a.

```
sudo touch /forcefsck
```

and reboot, so I think the filysystem are ok now. so there are no panic :)  The problems are that it is a SATA-disk and I have had problem to boot on it before.  I have also checked that the / have boot-flagg, so it can be a BIOS problem, and maybe need to reset BIOS?  (But BIOS find the disks) So If I try to boot hdd from BIOS, the "veryfying DRI pool data...." appearse and the boot stopps. But the system seems to work when it run :)

---

### Post by Azyx on 2011-11-01
> **oldos2er said:**
> Please watch your language, Azyx.

Yes i will, but I get really angry! When he shut off the power twice, just for 'checking' he said. The also could have warned us before he break the power.

---

### Post by WasMeHere on 2011-11-01
I don't understand what you mean by > So If I try to boot hdd from BIOS, the "veryfying DRI pool data...." appears and the boot stops
How is the system behaving when you boot from the CD? The BIOS is always run before booting the operating system. Do you mean booting from grub? Do you ever reach the grub menu?

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> I don't understand what you mean by 
How is the system behaving when you boot from the CD? The BIOS is always run before booting the operating system. Do you mean booting from grub? Do you ever reach the grub menu?

If I select in BIOS to boot on harddrive, it's just waiting under "verifying DRI pool data....."
But if iput in a CD and boot from the  8.04 CD, I came to  the prompt there you can choose. 
*Boot LiveDC
*Install
*Check CD
*Check memory
*Boot from first harddrive

And the select "Boot from first harddrive" the system on the harddisk starts and work perfect. So it's not any hurry in the problem. It's just that BIOS are not able to boot hdd directly, but the bootloader on the Ubuntu-CD are able to boot the system on the hdd.

/cheers

---

### Post by kurt18947 on 2011-11-01
> **Olle Wiklund said:**
> I don't understand what you mean by 
How is the system behaving when you boot from the CD? The BIOS is always run before booting the operating system. Do you mean booting from grub? Do you ever reach the grub menu?

This is probably not your problem but if I have a non-bootable device plugged into a USB port, I get that message and the boot process halts.  I have to remove or turn off the device then do ctrl-alt-del. By non-bootable I'm referring to something like an external H.D. or USB flash drive with no O.S. on it.  I would think if it were a GRUB problem or something like that the boot process would get a little further then you'd get a "Operating system not found" or "Boot error" or something along those lines.  If it were me I might restore the BIOS to default settings and see if that helped.

---

### Post by Azyx on 2011-11-01
> **kurt18947 said:**
> This is probably not your problem but if I have a non-bootable device plugged into a USB port, I get that message and the boot process halts.  I have to remove or turn off the device then do ctrl-alt-del. By non-bootable I'm referring to something like an external H.D. or USB flash drive with no O.S. on it.  I would think if it were a GRUB problem or something like that the boot process would get a little further then you'd get a "Operating system not found" or "Boot error" or something along those lines.  If it were me I might restore the BIOS to default settings and see if that helped.

Could it be any problem in MBR, that the BIOS don't can solve, but the UbunutuCD? I rembember from windows that you could fix MBR?

---

### Post by WasMeHere on 2011-11-01
I see. If Kurt's recipe works all is fine. Otherwise we have to come up with something new. Can it be 'DMI Pool Data' that is written to the screen? Search for it on the internet!

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> I see. If Kurt's recipe works all is fine. Otherwise we have to come up with something new. Can it be 'DMI Pool Data' that is written to the screen? Search for it on the internet!

Yes Kurt tips are great :), but just now I use the computer so I can not test it. "veriifying dri pool data", probably appears when the BIOS not can boot. Will try a CMOS-reset later.

/Cheers

---

### Post by WasMeHere on 2011-11-01
> **Azyx said:**
> Yes Kurt tips are great :), but just now I use the computer so I can not test it. "veriifying d[COLOR="Red"]r[/COLOR]i pool data", probably appears when the BIOS not can boot. Will try a CMOS-reset later.

/Cheers
Is it D[COLOR="Red"]M[/COLOR]I data? I think you find info about that on the internet.

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> Is it D[COLOR=Red]M[/COLOR]I data? I think you find info about that on the internet.

yes. look here:
[http://www.computerhope.com/issues/ch000474.htm](http://www.computerhope.com/issues/ch000474.htm)

yes i wrote dri, but mean dmi, what ever it means. sorry.

I mean DMI not DRI, and now do I know that it means DesktopManagement Interface, so there not gonna be anymore errors..I think. :) /Cheers

---

### Post by WasMeHere on 2011-11-01
You found a valuable link :-)

---

### Post by Azyx on 2011-11-01
Thanx kurt and Olle. Reset CMOS fixed it. :)

---

