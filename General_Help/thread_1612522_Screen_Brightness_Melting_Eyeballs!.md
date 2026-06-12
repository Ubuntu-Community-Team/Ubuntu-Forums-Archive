---
title: "Screen Brightness Melting Eyeballs!"
date: 2010-11-03
forum: General Help
---

### Post by SandWrrm on 2010-11-03
Hey guys,
I just re-installed Lucid on my laptop, and I CAN'T TURN THE SCREEN BRIGHTNESS DOWN. I opened the power manager (the one that comes up when you click on the battery icon,) and I can move the slidey bar to change the brightness percentage, but it won't actually change; I can set it as 50% and it will actually be 100.
If it helps, I'm using an HP Pavillion notebook.

---

### Post by carini on 2010-11-15
Same problem to me with kubuntu 10.10 on HP Pavilion dv6.

I assume that kernel/acpi is working since if i check for allowed brightness

```
root@host:~# cat /proc/acpi/video/VGA1/LCD/brightness
levels:  0 10 20 30 40 50 60 70 80 90 100
current: 80
```

And if I try to change the backlight brightness with

```
echo "10" > /proc/acpi/video/VGA1/LCD/brightness
```

The screen dimming works properly.

A workaround is to install cpufreqd service and configure it to dim properly the screen with the appropriate exec_post in rules

```
root@host:~# cat /etc/cpufreqd.conf 
# this is a comment
[...]

# conservative mode when not AC
[Rule]
name=AC Off - Medium Battery
ac=off                   # (on/off)
battery_interval=60-80
profile=Conservative Low
exec_post=echo 20 > /proc/acpi/video/VGA1/LCD/brightness
[/Rule]
```


but installing cpufreqd is just a workaround and, sometime KDE powerdevil turn brightness to 100% again

Keyboard backlight control keys ( fn7 / fn8 ) dosen't work. If pressed they turn backlight back to 100%

After a short search I found also that there is a config-file

```
root@host:~# cat /etc/acpi/events/videobtn 
# /etc/acpi/events/videobtn
event=video.* 00000080
action=/etc/acpi/videobtn.sh
```

But file videobtn.sh seems missing.

---

