---
title: "keyboard shortcuts not working in 11.04"
date: 2011-05-02
forum: General Help
---

### Post by BinaryMn on 2011-05-02
Topic pretty much states the problem. Keyboard shortcuts set in Settings -> Settings Manager -> Keyboard -> Application Shotcuts do not work. 

They worked in 10.04. How do I fix this?

---

### Post by eric forman on 2011-05-08
Me too!

In fact...that's why I joined the forum.

---

### Post by Toz on 2011-05-08
> **BinaryMn said:**
> Topic pretty much states the problem. Keyboard shortcuts set in Settings -> Settings Manager -> Keyboard -> Application Shotcuts do not work. 

They worked in 10.04. How do I fix this?

Please reply with results of:```
ps -ef | grep xfce
```
and contents of ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml.

---

### Post by HobbitTR on 2011-05-13
> **BinaryMn said:**
> Topic pretty much states the problem. Keyboard shortcuts set in Settings -> Settings Manager -> Keyboard -> Application Shotcuts do not work. 

They worked in 10.04. How do I fix this?

A bit awkward but this worked GREAT for me:
FIRST:
Settings->Accessories->Application Finder
Put mouse over application; command will show
NEXT:
Settings->Settings Manager->Keyboard->
Then click tab: Application Shortcuts->Add
Paste/Type Command: (Your shortcuts may be different)
<Control>1 exo-open --launch TerminalEmulator
<Control>2thunderbird %u
<Control>3firefox %u
<Control>4/usr/bin/chromium-browser %U
After you paste/type the command, CAREFULLY execute the keystroke combination you wish to use for the shortcut. Test it...:o

---

### Post by keithpeter on 2011-05-13
Hello All

The few short cuts that are in the Keyboard | Application Shortcuts tab are working for me. ps -ef | grep xfce command output below...

```
keith@T42:~$ ps -ef | grep xfce
keith      991   979  0 17:37 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
keith     1034     1  0 17:37 ?        00:00:00 /usr/lib/xfce4/xfconf/xfconfd
keith     1042   991  0 17:37 ?        00:00:00 xfce4-session
keith     1050     1  0 17:37 ?        00:00:06 xfce4-panel
keith     1095     1  0 17:37 ?        00:00:00 xfce4-volumed
keith     1144     1  0 17:37 ?        00:00:00 xfce4-settings-helper
keith     1179     1  0 17:37 ?        00:00:02 xfce4-power-manager
keith     1201  1050  0 17:37 ?        00:00:07 /usr/lib/xfce4-indicator-plugin/xfce4/panel-plugins/xfce4-indicator-plugin  17 20971619 indicator Indicator Plugin An indicator of something that needs your attention on the desktop 
keith     1206  1050  0 17:37 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libthunar-tpa.so 24 20971620 thunar-tpa Wastebasket Applet Display the Wastebasket 
keith     1209  1050  0 17:37 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libsystray.so 18 20971621 systray Notification Area Area where notification icons appear 
keith     3187     1  1 19:41 ?        00:00:00 xfce4-terminal
keith     3246  3192  0 19:42 pts/0    00:00:00 grep --color=auto xfce
```

---

### Post by Krydahl on 2011-06-11
Keyboard shortcuts work for me if I've been using something that expects keyboard input (terminal, writer etc), but if I've most recently been using something that uses mouse only input the system seems to stop looking for keyboard input.

Anyone any ideas were to start looking?

---

### Post by eupharis on 2011-06-19
I ran these two commands and then my keyboard shortcuts worked fine:

Remove or rename the global autostart .desktop file:

```
mv /etc/xdg/autostart/xfce4-settings-helper-autostart.desktop /etc/xdg/autostart/xfce4-settings-helper-autostart.desktop.disabled
```

Remove or rename the local autostart .desktop file:

```
mv ~/.config/autostart/xfce4-settings-helper-autostart.desktop ~/.config/autostart/xfce4-settings-helper-autostart.desktop.disabled
```

Found the solution [here]("https://wiki.archlinux.org/index.php/Xfce#Keyboard_shortcuts_aren.27t_working").

Also, I used to use the command "xfce-popup-menu" as a shortcut to the menu. After updating, I had to change it to "xfce-popup-applicationsmenu"

---

### Post by Krydahl on 2011-06-22
This seems to be a fix for a problem in xfce 4.6 that is not needed in 4.8. It certainly doesn't fix my problem. 

Thanks for trying though.

---

### Post by Toz on 2011-06-22
I believe **xfce4-settings-helper** needs to be running for the keyboard shortcuts to work. Check if it is:```
ps -ef | grep xfce4-settings-helper
``` and if it is not, fire it up:```
xfce4-settings-helper &
```and see if the shortcuts work.

---

### Post by chipsugar on 2011-06-25
I'm having the same trouble with xfce/mythbuntu and natty although in gnome the shortcuts work fine. For me having xfce4-settings-helper running doesn't make a difference but the "media" keys (also NOT assigned in xfce's shortcuts btw) work as pressing the "mail" button tries to launch evolution.

---

### Post by Perseides on 2011-08-28
Sorry to revive an old post, but i have sane problem with keyboard shortcut not working. 

I think my problem is smth to do wif messed up gnome in compiz ccsm. i d reseted my gnome into defaults after i accidentally set up my . my keyboard shortcuts are not working after that.

to b clear, i set my workspace 1 into alt-1, workspace 2 into alt-2 etc... this is not working now.... 

can any1 plz help?

Edit: problem solved. sorry.

---

### Post by Sopalajo de Arrierez on 2011-12-26
> **Perseides said:**
> 

Edit: problem solved. sorry.

   And how did you solve it? I have tested the above ideas, but no results :-(

   Please give me some help.

---

### Post by Krydahl on 2011-12-26
For me the problem was the way I was trying to run Compiz on top of xfce. I've now abandoned compiz and have had no further problems with keyboard shortcuts.

---

### Post by Sopalajo de Arrierez on 2011-12-26
> **Krydahl said:**
> For me the problem was the way I was trying to run Compiz on top of xfce. I've now abandoned compiz and have had no further problems with keyboard shortcuts.

   I have tested:

```
metacity --replace
```

   and even:

```
sudo apt-get remove compiz
```

   with no luck at all :( . Everything keeps the same.
   Using LXDE I have noticed the Alt+F2 key works only once :confused: and it does never work again until my next desktop login .

---

