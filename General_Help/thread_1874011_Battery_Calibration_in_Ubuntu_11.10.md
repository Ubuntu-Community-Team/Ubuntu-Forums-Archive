---
title: "Battery Calibration in Ubuntu 11.10"
date: 2011-11-02
forum: General Help
---

### Post by djpemberton on 2011-11-02
I have a new Asus U46e laptop with Windows 7 and Ubuntu 11.10. I am trying to "calibrate" the battery, as I feel I get poorer battery life than I should. However, there is no option in the power settings to allow "do nothing" when the battery is critically low.

Is there any way around this?

It sure seems that Ubuntu's newest releases restrict my choices quite a bit.

---

### Post by javince80 on 2011-11-02
I have the same problem  with a lenovo. It's so annoying that i can't change any option about the battery like i could with lenovo power manager...

---

### Post by nerver on 2012-01-10
Hopefully this isn't too late to help. You can set the power options to do what you want with dconf-editor.

To install:

```
sudo apt-get install dconf-tools
```

then launch the dconf-editor and go to:

org > gnome > settings-daemon > plugins > power

and change critical-battery-action to "nothing" without the quotes.

Cheers,
-Sean

---

### Post by weblearner115 on 2012-01-16
Great answer!  I was having the same problem.  Thanks!

---

### Post by WaNaBePi on 2012-02-16
This seems to be a good fix. What else can this program do? 3 interesting examples?

---

### Post by friTTe81 on 2012-05-31
Solved it for me aswell..thanks

---

