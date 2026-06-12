---
title: "Having some problems with HP Touchsmart tm2"
date: 2010-12-17
forum: General Help
---

### Post by someh4x0r on 2010-12-17
I installed Ubuntu 10.10 on my laptop and encountered several issues. 

1. The Synaptics touchpad is nearly unusable. It is impossible to drag while holding down a button. The cursor will move randomly across the screen instead. It is impossible to right click; a right click is treated like a left click. Double-tapping the dot in the corner does not disable the touchpad. 

2. Attempting to change the brightness will kill the screen. The computer is still functioning, and it is possible to perform tasks "blind." Only the screen becomes completely blank.

3. Ubuntu does not always boot up reliably. When it does not, the screen is blank but the computer is otherwise responding.

4. The screen is black after suspend.

5. The computer will sometimes hang when shutting down (showing desktop background).

Possibly related messages in dmesg:

```

[    1.340483] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    1.357191] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    8.365185] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled

```Can anybody help?



EDIT: I fixed problems 2 and 4 and possibly fixed 3. To fix, extract the DSDT and change the OBCL method to (remove the if/else):
```

                    Method (OBCL, 0, NotSerialized)
                    {
                        BINI ()
                        Return (Package (0x0D)
                        {
                            0x64, 
                            0x3C, 
                            0x06, 
                            0x0A, 
                            0x14, 
                            0x1E, 
                            0x28, 
                            0x32, 
                            0x3C, 
                            0x46, 
                            0x50, 
                            0x5A, 
                            0x64
                        })
                    }

```I half-fixed the touchpad problem with the proto=exps fix, but that disables scrolling. Is there a better fix? Also, is there a way to inject a DSDT without compiling the kernel?

---

### Post by jannoke on 2011-02-11
I have the same problems. My screen brighness changing seems to work better - it seems that then it has not been used then dimming down gives immediate dark..but then it can be dimmed back to bright normally again.

Did you get the ATI driver working? Seems like if it's not installed, then battery is drastically drained. But if install ati driver then it will boot up blank. All keys seem to work (pressing power button will shutdown the computer and control-alt-delete gives reboot). I have only tryd it with drivers that ubuntu offers. 

If you set acpi=off then it won't show the X , but it WILL show screen and console can be used to fix things up again.

---

### Post by someh4x0r on 2011-02-11
I don't use the ati driver at all. I power off the card using the VGA_switcheroo interface. I actually have the computer working fine (except clickpad) by patching the brightness table in the bios using ezh20.

---

### Post by jannoke on 2011-02-14
yup. Got the vga_switcheroo working also now.

I'm useing it dualboot and seems like if linux messes around with bluetooth then sometimes i could end up with no bluetooth connection in windows. Everything seems to work, except that seems like bluetooth antenna is turned off. 

Reinstall of bluetooth drivers in windows seems to fix the problem.

---

### Post by dess on 2012-04-01
There is a way to patch DSDT without modifying BIOS.

In short, get DSDT dump from */sys/firmware/acpi/tables/DSDT*, disassemble with *iasl*, fix as proposed by **someh4x0r**, assemble with *iasl*, place it to */boot/* directory, add *acpi /boot/dsdt.aml* to grub2 config.

Full HowTo placed here:
[https://wiki.ubuntu.com/HP%20TouchSmart%20tm2#Screen_Brightness](https://wiki.ubuntu.com/HP%20TouchSmart%20tm2#Screen_Brightness)

Big thanx to **someh4x0r** for debugging the problem.

---

