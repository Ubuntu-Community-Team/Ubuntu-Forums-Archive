---
title: "Simple Command To Show Memory Chip Info"
date: 2012-08-31
forum: General Help
---

### Post by NM5TF on 2012-08-31
I am looking for a simple command that will list my RAM info...I am
looking to increase my RAM capacity, but need to know what type I have
to order compatible chips.

Have already tried SysInfo with no luck, it just tells me how much I have used...

Any help???

Tommy

---

### Post by Zill on 2012-08-31
To produce a listing of your hardware run the following command:
```
sudo lshw -html > ~/Desktop/hardware.html
```
Click on the resulting file (hardware.html) to open this in your web browser.
```
man lshw
```

---

### Post by NM5TF on 2012-08-31
thanks for the reply Zill....worked great!!!

BTW, love your Avatar.....waiting for new season to start on BBC America!!!

Tommy

---

### Post by phosphide on 2012-08-31
You could always try:

```
sudo lshw
```

lshw will return a ton of information, so search through it to find the info you need. You could also do:

```
sudo lshw | grep -A 25 "System Memory"
```
That will return 25 lines following "System Memory" in the lshw command. Change the 25 to a bigger number if you don't get all that you need.

---

