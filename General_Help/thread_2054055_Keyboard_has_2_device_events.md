---
title: "Keyboard has 2 device events"
date: 2012-09-06
forum: General Help
---

### Post by sienile on 2012-09-06
This is a clone of another thread which I was not able to change the title to. Mods, please delete the old thread as this one has more info.

I've been trying to get Keytouch working so I can use my extra buttons on my MS Digital Media Pro keyboard. I can't seem to get it to work.

After I select the keyboard from the list and configure it, pressing the buttons that didn't work before still does nothing. Interestingly, the Keytouch-editor shows 2 of my keyboard, but only one (2nd listed) responds when I hit those non-working keys. I'm thinking this may be the root of my problem.

Anyone know how I can either get Keytouch to work with the right keyboard entry, or how I can remove the other?

Basically, Ubuntu is recognizing the keyboard twice and logging 2 device events. Keytouch uses the 2nd event, but the default is the 1st. How can I get Ubuntu to have only 1 keyboard event?

---

### Post by sienile on 2012-09-09
Anyone else have issues with Keytouch? I've heard lots of great stuff about it, but I can't get it to work with my keyboard even though it's one of the supported models. Is there another program to get multimedia keys to work?

---

### Post by sienile on 2012-09-11
After much searching and zero forum replies, I managed to find  [this page]("http://ubuntuforums.org/showpost.php?p=11336640&postcount=178"). It showed me how to do the mappings manually.

For anyone else with the Microsoft Digital Media Pro keyboard, here is the info you need:

in **/lib/udev/rules.d/95-keymap.rules** find the section titled **LABEL="keyboard_usbcheck"** and paste the line
```
ATTRS{idProduct}=="00b0", ATTRS{manufacturer}=="Microsoft", RUN+="keymap $name microsoft-digitalmediapro-keyboard"
```
before **GOTO="keyboard_end"**

then create the file **/lib/udev/keymaps/microsoft-digitalmediapro-keyboard** with the contents ```
0xC022D 0xE1 # Zoom +
0xC022E 0xE7 # Zoom -
0xC01B7 0xE8 # Music
0xC019C 0xE9 # LogOut
0xC01B6 0xEA # Pictures
```

You keys will work on your next reboot. (Although the system will recognize them as different keys and need to be bound in the keyboard shortcuts under System Settings.)

---

