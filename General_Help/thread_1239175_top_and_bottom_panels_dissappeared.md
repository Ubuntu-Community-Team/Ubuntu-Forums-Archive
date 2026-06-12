---
title: "top and bottom panels dissappeared"
date: 2009-08-13
forum: General Help
---

### Post by hairchin67 on 2009-08-13
i lost access to my top and bottom panels. I cannot get to my launchers applications etc. How  can I restore this?

---

### Post by matthewbpt on 2009-08-13
try 'Alt + F2' and type in gnome-panel and press enter. Does this problem persist when you restart?

---

### Post by hairchin67 on 2009-08-13
> **matthewbpt said:**
> try 'Alt + F2' and type in gnome-panel and press enter. Does this problem persist when you restart?

i still have this problem

---

### Post by mordecai83 on 2009-08-13
Try this in a terminal

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

That should do the trick

With kind regards,
Mordecai

---

### Post by wojox on 2009-08-13
In order to get the terminal for above press Alt+F2 type in gnome-terminal then hit run.

---

### Post by hairchin67 on 2009-08-13
> **mordecai83 said:**
> Try this in a terminal

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

That should do the trick

With kind regards,
Mordecai

craig@craig-desktop:~$ gconftool-2 --shutdown rm -rf ~/.gconf/apps/panel pkill gnome-panel
Error while parsing options: Unknown option -rf.
Run 'gconftool-2 --help' to see a full list of available command line options.
craig@craig-desktop:~$ gconftool-2 --help
Usage:
  gconftool-2 [OPTION...] - Tool to manipulate a GConf configuration

Help Options:
  -?, --help                                     Show help options
  --help-all                                     Show all help options
  --help-client                                  Show client options
  --help-key-type                                Show key type options
  --help-load                                    Show load/save options
  --help-server                                  Show server options
  --help-install                                 Show installation options
  --help-test                                    Show test options
  --help-schema                                  Show schema options

Application Options:
  -v, --version                                  Print version

this is what happened what do i do now

---

### Post by P4man on 2009-08-13
you should enter those line per line.. not all at once :)

---

### Post by hairchin67 on 2009-08-13
i am still having the problem with my top and bottome panels. i have ubuntu, would doing a system restore help? how do i do that?

---

### Post by hairchin67 on 2009-08-13
i hav the panels in the main window, when i open a new window--they disappear again

---

### Post by wojox on 2009-08-13
Do you mean the workspace switcher?

---

### Post by hairchin67 on 2009-08-13
what is the workspace switcher? i am missing my top and bottom panels......apps, places, system, all launchers on top.. no bottom panel either.

---

### Post by wojox on 2009-08-13
> **hairchin67 said:**
> i hav the panels in the main window, when i open a new window--they disappear again

I don't understand? I thought you had them back. What new window are you opening?

---

### Post by hairchin67 on 2009-08-13
the panels come and go. how do i do a system restore with ubuntu? im used to windows.when i click on a new internet window, or when i open my home page, it maximizes and i lose my top and bottom panels.

---

### Post by wojox on 2009-08-13
No there is no system restore that I'm aware of anyway. Try right clicking on the panel when it loads on start up and choose properties and see if autohide is checked, if so uncheck it.

---

### Post by P4man on 2009-08-13
just to make sure.. you didnt set the panels to autohide, did you? If you move your mouse to the top of the screen, do the panels re-appear? Sorry if this is a silly suggestion, but .. well.. :)

---

### Post by hairchin67 on 2009-08-13
autohide is not on. i know, i thought that too. this is really beginning to upset me profoundly. the window seems to be covering up the panels. how do u resize the windows?

---

### Post by hairchin67 on 2009-08-13
when the window opens, there is no way to minimize the window without shutting down my session.

---

### Post by wojox on 2009-08-13
Open a terminal:

```
sudo apt-get update
```

```
sudo apt-get install --reinstall gnome-panel
```

---

### Post by P4man on 2009-08-13
you dont have window borders with minimize/ (un)maximize and close buttons?
You can normally just drag the window title bar to "snap" a window out of maximized state..(or press the middle of those buttons)  but Im getting pretty confused as to what you are seeing, perhaps posting a screenshot may help clarify?

---

### Post by hairchin67 on 2009-08-13
> **wojox said:**
> Open a terminal:

```
sudo apt-get update
```

```
sudo apt-get install --reinstall gnome-panel
```

i dit it but terminal says couldnt find package file

---

### Post by hairchin67 on 2009-08-13
> **hairchin67 said:**
> i dit it but terminal says couldnt find package file

i did gnome panel reinstall still have the issue. could it be firefox? how about reinstalling fire fox? this happened once before .

---

### Post by wojox on 2009-08-13
Ok found a little different way then before open terminal:

```
rm -rf ~/.gconf/apps/panel
```

```
killall gnome-panel
```

```
gnome-panel
```

Then reboot to take effect

---

### Post by matthewbpt on 2009-08-13
What ubuntu version are you using? In Hardy and for a while in Intrepid there was a firefox bug where it would cover and overlap the panels (I got this bug) But the bug is not present in the latest version of Ubuntu, "Jaunty Jackalope 9.04". Try pressing F11 twice, it's what I used to do before the bug was fixed, it toggles fullscreen mode. To find out what Ubuntu version you're running type the following in terminal

```
lsb_release -a
```

---

### Post by hairchin67 on 2009-08-13
hitting the f11 button twice works, thank you. we had this problem once b4 but it corrected itself. do u hav any problems with jauntyjackalope? would i be better off just keepin it this way?

---

### Post by hairchin67 on 2009-08-13
if i upgrade to jaunty jackolope 9.04, will all my files and settings b effective?

---

### Post by wojox on 2009-08-13
No I upgraded with no problem from 8.10. I thought you had jaunty 9.04. Sorry about that.

---

### Post by The Plainsman on 2009-09-28
I have the same problem, the top and bottom panels disappeared, but when I press alt+f2 nothing happens.  btw, if it matters, I am using the netbook remix.

---

