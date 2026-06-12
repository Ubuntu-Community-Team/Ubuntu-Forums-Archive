---
title: "Two hardware control issues"
date: 2012-05-26
forum: General Help
---

### Post by raptir on 2012-05-26
Not quite sure where these would go, so I figured general help sounded reasonable.

[LIST=1]
[*]I only have 6 brightness options in Xubuntu. The brightness hardware keys work, but the number of options are limited. If I quit xfce4-power-manager, I get about 12 options. But I don't get the battery meter obviously. Is there any way to keep xfce4-power-manager running but not let it steal brightness control? Or to set xfce4-power-manager to allow more brightness options?
[*]Both Bluetooth and Brightness default to on/max when I turn on the computer. Kubuntu remembered the previous value, Ubuntu let me set a default, but I can't find a way to change this in Xubuntu. Is there any way to force a particular brightness/bluetooth state on boot, or have it remember the previous value?
[/LIST]

Thanks in advance for any help, and let me know if you need more info.

---

### Post by raptir on 2012-05-28
Does anyone have any suggestions of how to do this?  Or even an alternative to xfce4-power-manager that would allow this?

---

### Post by raptir on 2012-05-29
One other issue came up, and I'm not sure if its new or I just didn't notice it. I'm using the default LightDM, and the login window (the actual box where you choose your user and enter your password) is off center. It's shifted slightly to the right.

---

### Post by raptir on 2012-05-29
Alright, I found a solution to the number of brightness options.

[http://docs.xfce.org/xfce/xfce4-power-manager/preferences]("http://docs.xfce.org/xfce/xfce4-power-manager/preferences")

```
xfconf-query -c xfce4-power-manager -n -p "/xfce4-power-manager/change-brightness-on-key-events" -t bool -s false
```

However, I have not found any way to set the brightness or bluetooth status on boot.

---

