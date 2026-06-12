---
title: "Firefox always maximized"
date: 2011-12-03
forum: General Help
---

### Post by Ceris on 2011-12-03
I'm using Ubuntu 11.10 and Firefox 8.0. The problem I have is very simple. It won't save my preferred window size and position for Firefox, so whenever I open it, it's always the same. It starts maximized, and when I restore it to normal size, it still takes up as much of the screen as possible. I then have to resize the window manually every single time.

I wasn't sure whether this was a problem with Ubuntu or Firefox, and eventually decided to put it here. After all, I've never had this issue with Firefox in Windows, and it seems like it might be a problem with the desktop environment... Or something.

---

### Post by bluexrider on 2011-12-03
resize the firefox window to the size you want it, minimize it and close. the next time you start firefox it should have "remembered" its size.

---

### Post by Ceris on 2011-12-03
> **bluexrider said:**
> resize the firefox window to the size you want it, minimize it and close. the next time you start firefox it should have "remembered" its size.

Just tried it, but... It didn't work, sorry.

---

### Post by bluexrider on 2011-12-03
there is another thread here

try this [http://ubuntuforums.org/showthread.php?t=775909](http://ubuntuforums.org/showthread.php?t=775909)

---

### Post by JRV on 2011-12-03
In 11.10 a window will automaximize if it covers over 75% of the screen.  To change this open a terminal and enter this code:
```

sudo apt-get install compizconfig-settings-manager
ccsm

```
Open the Ubuntu Unity Plugin under the Desktop heading.

Click on "Experimental" and change the "Automaximize Value" to 100%.


A window will automaximize if you drag it to the top of the screen.  To change this uncheck "Grid" in the Window Management section.

---

### Post by bluexrider on 2011-12-03
> **JRV said:**
> In 11.10 a window will automaximize if it covers over 75% of the screen.  To change this open a terminal and enter this code:
```

sudo apt-get install compizconfig-settings-manager
ccsm

```Open the Ubuntu Unity Plugin under the Desktop heading.

Click on "Experimental" and change the "Automaximize Value" to 100%.


A window will automaximize if you drag it to the top of the screen.  To change this uncheck "Grid" in the Window Management section.
Well I did not know that, thanks

---

### Post by BC59 on 2011-12-03
> **JRV said:**
> In 11.10 a window will automaximize if it covers over 75% of the screen.  To change this open a terminal and enter this code:
```

sudo apt-get install compizconfig-settings-manager
ccsm

```
Open the Ubuntu Unity Plugin under the Desktop heading.

Click on "Experimental" and change the "Automaximize Value" to 100%.


A window will automaximize if you drag it to the top of the screen.  To change this uncheck "Grid" in the Window Management section.

Very good HOWTO!

---

