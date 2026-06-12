---
title: "Brightness control on Toshiba Satellite C660 laptop"
date: 2012-10-05
forum: General Help
---

### Post by snake_eyes on 2012-10-05
Hello,

Backlight control does not work on Toshiba Satellite C660 with Ubuntu 10.04 64 bits. Hot keys Fn 6 and Fn 7 are active but have no effect on the brightness of the LCD

I saw many threads in ubuntufourms and others but nothing worked.

Please note that I added the line Option "RegistryDwords" "EnableBrightnessControl=1" to the /etc/X11/xorg.conf but it wont work, unlike before I format my PC, there was 2 OS windows and ubuntu, now I formatted and left the Ubuntu only.

Any cooperation would be appreciated.

Best regards

---

### Post by Tamlynmac on 2012-10-05
Just a quick thought.

If you have nvidia video. Did you install the nvidia driver prior to changing your xorg.conf? See this [fix]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/939569"), make sure you look at the last two posts. You may also have an nvidia hardware driver available in your "system/administration/hardware drivers" that isn't turned on.

Good Luck & hope this helps.

---

### Post by snake_eyes on 2012-10-06
As I said the command of the Option "RegistryDwords" "EnableBrightnessControl=1" was working as well when I had 2 OS but not there is only ubuntu and even that is not working.

Please note that I installed my driver via shell by applying the following command:

> sudo apt-get install nvidia-glx

> sudo lsmod | grep -i nvidia
nvidia              10833082  43

Although the following command is not helpful because it effect the RGB colour, in other word if I go to youtube it appear the video in blank.

> xgamma -gamma 1

Any other assistance would be appreciated.

---

### Post by snake_eyes on 2012-10-12
any updates please :(

---

