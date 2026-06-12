---
title: "install and use a theme in emerald theme manager"
date: 2010-08-15
forum: General Help
---

### Post by Affrikka on 2010-08-15
Hey all,

I installed a theme in emerald, and it didn't do anything, like, it had no effect on my windows or anything. So i did some searching and the only thing i could find was to run "emerald --replace" in the terminal, and it worked, but if I exit out of the terminal, it reverts back to the old theme.

How do I keep emerald's theme, even after I exit the terminal?


thanks!


Mathieu


--running 10.04

---

### Post by WorMzy on 2010-08-15
If you ahven't already done so, install ccsm ```
sudo apt-get install ccsm
``` run that (Alt+F2, ccsm, run), and enable the Window Decoration plugin (should be about half-way down the list).

Enter the plugin's settings by clicking on it, and set the command to "emerald --replace". If the effects aren't immediate, then press Alt+F2 again, and run "compiz --replace"

If that works, then press Alt+F2, and run "gconf-editor". In this application browse to /desktop/gnome/applications/window_manager/default and set it to ```
/usr/bin/compiz
``` Then browse to /desktop/gnome/session/required_components/windowmanager and set it to the same thing.

That should make it so that you get your window decoration every time you boot into Ubuntu, instead of having to run a command every time.

If anything goes wrong, then you can restore the original window decoration by running ```
metacity --replace
```

---

### Post by Affrikka on 2010-08-15
awesome, thanks so much for the quick reply and the great instructions, everything worked for me and now i have an awesome new theme ^^

thanks again!!


Mathieu

---

### Post by cro_409 on 2010-08-18
Hey, 

I as well am having an issue with the emerald themes, but this solution didn't work so well for me. I have Emerald Theme Manager v.0.7.2 and CompizConfig Settings Manager. The "emerald --replace" code didn't work, so I double checked that the Windows Decorator Plug-in was enabled and then tried the steps to the "compiz --replace" After that I lost the top bar with the close/min/max buttons, so tried to do the fix with "metacity --replace" but was unable to type, leading to forced reboot pressing the power button on the tower since I couldn't get the off button in the corner to work. Am I missing a step or a program? And why hasn't an APPLY button been added to Emerald yet? It's been like this since my friend first showed me Ubuntu a few years ago. I love Ubuntu, much more than Windows, but in Windows you rarely use the terminal, especially for simple processes as applying a change.

Thank you in advance for the help.

---

### Post by snip3r8 on 2010-08-20
> **cro_409 said:**
> Hey, 

I as well am having an issue with the emerald themes, but this solution didn't work so well for me. I have Emerald Theme Manager v.0.7.2 and CompizConfig Settings Manager. The "emerald --replace" code didn't work, so I double checked that the Windows Decorator Plug-in was enabled and then tried the steps to the "compiz --replace" After that I lost the top bar with the close/min/max buttons, so tried to do the fix with "metacity --replace" but was unable to type, leading to forced reboot pressing the power button on the tower since I couldn't get the off button in the corner to work. Am I missing a step or a program? And why hasn't an APPLY button been added to Emerald yet? It's been like this since my friend first showed me Ubuntu a few years ago. I love Ubuntu, much more than Windows, but in Windows you rarely use the terminal, especially for simple processes as applying a change.

Thank you in advance for the help.

make sure there is a space between "emerald" and "--replace"

---

### Post by WorMzy on 2010-08-20
Next time, instead of using the run dialogue to run the commands, use a terminal (Applications -> Accessories -> Terminal). It'll report any problems which may be stopping the various commands working. Once a command is running in a terminal, you can press Ctrl+C to stop it. Beware that stopping a window manager that's running in a terminal may make it difficult to run any other commands, so you may want to add the "Run Application" applet to your gnome-panel, it lets you bring up the run dialogue even when the shortcut doesn't work. 

Also, make sure you have the gnome-compatibility plugin enabled in ccsm. And check that you have graphics drivers installed.

---

