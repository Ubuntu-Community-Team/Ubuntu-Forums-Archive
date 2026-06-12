---
title: "Radeon 7970 and multimonitor"
date: 2012-08-11
forum: General Help
---

### Post by erupter on 2012-08-11
Hello.
I recently installed 12.04 on my new desktop computer

I7 2600
Asrock Z77 Extreme6
Sapphire Radeon 7970

Now at first I installed the Ubuntu-provided drivers (pre-release).
I then got a second monitor

Dell U2412M (1920x1200)
Asus VW222S (1680x1050)

So tried enabling them both under Linux.
No joy: the shared desktop would trigger a "not enough memory" message.
I read up about it and decided to try the manual installation of 12.6 following the ATI drivers Wiki.

So then I got 12.6 but still if I share the desktop among the two monitors the following happens:
at the login screen the system appears working correctly showing the same background on both screens, login mask on the 1st, and the ubuntu logo on the second.
But as the password is entered, the configuration is reverted to single screen, and the second is disabled.

So I also tried the other multi-monitor option (single desktop per screen? something like that), but upon logging in the secondary monitor only shows a white background, like some default window background, and I can't move anything there, I can only right click.

I checked and the drivers are working, OpenGL is correctly recognized, and when the two monitors are enabled (with the strange white window thing on the secondary), the test shows the drivers are correctly loaded for both monitors.

What can I do?

---

### Post by raja.genupula on 2012-08-11
I think for 1st monitor you gave the maximum resolution . check out the maximum resolution and give the proper resolution .

i mean try as , after doing login with the 1st screen ,check it screen resolution and status of 2nd monitor as on or off . by limiting the resolution of the 1st monitor you can view 2nd monitor also .

---

### Post by erupter on 2012-08-11
> **raja.genupula said:**
> I think for 1st monitor you gave the maximum resolution . check out the maximum resolution and give the proper resolution .

i mean try as , after doing login with the 1st screen ,check it screen resolution and status of 2nd monitor as on or off . by limiting the resolution of the 1st monitor you can view 2nd monitor also .

You mean that I have to lower the resolution of the larger monitor to the same as the smaller one?
But that's stupid: I'm loosing resolution this way :(

---

### Post by raja.genupula on 2012-08-11
> But as the password is entered, the configuration is reverted to single screen, and the second is disabled.

you sure about that ?

---

### Post by erupter on 2012-08-11
> **raja.genupula said:**
> you sure about that ?

Positive: if I open the Catalyst CCC afterwards the secondary is disabled.

---

### Post by raja.genupula on 2012-08-11
have you tried with Catalyst 12-1 ?

---

### Post by erupter on 2012-08-11
> **raja.genupula said:**
> have you tried with Catalyst 12-1 ?

Nope, but I read that only 12.6 brought support for kernel v3.
Also I think that 12.1 may only have experimental support for HD7000 series, don't remember exactly when that was released...

---

### Post by raja.genupula on 2012-08-11
yeah but Catalyst 12.1 only going to support . 

see this for more info 

[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

---

### Post by erupter on 2012-08-12
So you say 12.1 is supported, but at [this link]("http://www.x-drivers.com/catalog/drivers/video_cards/companies/amd/models/catalyst_linux/23776.html") you can clearly read they have no support for the 7970.

I'll still try installing.


Edit: ok installed 12.1, a big green writing on the lower right corner says "AMD Unsupported Hardware", running fglrxinfo gives this
```

erupter@FCD-Ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series
OpenGL version string: 4.2.11399 Compatibility Profile Context

```So 7970 isn't supported by 12.1 as I supposed.
Why does the wiki say the contrary?

Edit 2:
ok it allows me to set the desktop on both monitors but still at the resolution of the smaller one.
No way I can run the bigger at its native resolution.
And this way my main screen looks way blurred... (well it is way blurred!)

---

### Post by erupter on 2012-08-14
I reverted to the Catalyst 12.6, if I set the two screens to the same resolution, spanning the desktop works.
But then after a restart, the bigger monitor gets reset to the "preferred resolution" which triggers the "not enough memory" problem thus disabling the second monitor.

It seems that upon loading XORG sets a certain resolution by default and changes aren't retained.

---

### Post by erupter on 2012-08-16
Thanks to a suggestion I tried the Xinerama option: it works, meaning the bigger screen maintains its own native resolution, but the transparency effect (and possibly others) get glitchy as the launcher background isn't transparent anymore (just black) and the status bar text has greenish hues around text.

---

### Post by erupter on 2012-08-16
> **erupter said:**
> Thanks to a suggestion I tried the Xinerama option: it works, meaning the bigger screen maintains its own native resolution, but the transparency effect (and possibly others) get glitchy as the launcher background isn't transparent anymore (just black) and the status bar text has greenish hues around text.

Not only that: running Xinerama (Catalyst 12.6) effectively disables 3D acceleration thus leading to many ugly graphic disfunctions.



Really: am I the only one with a 7970, 2 monitors AND Ubuntu ???
Almost no answer in days...

---

### Post by erupter on 2012-09-05
Further experiments:
previously the situation was old vga monitor connected with dvi-vga converter, new dell connected with hdmi-dvi converter.

Now the old monitor is connected just the same, while the new is displayport (no converters).
This way the dual desktop with native resolution finally works!
Moreover the dell monitor is finally displaying better colors then the VGA one.
So I guess HDMI is just not meant for real work, rather to beam a movie to a television... but not much more.

---

### Post by SJR Dorset on 2012-09-05
I have two monitors connected to my HD5570, one by HDMI and the other by VGA. My main monitor is connected by HDMI running at resolution of 1900 x 1200 without problem.

When I set up both monitors I disabled the second monitor on the login screen and set the main monitor to maximum resolution. The second monitor is then enabled after login at a different resolution with the desktop spanning both monitors.

---

### Post by erupter on 2012-09-05
> **SJR Dorset said:**
> I have two monitors connected to my HD5570, one by HDMI and the other by VGA. My main monitor is connected by HDMI running at resolution of 1900 x 1200 without problem.

When I set up both monitors I disabled the second monitor on the login screen and set the main monitor to maximum resolution. The second monitor is then enabled after login at a different resolution with the desktop spanning both monitors.

Yeah, really, as if I didn't know ;)
I tried doing the same but it did not work until I changed cables today.
That has probably to do with the segmentation of the frame buffers: DVI and DP are probably on the same segment, HDMI is on another.
For the 7970.
Your card may very well be different.

---

