---
title: "Lost window title bar and min/max/close Buttons"
date: 2011-04-30
forum: General Help
---

### Post by Tony Flury on 2011-04-30
Just recently,on occassion when I log in to my main user, I don't get the Title Bars, or windows minimize, maximize, close buttons.

I have tried changing theme - this does not help.

I have noticed that running the "compiz" command from the main manu will restore the title bars etc, and that my second user (created yesterday) does not have that problem.

How can I diagnose what is going wrong ?

---

### Post by Tony Flury on 2011-05-01
sorry to bump - any ideas from anyone ?

---

### Post by Tony Flury on 2011-05-03
Sorry for another bump.

I assume no-one has seen this before.

---

### Post by pAsM on 2011-05-03
Hello,
[INDENT]This can be fixed in the Gnome Config Editor.
 
1) Launch a terminal (note, do not use "sudo")
2) Type "gconf-editor" followed by the enter key (this will look almost like the registry editor on Windows)
3) Navigate to "/desktop/gnome/shell/windows"
4) Locate the key "button_layout" and change the value to ":minimize,maximize,close" (No quotes)
5) Exit the Gnome Config Editor
6) Press "ALT+F2" to bring up the run command
7) Enter the letter "r" followed by the enter key 
[/INDENT]

---

### Post by matt_symes on 2011-05-03
Hi

> Just recently,on occassion when I log in to my main user, I don't get the Title Bars, or windows minimize, maximize, close buttons.

What version are you using ?

For 10.04 and 10.10 (unsure about Unity).

I had the same issue myself a while ago on 10.04, but an update fixed it by itself so i never got around to diagnosing the problem.

Your window decorator is not starting or is crashing would be my guess.

You can verify this by typing

```
gtk-window-decorator --replace
```

instead of compiz replace. (or emerald if you use that). 

That might give you a starting point. Check your logs.

Kind regards

---

### Post by Tony Flury on 2011-05-03
> **pAsM said:**
> Hello,
[INDENT]This can be fixed in the Gnome Config Editor.
 
1) Launch a terminal (note, do not use "sudo")
2) Type "gconf-editor" followed by the enter key (this will look almost like the registry editor on Windows)
3) Navigate to "/desktop/gnome/shell/windows"

I don't have /desktop/gnome/shell - so i am unable to do any of the rest.
Part of the problem as well is that unti i run "compiz" to get the title bars back - i can open a terminal window - but not select it in order to type anything.

Thanks for trying to help though :-)

---

### Post by Tony Flury on 2011-05-03
> **matt_symes said:**
> Hi
What version are you using ?

For 10.04 and 10.10 (unsure about Unity).

I am on 10.04

> 
I had the same issue myself a while ago on 10.04, but an update fixed it by itself so i never got around to diagnosing the problem.

I have another user on the same PC - running the same version of Ubuntu - and that works fine - so i am guessing it is not a library issue.

> 
Your window decorator is not starting or is crashing would be my guess.

You can verify this by typing

```
gtk-window-decorator --replace
```

If I open a terminal window without the window decorations, I can't type anything in it. I will add a launcher  to the menu - and see if that fixes the issue next time i boot

> 
instead of compiz replace. (or emerald if you use that). 

That might give you a starting point. Check your logs.

Kind regards
Which logs ? Nothing in dmesg i can see indicating any sort of crash.

---

### Post by matt_symes on 2011-05-03
Hi

> If I open a terminal window without the window decorations, I can't type anything in it. I could still type things in, so i never had that issue. Just disappearing title bars and window decorations..

Can you type 

alt + F2 

when it happens and enter 

```
gtk-window-decorator --replace
```that way ? 

If it does not happen to your other user then compare and contrast your gconf and compiz settings to start with.

BTW: If anybody is using Unity, on Unity it seem to be 

```
unity-window-decorator --replace
```Kind regards

---

### Post by Tony Flury on 2011-05-03
> **matt_symes said:**
> Hi

I could still type things in, so i never had that issue. Just disappearing title bars and window decorations..

Can you type 

alt + F2 

when it happens and enter 

```
gtk-window-decorator --replace
```that way ? 

No - alt +F2 does not work - unless i re-enable the title bar etc - with my compiz menu thing.
Having the gtk command as a menu entry, and clicking that when the desktop appears does not work.

> 
If it does not happen to your other user then compare and contrast your gconf and compiz settings to start with.

Which settings files - i have never explored this area.

---

### Post by matt_symes on 2011-05-04
Hi

You could try to reset all your gconf settings. It will wipe out any customisations you have but it might fix the issue. 

Make a backup of your home directory first including all the hidden files and folders.

From the terminal.

```
gconftool-2 --recursive-unset /
```

If anybody else has other suggestions please chip in.

Kind regards

---

### Post by Tony Flury on 2011-05-04
> **matt_symes said:**
> Hi

You could try to reset all your gconf settings. It will wipe out any customisations you have but it might fix the issue. 

Make a backup of your home directory first including all the hidden files and folders.

From the terminal.

```
gconftool-2 --recursive-unset /
```

If anybody else has other suggestions please chip in.

Kind regards

Will try that as a last resort - I would like to find a log file which indicates what is actually failing in the first place - i don't understand the folder heirarchy well enough. Also whatever the problem is - running compiz from the menu (The launcher just executes "compiz" - no arguments) solves the problem - which suggests that the gnome config is ok - and that something else is failing to start.

---

### Post by matt_symes on 2011-05-04
Hi

If you want a log to look through have a look at .xsession-errors (that's <dot>xsession-errors) in your home directory. It's a hidden file.

Kind regards

---

### Post by Tony Flury on 2011-05-05
> **matt_symes said:**
> Hi

If you want a log to look through have a look at .xsession-errors (that's <dot>xsession-errors) in your home directory. It's a hidden file.

Kind regards

Ok - i have rigged things to save the .xsession-errors file before i start "compiz" i attach it here - i have looked through it and can't see anything obvious - another pair of eyes might spot something.

---

### Post by matt_symes on 2011-05-06
Hi 

I can't see much wrong with your .xsession-errors file apart from RingSensorsScreenlet but that should not cause the problem.

Do you still get the issue with Compiz switched off ? Does your second user have Compiz switched on ? 

Kind regards

---

### Post by bhanu860 on 2011-05-19
Hi

I had the same problem, fixed by re-installing the Compiz(Using Ubuntu Software Center, search for compiz and install)

---

