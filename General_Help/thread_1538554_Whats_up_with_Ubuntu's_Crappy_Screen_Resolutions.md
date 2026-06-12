---
title: "Whats up with Ubuntu's Crappy Screen Resolutions?"
date: 2010-07-25
forum: General Help
---

### Post by rugbert on 2010-07-25
I have a ViewSonic VX2000 with a max resolution of 1600x1200 but the max resolution I can get with ubuntu is like 1152x864 which is kinda not cool. I just left Win7 because some nasty virus reminded me how care free linux was, but I had a kick *** high resolution.

Im about to hook this box up to a flat panel as a HTPC but if I cant get a 1900x1080 resolution Im going to have to go back to windows.

Oh yea, Im using the NVIDIA X Server Settings

Important specs are:
ZOTAC GF9300-D-E LGA 775 NVIDIA GeForce 9300 HDMI Wi-Fi Mini ITX Intel Motherboard
Intel Pentium E5200 Wolfdale 2.5GHz LGA 775 65W Dual-Core Desktop Processor BX80571E5200

---

### Post by robsoles on 2010-07-26
Please hook up to the monitor capable of 1920x1080 res and get back to us if you need help - I haven't seen 10.04 LTS fail to run a monitor capable of 1920x1080 at that res very nicely yet.

---

### Post by Bachstelze on 2010-07-26
> **rugbert said:**
> Im going to have to go back to windows.


Suit yourself. :)

---

### Post by MartyBuntu on 2010-07-26
Which NVIDIA drivers are you using?

---

### Post by rugbert on 2010-07-26
> **MartyBuntu said:**
> Which NVIDIA drivers are you using?
Current Version of hte  NVIDIA accelerated graphics drive. the Previous v was 173 i guess.

> **robsoles said:**
> Please hook up to the monitor capable of 1920x1080 res and get back to us if you need help - I haven't seen 10.04 LTS fail to run a monitor capable of 1920x1080 at that res very nicely yet.

I was looking at the xorg.conf file and saw that the monitor wasnt identified. Someone in another forum suggested that my machine cant get the EDID of the monitor but I havent found a solution yet.

---

### Post by robsoles on 2010-07-26
please specify if you are using the monitor that is capable of 1920x1080 yet or not - I expect the new monitor has better chance of being better supported than this one you can't set to it's highest res - 1600x1200.

Should be able to force it to your desired resolution, have you tried stuff like 'force resolution in xorg.conf' in Google?

---

### Post by rugbert on 2010-07-26
Yea, I solved it actually, and wrote a little guide on how to edit the xorg for unsupported monitors too:
[http://ubuntuforums.org/showthread.php?t=1539678]("http://ubuntuforums.org/showthread.php?t=1539678")

---

