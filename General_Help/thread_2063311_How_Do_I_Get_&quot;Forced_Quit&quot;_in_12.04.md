---
title: "How Do I Get &quot;Forced Quit&quot; in 12.04?"
date: 2012-09-26
forum: General Help
---

### Post by coljohnhannibalsmith on 2012-09-26
How Do I Get Forced Quit in 12.04?

Thanks Hannibal

---

### Post by colin.p on 2012-09-26
Do a ctrl-alt-X which will change your cursor to an "X". Then click on offending program to terminate it.

If your computer freezes up and the above won't work, then do a ctrl-alt - tap the "printscreen" key, then tap the "K" key. That will drop you to a login screen. It's better than using the power off button.

---

### Post by HiImTye on 2012-09-27
you can kill a program a number of ways

```
kill <pid>
kill -9 <pid>
sudo kill <pid>
sudo kill -9 <pid>
killall <program name>
killall -9 <program name>
sudo killall <program name>
sudo killall -9 <program name>
xkill (then click on the program window)
```
all of these are acceptable choices. SIGTERM is generally the signal you want to use (kill) but failing that I generally use SIGKILL (kill -9). you can, of course, use other signals, but I generally find that if SIGTERM fails, other signals are less likely to work.

---

### Post by stinkeye on 2012-09-27
....or if you prefer a clickable launcher,copy and paste the below code in gedit and save as **X-Quit.desktop** to **~/.local/share/applications**
Then drag and drop **X-Quit.desktop** to the unity launcher.
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=gnome-panel-force-quit
Name=X-Quit
Exec=sh -c 'notify-send -i gnome-panel-force-quit "Click on an application to force-close it, or right-click to cancel."; xkill'
Comment=Click on the app to quit


```

---

