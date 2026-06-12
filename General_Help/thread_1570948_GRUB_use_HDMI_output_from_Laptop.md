---
title: "GRUB use HDMI output from Laptop"
date: 2010-09-08
forum: General Help
---

### Post by juanoleso on 2010-09-08
I have my laptop set to default to boot to Ubuntu 10.04, but I also like to game on Windows 7.  I have the laptop hooked up to a Sony Bravia 42" LCD by HDMI-HDMI.  GRUB doesn't output to the TV through HDMI so I have to go to the laptop and open it to watch for GRUB so I can switch it to Windows when I want to game.  Ubuntu outputs to the TV just fine and so does windows.

Is there a way to get GRUB to display out of this HDMI port?  I tried sifting through google, but I just can't come up with anything useful...

The laptop is an Alienware M11x R1.  It has an intel integrated, but I have the BIOS set to always use the discrete graphics card; an NVidia GeForce GT 335M.

```

:~$sudo lspci
01:00.0 VGA compatible controller: nVidia Corporation Device 0caf (rev a2)

```

Thank you in advance

---

### Post by dcstar on 2010-09-09
> **juanoleso said:**
> I have my laptop set to default to boot to Ubuntu 10.04, but I also like to game on Windows 7.  I have the laptop hooked up to a Sony Bravia 42" LCD by HDMI-HDMI.  GRUB doesn't output to the TV through HDMI so I have to go to the laptop and open it to watch for GRUB so I can switch it to Windows when I want to game.  Ubuntu outputs to the TV just fine and so does windows.

Is there a way to get GRUB to display out of this HDMI port?  I tried sifting through google, but I just can't come up with anything useful...

The laptop is an Alienware M11x R1.  It has an intel integrated, but I have the BIOS set to always use the discrete graphics card; an NVidia GeForce GT 335M.

```

:~$sudo lspci
01:00.0 VGA compatible controller: nVidia Corporation Device 0caf (rev a2)

```

Thank you in advance

GRUB is a simple OS loader that will only use the VESA resources provided by the video hardware, it is up to your video hardware to provide the output to whatever connectors you have.

If you get BIOS message then GRUB should appear, if no BIOS messages appear then it is doubtful GRUB will also be there.

My motherboard has onboard ATI graphics with HDMI, and my BIOS output and GRUB go to that as well as the VGA port.

---

### Post by juanoleso on 2010-09-09
ah, good to know.  The BIOS doesn't show so that answers that question.

Thank you!

---

### Post by SorryGoFish on 2010-10-01
Is there a way, in the motherboard BIOS to configure the default output device for situations like this?

---

### Post by juanoleso on 2010-10-01
My BIOS doesn't have the option to change that.

I've resigned myself to getting out of my chair when I want to switch OS's.  =-D

---

### Post by SorryGoFish on 2010-10-01
Okay. Thanks for the reply.

---

