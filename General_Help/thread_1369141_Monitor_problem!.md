---
title: "Monitor problem!"
date: 2009-12-31
forum: General Help
---

### Post by dudeeh on 2009-12-31
I'm using ubuntu 9.04 with nvidia driver 180.44. I have two screens:
- LG: HDMI (but with overscan) and VGA
- Packard bell (PB): VGA, DVI, HDMI

My nvidia card (8600 GTS) has two outputs:
- HDMI
- DVI (with a DVI-VGA converter for the LG)

HDMI on the LG is tricky because of the overscan, plus if I enable a high resolution, it...vibrates... for lack of a better word, the contents on the screen are fuzzy due to what seems to be a vibrating motion. So I use VGA on the LG.

If i plug in HDMI on the PB, the "nvidia-settings" manager will pick up the PB and its model name, so it clearly detects the screen, but when I enable twinview, nothing happens. The screen is not active.

Here is where it get's freaky:
- if i plug in both DVI & HDMI in the PB, both work fine! (HDMI at high resolution is ok, no fuzziness or nothing!)
- if i plug in VGA & HDMI in the LG, vga works, HDMI is overscanned and at high resolution fuzzy

Now in the second case, if i transfer the HDMI connection from the LG to the PB...the PB works! The nvidia manager still shows the old screen (by model name i mean), but then i have a working setup for HDMI & VGA, however, a few things:

- in high resolution... the PB gets fuzzy! (this means the fuzziness is not screen-related?)
- once nvidia manager catches on that its the PB and not the LG, it stops working

This leaves me with two questions:
- Why is the fuzziness apparantly related to the type of monitor nvidia thinks it is, rather then to the actual monitor?
- Why does HDMI stop working for my PB if nvidia recognizes it as such, but does it play happily along as long as nvidia thinks its the LG?

---

### Post by gsmanners on 2009-12-31
I think TwinView tries to force both monitors to a similar resolution or frequency. Maybe it would be better if you used "Separate X screen" Configurations for them.

---

### Post by dudeeh on 2010-01-02
I have updated to ubuntu 9.10, so i have the "185.18.36" driver now, I tried separate X, twinview, what have you, but it simply won't work.

Mind you that the screen does show up in the nvidia-settings dialogue and that the 9.04 livecd sets up a cloned environment out of the box with no problems at all.

---

### Post by gsmanners on 2010-01-02
It's too bad you didn't get a VGA/DVI card. Those HDMI cards are unfamiliar to me. I think what may be happening is that the driver assumes HDMI is going to a TV rather than a monitor and puts it at 60Hz (which the PB will not sync down to). This kind of thing requires some options in the config file which I don't think you can get in nvidia-settings.

It's rather odd that nvidia-settings can't just detect the PB automatically with the HDMI. Maybe it's a bug in the 18x series driver, but I have no way to test it from here.

---

