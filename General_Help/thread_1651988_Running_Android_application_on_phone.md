---
title: "Running Android application on phone"
date: 2010-12-24
forum: General Help
---

### Post by Vistz on 2010-12-24
I'm attempting to run my android application on my phone. But every time I run it in Eclipse, I see question marks where the device info should be.

1) I have turned on USB debugging on my phone
2) I have created a new file 
[HTML]/etc/udev/rules.d[/HTML] 
with the text
[HTML]SUBSYSTEMS==&#8221;usb&#8221;, ATTRS{idVendor}==&#8221;22b8&#8243;, ATTRS{idProduct} ==&#8221;41db&#8221;, MODE=&#8221;0600&#8243;[/HTML]

I used the vendor id provided **[here]("http://developer.android.com/guide/developing/device.html")**

I also seem to be having some issues with the "adb" command. When I navigate to the directory (it's in platform-tools now) and type "adb", it says "adb" is not a recognizable command. I already set the "adb" to executable.

---

### Post by eggdeng on 2011-01-11
Put ./ in front of the command:
```
./adb
```

---

### Post by leg on 2011-01-11
Which version of Eclipse are you running? I ask as there was a problem with the latest version and the ADT plugin. I am using Galileo (3.5 I think) and it all works after completing the steps you noted.

---

### Post by Vistz on 2011-01-13
> **eggdeng said:**
> Put ./ in front of the command:
```
./adb
```

Well that was embarrassing.

---

