---
title: "Unexpected desktop color management"
date: 2012-08-07
forum: General Help
---

### Post by Rallg on 2012-08-07
I understand color management reasonably well for a non-professional. I use it both on Windows XP and Ubuntu 12.10 (current development) with GIMP and other graphics programs. That's not the problem. I wish to discuss desktop color, not within a graphics application.

On Windows XP the appearance of my desktop does not change, whether or not I apply the *.icc color profile that pertains to my laptop monitor. This is what I would expect.

My understanding is that the system monitor profile, which is what I set via Windows (rather than within a graphics application) is solely for the purpose of informing other computers about my own desktop, if I transfer the file. That is, if I embed the profile in an image, it tells other others that "when I made this image I was looking at thus-and-such color space on my own computer, and here are its parameters."

I do not expect the system monitor profile to change the appearance of my own desktop. But in Ubuntu 12.10, that is what it does.

With system options, color, if I choose the correct *.icc for my monitor, then the desktop color becomes incorrect. That is, the profile is applied to color rendition on my own monitor. In order to see correct color, I must turn off Ubuntu's system color profile.

I am reasonably sure that this is not due to an incorrect *.icc file. What Windows does, is different from what Ubuntu does, in terms of desktop color management. I believe Windows is correct.

Before posting this, I searched and discovered that Ubuntu had no desktop color management until relatively recently. Could it be that the concept of desktop color management is in error? It may well be that so few people use it, nobody noticed.

Or, my own concept could be wrong.

---

### Post by CatKiller on 2012-08-07
> **Rallg said:**
> 
Or, my own concept could be wrong.

Seems like it. There's no reason why you should assume that an uncalibrated monitor is outputting accurate colour. That calibration is the monitor colour profile, which may be provided by the manufacturer or be self-generated.

Embedding a colour profile is to do the inverse of this; to translate between the display on your monitor and some other device. They are complementary, not identical, concepts.

---

### Post by Rallg on 2012-08-08
Calibration would not be the problem. Although my specific laptop was not calibrated, I have two calibrated *.icc files from others with the same model and production time; those two profiles are approximately the same. Besides, I do not need really accurate color.

On the SAME laptop, same hardware, there is a difference between what Windows does, and what Ubuntu does. Windows: monitor looks the same whether or not I enable the *.icc (so it doesn't matter whether the calibration is correct or not). Ubuntu: monitor looks as expected if system color management is not enabled, looks wrong if I enable the *.icc. In order to get Ubuntu to show what I expect as correct color on the monitor, I must use sRGB profile.

I have been using Gimp with color management (internal to Gimp) for softproofing, and the results are identical, Windows and Ubuntu. But that is with system color management turned off (or set to sRGB) in Ubuntu.

---

### Post by Rallg on 2012-08-08
Since forum threads last a long time, and can be found by search engine from outside, I thought it would be useful to update this post.

My question pertained to a laptop that came with Windows XP. I now have Windows/Ubuntu12.10 dual boot. Most of the time, I do color management from within an application, without reference to the system monitor color setting (because the application over-rides the system setting).

It turned out that the computer manufacturer provided additional software for color correction of the monitor. This was in addition to the hardware lookup table (LUT) and the Windows color management scheme. I had not noticed it before; it was one of those services that loaded at startup without me giving it any thought.

Of course, that manufacturer's program does not load in Ubuntu, because it is not part of the Ubuntu system.

One the Windows side, using a system color *.icc profile did not take effect. That is, Windows would allow me to choose the correct profile and load it. But that was an illusion. The other software would force system profile to the manufacturer's standard, no matter what Windows said was the *.icc. It was still possible to do manual adjustments (such as color balance and gamma) using sliders, via other software. But any attempt to load an *.icc file would simply be ignored. However, a monitor *.icc could be loaded within an application, which is why I hadn't noticed this before.

Perhaps there is a way to disable the extra color management on the Windows side, but it is unimportant as long as I am working within an application that reads color profiles (such as Gimp or Acrobat, or recent versions of Firefox). If an image is opened in an application that does not recognize color profiles, then it will look different on the two systems, unless I choose sRGB rather than the measured profile.

EDIT: The solution was the free dispcalGUI profile loader. After using Windows to set the required profile (which was set but not loaded), the dispcalGUI profile loader defeated the extra color management and loaded the profile. Now my Windows and Ubuntu desktops have the same color management.

---

### Post by sg4032 on 2012-09-28
> **Rallg said:**
> I do not expect the system monitor profile to change the appearance of my own desktop. But in Ubuntu 12.10, that is what it does.

What the color profile does, when loaded in "System settings > Color" in Ubuntu, is applying the gamma curve. This affects gamma, contrast and brightness (all color-independant).
(Edit: For each curve in RGB. So colors might change, but not the relation of colors to each other. You can compare it to setting a white balance, brightness and contrast in a photo editing program.)
The corrections of color values (hue, saturation and luminance) for each color are not corrected through the system settings. You need to load the profile a second time inside each program where you need correct colors (i.e. Gimp or Firefox).
In Gimp it's done in the Color Management settings, in Firefox in the about:config settings. Easiest way for Firefox is to install the "Color Management" extension. Make sure to give the exact path to the profile, automatic recognition of the loaded profile in Ubuntu system settings didn't work for me. Also activate in the extension settings the option to apply the profile "for all images".

---

