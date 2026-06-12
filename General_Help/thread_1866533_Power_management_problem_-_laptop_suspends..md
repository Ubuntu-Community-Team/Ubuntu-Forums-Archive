---
title: "Power management problem - laptop suspends."
date: 2011-10-21
forum: General Help
---

### Post by Borts on 2011-10-21
[FONT=Tahoma]Hey guys,

I'm having this issue on Ubuntu 11.10 with Gnome 3. Whenever I unplug my laptop from charger, system gives me "your battery is critically low" and my laptop suspends after few seconds, even though battery is full. And only in case it's 100% full, then it doesn't suspend. If it's 90-97% full- suspends right away. I had same problem on Natty, and I did fix it, it's known bug from what I remember, but did clean install of Oneiric and I can't find fix this time. :c
Anyone had this problem before? Any ideas of how to fix it? There is some bug in gnome-power-manager reporting incorrect values, that's why it suspends...
Your help would be greatly appreciated.
Oh, yes, I have Dell Studio 1440, if that matters. I doubt it does though.
[/FONT]

---

### Post by lovinglinux on 2011-10-21
It started to work for me after installing Jupiter, but I am not sure if it was a coincidence. The article mentions improvements in power management.

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by Borts on 2011-10-21
[FONT=Verdana]Didn't work. :c
[http://goo.gl/1XoJW](http://goo.gl/1XoJW)
Installed Jupiter, restarted, tried switching power modes- when it hits  85% recharging, then if I unplug it- suspends.. >> Annoying bug,  really.
I searched all over my Firefox history, can't find the solution I found  before. I'm getting desperate, yet, I'm sure there is a solution.
But thanks for the tip about Jupiter.
[/FONT]

---

### Post by lovinglinux on 2011-10-21
> **Borts said:**
> [FONT=Verdana]Didn't work. :c
[http://goo.gl/1XoJW](http://goo.gl/1XoJW)
Installed Jupiter, restarted, tried switching power modes- when it hits  85% recharging, then if I unplug it- suspends.. >> Annoying bug,  really.
I searched all over my Firefox history, can't find the solution I found  before. I'm getting desperate, yet, I'm sure there is a solution.
But thanks for the tip about Jupiter.
[/FONT]

Sorry to read that. Perhaps I did something else then.I was trying several methods.

I read that power management needs to "learn" about your battery, so perhaps it will fix itself with time.

---

### Post by Borts on 2011-10-22
Probably you did something else that it worked. Probably power manager "learned" about you battery after you discharged it and charged it again couple of times, yeah, I think that's possible too. But I'm still sure there is a way to "teach" it. I'll keep looking.
Thanks anyway.

EDIT:
YES!!! Found it. Found same link I used 2 months ago.[SIZE=2][B]
Laptop suspends when I connect/disconnect AC:[/B][/SIZE]
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481312](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481312)[SIZE=2]
[/SIZE]**[SIZE=2]upower (devkit-power) reporting bad data when AC cable is [/SIZE][SIZE=2]unplugged[/SIZE]**
[https://bugs.launchpad.net/devicekit-power/+bug/531190](https://bugs.launchpad.net/devicekit-power/+bug/531190)

Although:
```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```This ^ won't work, since there is no "gnome-power-manager" entry. Yet, there is a patch in C ,[patch for natty version (upower0.9.8-1build1)]("https://launchpadlibrarian.net/63377553/patch.upower0.9.8-1build1_up-device-supply.c"), which worked for me last time, so I'm gonna try it now too. Hope this works.

EDIT 2:
WORKED! There is another fix exactly for 11.10:

                                                       "In order to work around this issue in Oneiric, you can issue the following command:
 gsettings set org.gnome.settings-daemon.plugins.power 'use-time-for-policy' 'false'
 You can alternatively do the following:
 1. sudo apt-get install dconf-tools
2. dconf-editor
3. Navigate to the 'org.gnome.settings-daemon.plugins.power' section
4. Uncheck 'use-time-for-policy' "


Worked like a charm. When I unplug power at 70%, gives me "1 minute remaining" at first, after couple of seconds "43 minutes remaining", and doesn't suspend the system.
I love Ubuntu for it's community. Hope it helps someone else.

---

### Post by skitfish on 2011-10-28
Borts,

  I wanted to write to say thank you for your 'EDIT 2' of your post above. I had spent too much time on trial-and-error changes in the GConfEditor only to find my laptop suspending regardless, whenever I disconnected the AC power.

  For other people out there using Oneiric, dconf-editor reveals more options than GConfEditor, and changing those options fixed the suspend/shutdown/hibernate problem when the AC power was disconnected. Follow Borts' instructions above (EDIT 2) and you should be sitting pretty.


Thanks again Borts,
skitfish

---

### Post by zipmon on 2011-11-01
> **Borts said:**
> In order to work around this issue in Oneiric, you can issue the following command:
 gsettings set org.gnome.settings-daemon.plugins.power 'use-time-for-policy' 'false'

Thank you SO much!!

---

### Post by werewolves on 2011-11-01
Awesome, thanks a million.

---

### Post by Borts on 2011-11-07
I'm glad it helped so many people. :) Turns out I wasn't the only one having this issue. All thanks to the_ _[Monkey (chris-boyle-1978)]("https://launchpad.net/%7Echris-boyle-1978") from this place:
[https://bugs.launchpad.net/devicekit-power/+bug/531190](https://bugs.launchpad.net/devicekit-power/+bug/531190)
I just googled it good. ;)
Help the community, and someone will help you back when you will have your problems.

---

### Post by AkifTariq on 2012-02-28
Thank you so much Borts for sharing this fix with us.

I have been facing this problem since upgrading to 11.10. Could live with it but I also upgraded my fathers laptop with it and it also had the same issue.

He will be relieved now.

Regards.

---

### Post by simn_stv on 2012-05-11
Thanks Bots...that fixed it for me too.:grin:

---

### Post by mtayyab1984 on 2013-02-15
> **Borts said:**
> Probably you did something else that it worked. Probably power manager "learned" about you battery after you discharged it and charged it again couple of times, yeah, I think that's possible too. But I'm still sure there is a way to "teach" it. I'll keep looking.
Thanks anyway.

EDIT:
YES!!! Found it. Found same link I used 2 months ago.[SIZE=2][B]
Laptop suspends when I connect/disconnect AC:[/B][/SIZE]
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481312](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481312)[SIZE=2]
[/SIZE]**[SIZE=2]upower (devkit-power) reporting bad data when AC cable is [/SIZE][SIZE=2]unplugged[/SIZE]**
[https://bugs.launchpad.net/devicekit-power/+bug/531190](https://bugs.launchpad.net/devicekit-power/+bug/531190)

Although:
```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```This ^ won't work, since there is no "gnome-power-manager" entry. Yet, there is a patch in C ,[patch for natty version (upower0.9.8-1build1)]("https://launchpadlibrarian.net/63377553/patch.upower0.9.8-1build1_up-device-supply.c"), which worked for me last time, so I'm gonna try it now too. Hope this works.

EDIT 2:
WORKED! There is another fix exactly for 11.10:

                                                       "In order to work around this issue in Oneiric, you can issue the following command:
 gsettings set org.gnome.settings-daemon.plugins.power 'use-time-for-policy' 'false'
 You can alternatively do the following:
 1. sudo apt-get install dconf-tools
2. dconf-editor
3. Navigate to the 'org.gnome.settings-daemon.plugins.power' section
4. Uncheck 'use-time-for-policy' "


Worked like a charm. When I unplug power at 70%, gives me "1 minute remaining" at first, after couple of seconds "43 minutes remaining", and doesn't suspend the system.
I love Ubuntu for it's community. Hope it helps someone else.

Thanks a bundle.... worked like a charm... :popcorn:
For other newbies I was searching for dconf-editor in directories then I found that its an app installed on system like others.... just goto the left bar and type dconf in search....

---

