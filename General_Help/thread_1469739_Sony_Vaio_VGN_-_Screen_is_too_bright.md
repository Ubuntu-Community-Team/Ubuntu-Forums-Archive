---
title: "Sony Vaio VGN - Screen is too bright"
date: 2010-05-02
forum: General Help
---

### Post by WinterAce on 2010-05-02
Hi,

I have a Sony Vaio VGN-FZ340E. I installed Ubuntu about 6 months ago and had a problem-free time with it. I then got busy with other stuff (house work, etc.) and hadn't worked on Ubuntu for about a month. Now I switch on my Vaio with Ubuntu and I find the screen is just too bright.

Since 10.04 was just coming up, I thought this would be fixed when I update. I updated, but the screen is still too bright.

I searched the forum for answers and found only some pretty old threads which were about the Fn key combos (which, obviously, doesn't work), spicctrl, etc.

So I followed the instructions [here]("https://help.ubuntu.com/community/SonyVaioBrightness"). I did just what *Step 1: Checking for Module* says, but Terminal just doesn't give any output. I tried *Step 2* but it says bash: /etc/modules: Permission denied.

I then installed Spicctrl and ran it. Okay. But when I run the command:
```
sudo spicctrl -B
```But I get - /dev/sonypi: No such file or directory.

I then tried the section *If Spicctrl Doesn't Work*, and ran the command
```
sudo echo 4 > /proc/acpi/sony/brightness
```But, again, I get - No such file or directory.

Any idea what I should do? :( Your help is appreciated.

---

### Post by 00arthuryu on 2010-05-03
What GPU have you got? I have a VGN-CR42 and brightness works out the box (minus the keys). Generally its the lack of display drivers

---

