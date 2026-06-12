---
title: "Can't Get Document Font Tab to Work Properly"
date: 2011-10-27
forum: General Help
---

### Post by w201 on 2011-10-27
I was playing around with different themes and one called for the use of ***msttcorefonts, ***which I downloaded and installed. I  decided to switch everything back but the problem now is that  the ***document font*** ***tab*** on appearance preferences has no effect when I select different font types.

Now Firefox is stuck with some weird font that I can barely read. I'm talking about the content font here. I know that different websites use different fonts, but if there is no specified font I think it falls back on the system font? All the other tabs appear to work.

If it helps anyone, these are the commands that I ran that got me in this annoying mess:

```
This will Install the Microsoft core fonts:
sudo apt-get install msttcorefonts


Next, copy the OSX fonts to the fonts folder:
cd /usr/share/fonts
 sudo tar xvzf /home/username/Mac_files/Mac4Lin_v0.4/Fonts/OSX_Fonts.tar.gz


Configure the fonts:
cd/
 sudo tar xvjpf /home/username/Mac_files/Mac4Lin_v0.4/Fonts/fontconfig.tbz -C /etc/fonts

```Thanks in Advance!

---

