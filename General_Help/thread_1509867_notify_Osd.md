---
title: "notify Osd"
date: 2010-06-14
forum: General Help
---

### Post by flyingsliverfin on 2010-06-14
my notifyOSD for some reason has abnormally small text, im not sure when this started or why.

i installed NotifyOSDconfiguration, and set the text side to 100%, yet its still tiny

---

### Post by stinkeye on 2010-06-14
The size of the font is determined by the setting in system > preferences > appearance > fonts > Application font.

If you want your application font to remain the same size but notification messages to be larger
you can go over 100% in your config.
Just open the **.notify-osd** in your home folder.
ctrl+h to show hidden.


Eg my .notify-osd file
```
slot-allocation = dynamic
bubble-expire-timeout = 10sec
bubble-vertical-gap = 30px
bubble-horizontal-gap = 10px
bubble-corner-radius = 50,5%
bubble-icon-size = 52px
bubble-gauge-size = 10px
bubble-width = 250px
bubble-background-color = 0F0742
bubble-background-opacity = 85%
text-margin-size = 10px
[COLOR="Purple"]text-title-size = 130%[/COLOR]
text-title-weight = bold
text-title-color = DF7D08
text-title-opacity = 100%
[COLOR="#800080"]text-body-size = 110%[/COLOR]
text-body-weight = normal
text-body-color = FFC100
text-body-opacity = 100%
text-shadow-opacity = 100%
```


After saving the file run```
pkill notify-osd
```



To test run```
notify-send "Test" "This is a test"
```
You may have to install the **libnotify1** package for notify-send to work.

---

### Post by flyingsliverfin on 2010-06-15
Thanks

---

