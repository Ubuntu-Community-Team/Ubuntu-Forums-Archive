---
title: "Ubuntu desktop froze after Nvidia driver installation"
date: 2012-04-17
forum: General Help
---

### Post by reborn_zwan on 2012-04-17
Hi everybody,im a newbie to Ubuntu. I'm using Ubuntu 11.04, everything  was working until i started my computer today. The screen was flickering  heavily, it was as if it is refreshing and everything momentarily  disappeared twice every second. I had changed my screen resolution earlier before shutting it down.

using ctrl+alt+F1 i tried to install the latest Nvidia drivers using:
         sudo apt-get install nvidia-current

I restarted my computer, now the desktop is properly shown and I can move my mouse but i can't click on anything! it's as if it is frozen. Using an online guide I tried to remove the xorg.conf:

        sudo rm /etc/X11/xorg.conf 
and then 
        sudo nvidia-xconfig
and  gksu nvidia-settings 
But the last two give me an error:  GTK Warning: Can not open display....

Now i have no idea what is causing this huge headache and what should i do?

Thanks for the replies

---

