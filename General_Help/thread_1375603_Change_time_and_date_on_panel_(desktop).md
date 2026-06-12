---
title: "Change time and date on panel (desktop)"
date: 2010-01-08
forum: General Help
---

### Post by Sicadastra on 2010-01-08
Hello,

Does anyone know how to change the style of the time and date shown on the panel for Karmic Koala? As shown on my attached screenshot located at the upper right corner, it does not show the year which is a bit vexing and I cannot figure it out how to change it.

  _[[IMG]http://img527.imageshack.us/img527/623/screenshotyj.th.png[/IMG]]("http://img527.imageshack.us/i/screenshotyj.png/")_[[IMG]http://img527.imageshack.us/img527/screenshotyj.png/1/w1280.png[/IMG]]("http://g.imageshack.us/img527/screenshotyj.png/1/")

---

### Post by stinkeye on 2010-01-08
Open configuration editor.
Go to /apps/panel/applets/clock_screen0/prefs
for format use ```
custom
``` 
for custom_format use ```
%a %d-%b-%Y %I:%M
```

or however you want it to look using your own format.
[_[COLOR="DarkRed"]http://au2.php.net/strftime[/COLOR]_]("http://au2.php.net/strftime")

eg
```
%a %d-%b-%Y %I:%M
```[ATTACH]142873[/ATTACH]

```
%a %d-%b%n%Y %I:%M
```[ATTACH]142874[/ATTACH]

```
%x%n%I:%M %P
```[ATTACH]142875[/ATTACH]

%n will create a new line but you have to increase your panel size to see it.

---

### Post by Sicadastra on 2010-01-09
> **stinkeye said:**
> Open configuration editor.
Go to /apps/panel/applets/clock_screen0/prefs
for format use ```
custom
```for custom_format use ```
%a %d-%b-%Y %I:%M
```or however you want it to look using your own format.
[_[COLOR=DarkRed]http://au2.php.net/strftime[/COLOR]_]("http://au2.php.net/strftime")

eg
```
%a %d-%b-%Y %I:%M
```[ATTACH]142873[/ATTACH]

```
%a %d-%b%n%Y %I:%M
```[ATTACH]142874[/ATTACH]

```
%x%n%I:%M %P
```[ATTACH]142875[/ATTACH]

%n will create a new line but you have to increase your panel size to see it.

Thank you for this. However, When I tried the first code you gave as example, the year still would not appear even after a reboot. Do you know how I can solve the problem?

Thanks.

---

### Post by stinkeye on 2010-01-09
> **Sicadastra said:**
> Thank you for this. However, When I tried the first code you gave as example, the year still would not appear even after a reboot. Do you know how I can solve the problem?

Thanks.
Did you change the format to ***custom***
No need to restart. It will change instantly and you can try different formats.
To change back to default just change ***custom*** to
**12-hour**
or
**24-hour**
in the format value.

---

### Post by Sicadastra on 2010-01-09
> **stinkeye said:**
> Did you change the format to ***custom***
No need to restart. It will change instantly and you can try different formats.
To change back to default just change ***custom*** to
**12-hour**
or
**24-hour**
in the format value.


Oh, I'm having trouble following simple instructions. :(

It worked, thank you very much for your assistance.

---

### Post by rapo007 on 2010-01-09
thanks for your tips.
[http://www.areapla.com/rapo/](http://www.areapla.com/rapo/)

---

### Post by stinkeye on 2010-01-09
> **Sicadastra said:**
> Oh, I'm having trouble following simple instructions. :(

It worked, thank you very much for your assistance.
No problem.Glad to help.
Some custom [_[COLOR="DarkRed"]time formats[/COLOR]_]("http://www.omgubuntu.co.uk/2009/11/gnome-panel-clock-themes.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29") to try.

---

### Post by afternine on 2010-01-29
Your tip is really what all tips should look like: clear, precise and complete. Thanx!

---

### Post by Sicadastra on 2010-02-25
> **stinkeye said:**
> No problem.Glad to help.
Some custom [_[COLOR=DarkRed]time formats[/COLOR]_]("http://www.omgubuntu.co.uk/2009/11/gnome-panel-clock-themes.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29") to try.

Hi, 

I hope you won't mind me asking again about changing the time and date on the panel again. I deleted my upper panel and I had to restore it back. When I tried configuration editor, I could not find the clock_screen0 folder already. I tried to locate it through find, found this **/apps/panel/default_setup/applets/clock** but it does not have the same configurations.

Would you know what the problem be? I would really appreciate your help. Thank you.

---

### Post by stinkeye on 2010-02-25
> **Sicadastra said:**
> Hi, 

I hope you won't mind me asking again about changing the time and date on the panel again. I deleted my upper panel and I had to restore it back. When I tried configuration editor, I could not find the clock_screen0 folder already. I tried to locate it through find, found this **/apps/panel/default_setup/applets/clock** but it does not have the same configurations.

Would you know what the problem be? I would really appreciate your help. Thank you.
If you don't have the path 
/apps/panel/applets/clock_screen0/prefs in config editor
I don't know where it might be or how to get it back because I don't know what you did to get rid of gnome-panel.
Maybe reinstall gnome-panel and gnome-applets through synaptic.

---

### Post by Sicadastra on 2010-02-25
> **stinkeye said:**
> If you don't have the path 
/apps/panel/applets/clock_screen0/prefs in config editor
I don't know where it might be or how to get it back because I don't know what you did to get rid of gnome-panel.
Maybe reinstall gnome-panel and gnome-applets through synaptic.

Well I've managed to restore all my applets on my panel. Only that I'm back to zero with my customization for my time and date. When I checked my configuration editor, the folder for the clock_screen0 was missing so it boggles me because I do have the applet. Under the apps/panel/applets folder only contained several applets folder, which I've checked.

Anyway, thank you for the fast reply. I still appreciate it. :)

---

