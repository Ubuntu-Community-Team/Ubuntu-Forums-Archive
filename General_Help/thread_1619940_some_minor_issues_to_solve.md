---
title: "some minor issues to solve"
date: 2010-11-12
forum: General Help
---

### Post by System_selector on 2010-11-12
Hello everybody!

Although Win7 is not bad either, I'm really happy using new Ubuntu Maverick Meerkat on my notebook. Since I've been using Linux (SimplyMepis, then Arch) on my desktop, I'm really happy that I found a Linux distro which suits me the best. BTW, I have a Toshiba T130-10g which I love for its long battery life.

However, I would like to solve some issues/dilemmas/questions (and I searched for s the solutions of some of them on Google so please don't tell me to use it...)

1) How do I turn off Wifi completely in a comfortable way? I tried sudo iwconfig wlan0 txpower off but it threw:

Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.

I even edited something in interfaces configuration file, but it did nothing. Oh, I forgot, my notebook doesn't have a hardware switch to turn off wifi.

2) Setting brightness doesnt work for my laptop. I can set it by udo setpci -s 00:02.0 F4.B=25 but I'm looking for a more comfortable solution. BTW, editing one GRUB configuration file didn't help and ended in booting into command line (it was something with adding backlight=vendor or something like that...)

3) My touchpad is sometimes too sensitive and clicks somewhere sometimes when I don't want to it. How to make clicks less sensitive? I tried to play with some mouse settings but it didn't help much but perhaps I'm setting a bad parameter.

4) I remember that back in KDE 3.5 times a network manager icon had a setting to switch on net statistics so I could very easily see how much I downloaded every day. But, since KDE 3.5 is not supported anymore, I stopped using it in refusal to update to KDE 4.XX and switched to GNOME. Since for some months I'll have a limited download connection, is there something esay in GNOME to watch my net statistics that wouldn't be deleted after reboot/shutdown?

5) Is XFS as FS best for my multimedia partition? I have there MP3s, videos, ISO files and some backuped Documents. Would change to ext4 partition would have any visible effects (like loading my MP3 playlists in Juk faster?)

6) Since not all my FN keys work, I'd like to associate for example hibernate function with some key combination. How?

7) How do I turn off Bluetooth automatically after startup?

8. Does open intel driver have 3D acceleration?

9) Why sometimes I cannot reboot or shutdown from menu? Sometimes I have to do it by sudo shutdown -h now or sudo reboot. Anybody any idea why is it like it?

Thank you for any help, comments. Thanx :)

---

### Post by papibe on 2010-11-12
> **System_selector said:**
> 
7) How do I turn off Bluetooth automatically after startup?


System -> Preferences -> Startup Applications

uncheck the Bluetooth Manager. This way it won't even run when you get into the desktop.

Regards.

---

