---
title: "Put display to sleep via key ?"
date: 2010-10-28
forum: General Help
---

### Post by MaximB on 2010-10-28
Hello !

My display is set to sleep after 30 minutes of inactivity.
When I go to sleep at night I don't want to wait 30 minutes for the monitor to shutdown, **is there any way I can use the keyboard (like a hotkey)** for :

1. Start my screensaver (when I go for 5-10 minutes afk for example).
2. Make the monitor go to sleep mode.

---

### Post by AndyCee on 2010-10-28
Sure there is.

If you're not using compiz, go to "System -> Preferences -> Keyboard Shortcuts". Click "Add" and you can add the following entry:

Name: Screensaver
Command: xdg-screensaver activate

Not sure about putting monitor to sleep.

---

### Post by MaximB on 2010-10-28
> **AndyCee said:**
> Sure there is.

If you're not using compiz, go to "System -> Preferences -> Keyboard Shortcuts". Click "Add" and you can add the following entry:

Name: Screensaver
Command: xdg-screensaver activate

Not sure about putting monitor to sleep.

Thanks, that really did the trick
Now I need to find a way to put the monitor on sleep mode.

---

### Post by matt_symes on 2010-10-28
Hi

xset dpms force suspend

standby, suspend, off, on

Kind regards

---

### Post by MaximB on 2010-10-28
> **matt_symes said:**
> Hi

xset dpms force suspend

standby, suspend, off, on

Kind regards

Can you please explain that in more detail ?

---

### Post by matt_symes on 2010-10-28
Hi 

Open a terminal and type

xset dpms force suspend

This will suspend your display. Press the space bar to wake the machine up

You can add this command as a button.

You also have the pm_suspend command to suspend your entire machine

Kind regards

---

### Post by WorMzy on 2010-10-28
Ctrl+Alt+L should lock the screen/activate screensaver.

And I always switch to tty8 (Ctrl+Alt+F8) when I go to bed, since my monitor is somewhat broken and takes ~20 minutes of constant button pressing to turn on.

---

### Post by MaximB on 2010-11-03
> **matt_symes said:**
> Hi 

Open a terminal and type

xset dpms force suspend

This will suspend your display. Press the space bar to wake the machine up

You can add this command as a button.

You also have the pm_suspend command to suspend your entire machine

Kind regards

It seems to be working but for some reason after 5 seconds of suspend it goes back to the screensaver mode.

---

### Post by matt_symes on 2010-11-03
Hi

Which one did you use xset or pm_suspend? And did they both do the same thing or were they different? They both work fine on my machine so i think some detective work is required. Type them from the terminal and see if you get the same behaviour.

Do you have anything like wake on LAN or other wake event set in the  BIOS or elsewhere?

Kind regards

---

### Post by MaximB on 2010-11-03
> **matt_symes said:**
> Hi

Which one did you use xset or pm_suspend? And did they both do the same thing or were they different? They both work fine on my machine so i think some detective work is required. Type them from the terminal and see if you get the same behaviour.

Do you have anything like wake on LAN or other wake event set in the  BIOS or elsewhere?

Kind regards

I used the "xset dpms force suspend" command as I only want to suspend the monitor, it doesn't give me any output on cli.
It just goes to "monitor suspend" and after 5 seconds it goes to "screensaver" mode.

I don't have any wake on LAN or other wake event set in the  BIOS or elsewhere (that I know of).

---

### Post by matt_symes on 2010-11-03
Hi

Try

xset dpms force standby

Does that give the same issue?

Kind regards

---

### Post by MaximB on 2010-11-03
> **matt_symes said:**
> Hi

Try

xset dpms force standby

Does that give the same issue?

Kind regards

Thanks, that actually seems to be working fine...

---

### Post by matt_symes on 2010-11-03
Hi

No problems. 

Mark this post as solved if it is solved.

If the screen saver does give you issues you can use

gnome-screensaver-command --inhibit

to stop it.

Kind regards

---

### Post by obscur156 on 2011-03-26
Working like a charm.
Thanks matt_symes

Best regards

---

### Post by apochry on 2011-04-24
> **matt_symes said:**
> Hi

xset dpms force suspend

standby, suspend, off, on

Kind regards

Hi,

all of the commands work fine for me, but aren't actually usable. When I press the shortcut keys (Ctrl+Alt+D in my case) the display goes to sleep and when I release them it wakes up. So, my laptop wants me to keep the keys pressed in order the display to be off... OR I have to try to release all the keys simultaneously... this is not quite easy, believe me. :P
I overcame this issue by assigning the command to single-key shortcut (to the help button on my laptop (= fn+f1), which is actually two-key combination, but considered as one by the machine, since the 'fn'-key does nothing pressed separately). Stupid machines... :P ...and now I'm happy!

Btw. my stupid machine is HP Pavilion dv2000 Series.

Thanks for the nice commands!

Regards,
Izzo

---

