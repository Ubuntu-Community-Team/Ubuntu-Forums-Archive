---
title: "Wesnoth Removal"
date: 2010-02-08
forum: General Help
---

### Post by rocket16 on 2010-02-08
Hello all. I had downloaded Wesnoth 1.7.5 previously. I also had the 1.6.1 deb package. Now, I recently upgraded from 9.04 to 9.10 (Ubuntu) and am trying to install Wesnoth 1.7.5. Everytime earlier, in several Computers running Wesnoth 9.04, (and Wesnoth 1.6.1 deb loaded) Wesnoth 1.7.5 binary got installed correctly, using the commands:
./autogen.sh
./configure
make
make install

But now, in 9.10, I tried to install Wesnoth 1.7.5 directly (without Wesnoth 1.6.1 installed) from the binary, and (all dependencies got satisfied) it got installed too. But, no sound is there, and additionally, it crashes when I tend to close it. So, I want to uninstall Wesnoth 1.7.5 and reinstall it (first adding 1.6.1 deb). But Software Centre, I saw that it is showing that Wesnoth is not installed. I think it is due to the installation from the Binary. S, how may I remove Wesnoth 1.7.5? (And, I don't want to download the 1.6.4 version again, because although is is stable, still it is large).

---

### Post by rocket16 on 2010-02-08
Ah, thanks to Almighty Lord Shiva (the principal God of Hinduism), Linux and Ubuntu developers and to last but not the least, you all, I mean Ubuntu forums members. I found the solution, and thought that I should share it. The problem was regarding "Preferences" file in my /home/user/.wesnoth1.7 directory. The file was somehow corrupt, and I reconstructed it as follows:
UI_sound="yes"
auto_save_max="10"
chat_lines="6"
clock_format="%H:%M"
colour_cursors="no"
encountered_terrain_list="Ce, Ch, Chr, Dd^Dc, Dd^Dr, Dd^Ft, Dd^Vda, Dd^Vdt, Dd, Ds^Ft, Ds, Gg^Vc, Gg^Vh, Ggf, Gs, Gt, Hd, Hh, Ke, Rd^Dr, Rd, Wo, Ww^Bw|, Ww^Dr, Ww, Wwf, ^Fp"
encountered_units="Dark Adept,Ghoul,Kaleh,Nym Hunter,Skeleton,Skeleton Archer,Vampire Bat"
fullscreen="yes"
grid="no"
idle_anim_rate="0"
music_volume="100"
scroll="50"
scroll_threshold="10"
scroll_to_action="yes"
show_haloes="yes"
sound="yes"
sound_volume="89"
turbo="no"
turbo_speed="2"
upload_id="33262086189201"
upload_log_new="yes"
xresolution="1280"
xwindowsize="1280"
yresolution="800"
ywindowsize="723"
[history]
[/history]

And now all is quite well! Hurray for Karmic Koala Uuntu 9.10, and after installing it, I realize why it is even better than Ubuntu 9.04.

---

