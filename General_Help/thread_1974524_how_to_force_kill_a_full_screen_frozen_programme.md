---
title: "how to force kill a full screen frozen programme?"
date: 2012-05-06
forum: General Help
---

### Post by fredphoesh on 2012-05-06
Hello guys,

XBMC crashes quite frequently with certain add-ons I very much want to use... if xbmc is full screen it seems impossible to kill the process as you cannot bring up the system monitor.

in windows, you press CTRL-SHIFT-ESC and the event viewer pops up.
is there a similar command for the system monitor, or a simple (non-super-coding-genius) way to do that... or a command more powerful than Alt-F4?

Thanks!
Mark.

---

### Post by Paqman on 2012-05-06
If you can still pull up Alt-F2 you can type:
```
xkill
```
and click on it. If that doesn't work you can hit Ctrl-Alt-F1 to bring up a virtual terminal. Then:
```
ps -A
```
Note the pid of the process (such as xbmc), and:
```
kill -9 *pid*
```

---

### Post by davidvandoren on 2012-05-06
IF that doesn't work you can push ctrl+alt+ PrtSc/sysRq
 While holding the keys type one after one slowly **R E I S U B **

Your pc will restart

---

### Post by tomatoe on 2012-05-06
You can also find the PID with this command
```
ps aux | grep xbmc
```

Grep will only show results from ps aux that have xbmc in process name

---

### Post by fredphoesh on 2012-05-06
> **Paqman said:**
> If you can still pull up Alt-F2 you can 

hi there
alt-f2 does not work

i can try those codes, though it seems my computer does not go back to ubuntu when i press ctrl alt f7.

is there no keyboard command to bring up the system monitor? all this code stuff is a major PITA for me... like back to 1982 with DOS ;)

Tx
Mark

---

### Post by StApnea on 2012-05-06
I don't know of a keyboard command for system monitor and if alt-f2 doesn't appear, I'm not sure System Monitor would either. If you still wanted a keyboard shortcut, though, it would be very easy to make.

---

### Post by fredphoesh on 2012-05-06
> **StApnea said:**
> I don't know of a keyboard command for system monitor and if alt-f2 doesn't appear, I'm not sure System Monitor would either. If you still wanted a keyboard shortcut, though, it would be very easy to make.

Hi
Yeah good point... I guess xbmc could (?) write their code so even if xbmc is full screen, you can alt-tab to other apps, which MAY mean being able to alt-tab to system monitor.

Tx
Mark

---

### Post by jerome1232 on 2012-05-06
alt+sysrq+k will restart your xsession (sysrq is usually prtscrn), you can also setup a custom keyboard shortcut in System Settings-Keyboard-Keyboard Shortcuts to launch system-monitor [I doubt it'll run if alt+f2 won't work]. Pressing ctrl+alt+f1 will get you to a tty where you can 'sudo killall taskname' then ctrl+alt+f7 back to the gui.

---

### Post by fredphoesh on 2012-05-06
> **jerome1232 said:**
> ctrl+alt+k will restart your xsession, you can also setup a custom keyboard shortcut in System Settings-Keyboard-Keyboard Shortcuts to launch system-monitor [I doubt it'll run if alt+f2 won't work]. Pressing ctrl+alt+f1 will get you to a tty where you can 'sudo killall taskname' then ctrl+alt+f7 back to the gui.

Hi
I will try those commands when it freezes again, thanks... but it assumes I know the taskname! I have no idea what the taskname of xbmc is.

I tried to create a keyboard shortcut, but it requires that you know some code, ie, you cannot just find the app you want in a list and apply a command to it, you have to know what the command for the app is. I tried System Monitor, then system-monitor and neither work.

Boy, this ubuntu is still waaaay more difficult than windows.

Mark.

---

### Post by jockyburns on 2012-05-06
I too have experienced problems with  my screen/computer freezing and becoming unresponsive (usually when Chrome is open) I can't bring the terminal up to kill Chrome, nor shutdown using the on screen buttons. Up to now, Iv'e had to force a shutdown using the power button on the front of my computer. If Ubuntu freezes, are any logs generated? If they are , where would these be stored?

---

### Post by jerome1232 on 2012-05-06
> **fredphoesh said:**
> Hi
I will try those commands when it freezes again, thanks... but it assumes I know the taskname! I have no idea what the taskname of xbmc is.

I tried to create a keyboard shortcut, but it requires that you know some code, ie, you cannot just find the app you want in a list and apply a command to it, you have to know what the command for the app is. I tried System Monitor, then system-monitor and neither work.

Boy, this ubuntu is still waaaay more difficult than windows.

Mark.

It's gnome-system-monitor, you can figure out the launch command by opening alacarte, and searching for the menu entry, then pressing the properties box.

The taksname is likely xbmc. Why don't you just check system monitor for it take note of the name.

For the record, I find Windows *Exceedingly* more difficult to work with than Ubuntu. It all depends on what your familiar with really. I wouldn't even know how to setup a custom keyboard shortcut in Windows or if you even can!


My suggestion really is to simply find addons that don't crash your system.

---

### Post by The Cog on 2012-05-06
This sequence will kill the X session, dropping you back to the login prompt:
Press and hold both the Ctrl and Alt keys. While still holding them down, press and release SysReq (which on a laptop may also need Fn), then press and release the K key. At this point the GUI should be killed and you can release Ctrl-Alt.

---

### Post by jim_24601 on 2012-05-08
Are you saying you can't drop down to a text mode console with ctrl+alt+f1 (... f6) and kill the offending process from the command line?

---

