---
title: "everything possible, terminal app?"
date: 2012-08-21
forum: General Help
---

### Post by arturusch on 2012-08-21
Hello guys...

One issue I dont know how to fix,if one can do it. Well, anything is possible with Ubuntu.

I created with Main Menu an application that start the terminal and directly logs into my ssh account.
terminal -e "ssh -l user host.com" --title="au-s@cosmo"
I gave it a separate icon to add to launcher.

Then when I start the terminal (new one) I get two indicator arrows besides my new app-icon and not the real terminal.

See the pic attached. See , when I launch the terminal (black icon) I dont get the indicator arrow there after I hit the icon in the launcher but instead it automatically indicates that two applications are running.
 which is not the entire truth. 
I started my new app first then terminal, shouldnt it be one arrow for new app and on for the terminal?

---

### Post by ajgreeny on 2012-08-21
But your new app, as you call it, is just a terminal running a command (ssh) so whatever you call the app, it is actually just a terminal.

---

### Post by arturusch on 2012-08-22
> **ajgreeny said:**
> But your new app, as you call it, is just a terminal running a command (ssh) so whatever you call the app, it is actually just a terminal.
 
That is so correct Sir. Allthough I wanted the indicator arrow to specifically indicate that app in the launcher while its active. And when I start another "Terminal" I wanted that to indicate the "Terminal" icon instead and vice versa.
No way to get around this problem?

---

### Post by ajgreeny on 2012-08-22
> **arturusch said:**
> That is so correct Sir. Allthough I wanted the indicator arrow to specifically indicate that app in the launcher while its active. And when I start another "Terminal" I wanted that to indicate the "Terminal" icon instead and vice versa.
No way to get around this problem?
I have no idea, I'm afraid.  I don't even use unity, so can not try it for myself.

---

### Post by efflandt on 2012-08-22
The only work around seems to be opening a completely separate terminal with **Ctrl+Alt+T** instead of using the terminal icon in Unity bar.

Otherwise Unity seems to associate terminals launched by it with whichever icon opened a terminal first, even if you right click the terminal icon and select **New Terminal**.  Similarly if you open a terminal first and they use your ssh launcher, another hash mark shows up on the terminal icon instead of the ssh launcher icon.

---

### Post by arturusch on 2012-08-22
> **efflandt said:**
> The only work around seems to be opening a completely separate terminal with **Ctrl+Alt+T** instead of using the terminal icon in Unity bar.

Otherwise Unity seems to associate terminals launched by it with whichever icon opened a terminal first, even if you right click the terminal icon and select **New Terminal**.  Similarly if you open a terminal first and they use your ssh launcher, another hash mark shows up on the terminal icon instead of the ssh launcher icon.


Okay. Thanks.

---

### Post by stinkeye on 2012-08-22
Possibly use another terminal app like guake just for your ssh.

eg
```
guake -e "ssh -l user host.com" --title="au-s@cosmo"
```

**PS:** If you use guake and want it to show in the top panel in unity run this command...
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'gnote', 'artha', 'clementine', 'guake']"
```

log out/in.
It has a couple of extras in there but won't hurt.

---

### Post by arturusch on 2012-08-23
> **stinkeye said:**
> Possibly use another terminal app like guake just for your ssh.
 
eg
```
guake -e "ssh -l user host.com" --title="au-s@cosmo"
```
 
Will do! Thank you.

---

