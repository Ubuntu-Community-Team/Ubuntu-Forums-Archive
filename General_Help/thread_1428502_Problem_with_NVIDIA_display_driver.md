---
title: "Problem with NVIDIA display driver"
date: 2010-03-12
forum: General Help
---

### Post by hemajith on 2010-03-12
I have a Ubuntu 9.10 fresh installation and have a Nvidia MX400 display adapter. After I activated the proprietary driver, I can only have 800x600 resolution! When I set it to 1024x768 and the monitor refresh rate to 60Hz, I get the resolution, BUT when I try to save the setting to X configuration file, it gives an error message, 

"Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Because of this each time I restart, I have to set the resolution!! Can anyone help to solve this??

thanx

---

### Post by Tourdog on 2010-03-12
[hemajith]("http://ubuntuforums.org/member.php?u=582964"),

"How to: Wrong/low Resolution and Flicker" posted 12 Nov 2009,  in General Help.  Search that posting and it will solve your situation.   It is the old Nvidia problem and Ubuntu.

I used his* 7 steps to solve mine which sounds exactly the same as yours!
HTH!


*It was posted 12 Nov 2009 in General Help by "Giblet5"

---

### Post by jocko on 2010-03-12
> **hemajith said:**
> "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Because of this each time I restart, I have to set the resolution!! Can anyone help to solve this??

thanx
You have to run nvidia-settings as root to be able to save the changes, so start it by typing this in a terminal:
```
gksudo nvidia-settings
```

---

### Post by DNCashman on 2010-03-17
I just had this exact same problem. Fresh install of 9.10. 185nvidia driver, 9400GT card.

Upon saving the changes from the gksudo nvidia-settings function I got this warning:

```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

```

And the same issues as the OP had :(

---

### Post by DNCashman on 2010-03-18
Okay I found a solution incase someone searches and/or finds this thread:

nvidia-settings dislikes the default xorg.conf file and therefore running this command wipes the default xorg.conf into a file nvidia-settings can parse:
```
sudo nvidia-xconfig
```

Then run the standard:
```
sudo nvidia-settings
``` and you should be able to save your changes!

---

### Post by hemajith on 2010-03-20
> **DNCashman said:**
> Okay I found a solution incase someone searches and/or finds this thread:

nvidia-settings dislikes the default xorg.conf file and therefore running this command wipes the default xorg.conf into a file nvidia-settings can parse:
```
sudo nvidia-xconfig
```

Then run the standard:
```
sudo nvidia-settings
``` and you should be able to save your changes!

I tried it and it worked!! I'm able to save my settings now. Thank you. Keep up the good work.

---

