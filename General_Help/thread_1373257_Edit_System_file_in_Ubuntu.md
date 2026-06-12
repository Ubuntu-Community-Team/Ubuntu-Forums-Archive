---
title: "Edit System file in Ubuntu"
date: 2010-01-05
forum: General Help
---

### Post by dogturd on 2010-01-05
Hi,

I am running 9.10 64bit a MBP 15 5,3 model.

I have installed nautilus so that I can open files as admin.

I need to edit /sys/devices/platform/applesmc.768/light and add the following text. (This will enable my backlight on the keyboard on my Macbook Pro).

 echo 255 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness

It won't let me save the file after adding the text - so now I am really stuck as I am unable to edit a system file and make any changes! What do I need to do to make this work so I can edit the file and save it?

Thanks

---

### Post by howefield on 2010-01-05
Try opening a terminal (Applications > Accessories > Terminal) and type

```
sudo gedit sys/devices/platform/applesmc.768/light
```

Enter your password if prompted, and you should then be able to append the line to the file and save.

---

### Post by sisco311 on 2010-01-05
Install [nautilus-gksu]("apt://nautilus-gksu") (apturl link, click it to install the application), log out and log back in.

Right click on the file and select *Open as administrator*.

---

### Post by sisco311 on 2010-01-05
> **howefield said:**
> Try opening a terminal (Applications > Accessories > Terminal) and type

```
sudo gedit sys/devices/platform/applesmc.768/light
```

Enter your password if prompted, and you should then be able to append the line to the file and save.

One should use gksu for GUI application. 

```
gksu gedit /sys/devices/platform/applesmc.768/light
```

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by howefield on 2010-01-05
> **sisco311 said:**
> One should use gksu for GUI application.

Yep, my mistake, I do know that.

Thanks for the correction.

---

### Post by dogturd on 2010-01-09
Many thanks for all your help and advice everyone - problem fixed.

---

