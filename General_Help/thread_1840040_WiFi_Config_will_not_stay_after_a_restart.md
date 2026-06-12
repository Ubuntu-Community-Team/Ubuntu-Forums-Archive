---
title: "WiFi Config will not stay after a restart"
date: 2011-09-06
forum: General Help
---

### Post by deadstump on 2011-09-06
I have a rather fresh install of lubunto 11.04 on an old HP Pavilion zv5000 and I had some trouble getting the WiFi to work, but with the use of [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") helpful bit of Ubuntu Documentation I was able to get my WiFi to work.  I have a bcm4306 card if you were wondering (the instructions for this card start at about 1/3 the way down that page).  But every time I restart my computer I have to re-enter the last two lines of code into the terminal.  The code I have to enter is this

~$ sudo modprobe -r b43 ssb
  ~$ sudo modprobe b43


And then my WiFi works.  Is there any way for the WiFi to keep its configuration so I don't have to do this every time?


Any help would be greatly appreciated.

---

### Post by fooman on 2011-09-06
have you tried adding b43 to the list of startup modules in /etc/modules ?

might try that if you have not already.  just open a terminal, and type or copy/paste the following command:

```
echo "b43" | sudo tee -a "/etc/modules"
```

then restart the computer.  hope that helps.

---

### Post by kerry_s on 2011-09-06
try putting those commands in /etc/rc.local


gksudo leafpad /etc/rc.local

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r b43 ssb &
modprobe b43 &

exit 0


```

the "&" is so if there is a problem it will continue to boot, not just stop.

---

### Post by deadstump on 2011-09-06
Fooman's suggestion worked.  I also tried kerry_s's suggestion, but I have tried to enter it in the text editor and have added the lines of code you suggested, but I cannot seem to save the changes made.  Is there some other way I have to do this for future reference?

---

### Post by kerry_s on 2011-09-06
> **deadstump said:**
> Fooman's suggestion worked.  I also tried kerry_s's suggestion, but I have tried to enter it in the text editor and have added the lines of code you suggested, but I cannot seem to save the changes made.  Is there some other way I have to do this for future reference?

as root, that's the "gksudo leafpad /etc/rc.local" command i put to open the file. you can use the run command in the menu or alt+f2 or from terminal. just remember sudo is for terminal commands & gksudo is for gui apps.

also in pcmanfm you can use the tools to open the whole folder as root & then edit it with the editor.

---

