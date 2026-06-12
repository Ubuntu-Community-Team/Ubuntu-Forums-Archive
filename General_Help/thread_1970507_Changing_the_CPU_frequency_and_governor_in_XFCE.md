---
title: "Changing the CPU frequency and governor in XFCE"
date: 2012-05-01
forum: General Help
---

### Post by samalex on 2012-05-01
I just installed Xubuntu 12.04 which is my first time to use XFCE, and I'm LOVING it!  The only thing I'm unable to find is how to easily change the CPU frequency and governor.  My system defaults to 800Mhz and OnDemand which is fine, but it seems very sluggish.  I was running Ubuntu 10.04 and had a panel applet that let me change these, and kicking it up to 2.5Mhz and Performance would hugely increase the snappiness of the system.  I want to do the same in XFCE.

I found [xfce4-cpufreq-plugin]("http://goodies.xfce.org/projects/panel-plugins/xfce4-cpufreq-plugin") which shows what the frequency and governor are set to on both processors, but it's more informational and doesn't actually change them.

So any other suggestions?

Thanks --

Sam

---

### Post by Toz on 2012-05-01
From a terminal prompt, you could:
```
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```
...but you need root privileges to do this.

There is also jupiter. See: [http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html]("http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html") and post #5 here: [http://ubuntuforums.org/showthread.php?t=1867276]("http://ubuntuforums.org/showthread.php?t=1867276") to get it to work in xubuntu.

---

### Post by samalex on 2012-05-01
Toz, Perfect!  Thanks.

Update: Jupiter is a no-go on Xubuntu 12.04.  It crashes after I install it, so i had to uninstall it.  Oh well, worth trying, but a least it changed the default governor to Performance which is good.

---

### Post by Yrralhann on 2012-10-14
Thanks to samalex for asking this question, and thanks to Toz for answering it, I found this info very helpful. :)

In the interest of sharing, here is a little shellscript i wrote that I'm hoping might be of some use to anyone else in our situation, it's just a simple menu with an extra feature or two.;)

Afaik, this will only work if the [COLOR=Blue]xfce4-cpufreq-plugin[/COLOR] and [COLOR=Blue]indicator-cpufreq [/COLOR]packages are installed.
Options 6 and 7 in the menu require the [COLOR=Blue]cpuid[/COLOR] and [COLOR=Blue]lm-sensors [/COLOR]packages to be installed.

```

#!/bin/bash
function main_menu
{
    sudo clear
    cursetting=$(cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor)
    getspd=$(cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq)
    curspd=$(echo $getspd 1000000 | awk '{printf $1 / $2}')
    echo ""
    echo ""
    echo "-----------------CPU Settings---------------------"
    echo "1. Allow software to set CPU speed (UserSpace) setting."
    echo "2. Set CPU to Minimum (Powersave) setting."
    echo "3. Set CPU to Low (Conservative) setting."
    echo "4. Set CPU to Medium (OnDemand) setting."
    echo "5. Set CPU to High (Performance) setting."
    echo "6. View CPUID info string."
    echo "7. View Temperature sensor info string."
    echo "8. Exit."
    echo "--------------------------------------------------"
    echo "        Current CPU Setting - "$cursetting;
    echo "        Current CPU Speed - "$curspd"GHz";
    choice=9
    echo ""
    echo -e "Please enter your choice: \c"
}

function press_enter
{
    echo ""
    echo -n "Press Enter to continue."
    read
    main_menu
}    

main_menu
while [ $choice -eq 9 ]; do
read choice

if [ $choice -eq 1 ]; then
    echo userspace | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
    main_menu
    else
if [ $choice -eq 2 ]; then
    echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
    main_menu
    else
if [ $choice -eq 3 ]; then
    echo conservative | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
    main_menu
    else
if [ $choice -eq 4 ]; then
    echo ondemand | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
    main_menu
    else
if [ $choice -eq 5 ]; then
    echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
    main_menu
    else
if [ $choice -eq 6 ]; then
    echo ""
    echo ""
    echo ""
    cpuid;
    press_enter
    else
if [ $choice -eq 7 ]; then
    echo ""
    echo ""
    echo ""
    sensors;
    press_enter
    else
if [ $choice -eq 8 ]; then
    exit;
    else
    echo -e "Please enter the NUMBER of your choice: \c"
    choice=9
fi
fi
fi
fi
fi
fi
fi
fi
done

```

---

### Post by The Cog on 2012-10-14
There is this:
cpufreq-set - A small tool which allows to modify cpufreq settings.
Try: man cpufreq-set

---

### Post by Yrralhann on 2012-10-14
> **The Cog said:**
> There is this:
cpufreq-set - A small tool which allows to modify cpufreq settings.
Try: man cpufreq-set

Thank you Cog, this utility is part of the [COLOR=Blue]cpufrequtils[/COLOR] package, it definitely helps shorten the command to something a bit more managable

```
sudo cpufreq-set -g performance
```

Still the package doesn't seem to provide any gui alternatives for XFCE, not a big deal since most of us are just going to setup a shell script for it anyway, but the gui option in Unity I must admit is very nice.

---

