---
title: "Urgent: Is there a hot key for shutting down a program in Kubuntu?"
date: 2009-08-03
forum: General Help
---

### Post by NinjaNumberNine on 2009-08-03
Hi, I need some help quick. Just have a few minutes. Does anyone know the keyboard shortcut for terminating an app in Kubuntu? (Jaunty Jackalope with KDE 4.2)

 Thanks in advance!

Addition: Alt-F4 does not work (it is an installer running through WINE with a full screen background, the installer goes on but the blue background stays on top of everything else. I tried alt-f3, but none of those options worked either. I need something that TERMINATES the apps.) Thanks again!

---

### Post by jocampo on 2009-08-03
By default, console switching is done using Alt-Fn or Ctrl-Alt-Fn. Still, is not working for you? I'm afraid you will have to reboot if your machine is so unresponsive

---

### Post by tjwoosta on 2009-08-03
you can bind the command xkill to any keybinding you want, then you can just press the keybinding and click on the window that you want to kill

---

### Post by jocampo on 2009-08-03
> **tjwoosta said:**
> you can bind the command xkill to any keybinding you want, then you can just press the keybinding and click on the window that you want to kill

Sweet! I was aware of xkill but did not know you can assign a specific key to it. Can you describe the process?

---

### Post by NinjaNumberNine on 2009-08-03
Thanks for replies. I somehow got this working- when I did alt-tab it showed the other windows fine, but when I let go on the one I wanted, the blue screen swallowed it up. What I ended up doing is as the programs scaled back to view I hit enter really quick to complete the installation- before the blue screen (typical of an MS program) could eat the dialog box. Thanks for your replies, and hope this helps someone else!

---

### Post by NinjaNumberNine on 2009-08-03
> Can you describe the process?
I'd like to know that too.

---

### Post by djurny on 2009-08-03
what about ctrl-Q ?

---

### Post by tjwoosta on 2009-08-03
> **jocampo said:**
> Sweet! I was aware of xkill but did not know you can assign a specific key to it. Can you describe the process?

Well I'm not really familiar with KDE, but I know its possible. The link I provided might help. If not just try searching google for "keyboard shortcuts kde" or something along those lines

[http://www.scottklarr.com/topic/25/linux-how-to-setup-custom-shortcuts-in-kde/](http://www.scottklarr.com/topic/25/linux-how-to-setup-custom-shortcuts-in-kde/)

---

### Post by Locutus_of_Borg on 2009-08-03
kde 4.2 keyboard shortcuts can be added by opening System Settings from your Kmenu thing and going to Input Actions, then right clicking under the "Configure Hotkey Settings" and selecting new global shortcut > Command/URL

---

### Post by NinjaNumberNine on 2009-08-03
Thanks, that is what I wanted! :D

---

### Post by Zorael on 2009-08-04
Um, I think xkill is bound to ctrl+alt+esc per default, and ctrl+esc should open up a list of processes much like the task manager in Windows. May be the other way around.

I'm not sure if xkill sends the terminate or the kill signal though. Likely the former, so you just might need to switch to a console and kill the process manually (with **-9**) if it doesn't respond to that.
```
$ killall firefox-bin **-9**
```

---

### Post by jocampo on 2009-08-04
> **Zorael said:**
> Um, I think xkill is bound to ctrl+alt+esc per default, and ctrl+esc should open up a list of processes much like the task manager in Windows. May be the other way around.

I'm not sure if xkill sends the terminate or the kill signal though. Likely the former, so you just might need to switch to a console and kill the process manually (with **-9**) if it doesn't respond to that.
```
$ killall firefox-bin **-9**
```

Well, I tried both shortcuts on my Gnome (Ubuntu Jaunty) and did not work. Also, how you suppose to switch to console when PC is so unresponsive? Ubuntu in general terms is really stable but I've had 2 times that was frozen and even switching to consoles was unsuccessful.   

Folks?
I tried on Gnome assigning a keyboard shorcut to xkill (ALT-Q) and problem is that then I had no way to revert that back, like a cancel switch. What is the cancel key for a shortcut, ESC? I also tried that and was forced to "xkill" something in order to cancel the command.

---

### Post by Zorael on 2009-08-04
I'm not sure what the GNOME equavilent is - the environment the OP had in mind was KDE, as far as I understand.

Now that I'm at my netbook I can verify the naming; Ctrl+Esc brings up the System Activity window, and Ctrl+Alt+Esc runs xkill, which changes the cursor into a skull-and-crossbones. Clicking on an app at this point kills it. Esc successfully cancels it here, though if I run xkill in a terminal I have to ctrl+c to cancel.

If your machine is so unresponsive that you can't switch to a console with ctrl+alt+f*n*, then I guess the only way to recover is to use another machine to ssh in and try to kill the process from there. I've had this happen once or twice, and Firefox has always been the culprit for me.

If you have zapping enabled (ctrl+alt+backspace) that's an option too, though only marginally better than sysrq+reisub, or holding down the power button.

---

### Post by jocampo on 2009-08-04
> **Zorael said:**
> 
If your machine is so unresponsive that you can't switch to a console with ctrl+alt+f*n*, then I guess the only way to recover is to use another machine to ssh in and try to kill the process from there. I've had this happen once or twice, and Firefox has always been the culprit for me.

True! the 2 or 3 times that i had problems was because Firefox. Anyway ... I'll check at home on my Ubuntu and see what the options are when you are running Gnome.

By the way, I tried Kubuntu and do not like it. Gnome is cleaner in my opinion. I also resuscitated an old desktop at home and is running Xubuntu now; I like it. Clean look and the terminal or console has an additional button that lets you minimize but not to the taskbar ... it just make it look like a thin line. I can not find that option on my Gnome and I want it ... :D ... that way, you can keep several consoles opened on your desktop and they are NOT on the taskbar, they are there but reduced to a thin line look...

---

### Post by Zorael on 2009-08-04
> **jocampo said:**
> By the way, I tried Kubuntu and do not like it. Gnome is cleaner in my opinion. I also resuscitated an old desktop at home and is running Xubuntu now; I like it. Clean look and the terminal or console has an additional button that lets you minimize but not to the taskbar ... it just make it look like a thin line. I can not find that option on my Gnome and I want it ... :D ... that way, you can keep several consoles opened on your desktop and they are NOT on the taskbar, they are there but reduced to a thin line look...
Have you tried Yakuake?

Random Google image hit: [http://yakuake.uv.ro/wp-images/yakuake.jpg](http://yakuake.uv.ro/wp-images/yakuake.jpg)

</end tangent>

---

### Post by NinjaNumberNine on 2009-08-04
> Um, I think xkill is bound to ctrl+alt+esc per default, and ctrl+esc should open up a list of processes much like the task manager in Windows. May be the other way around.
Now you're talkin'!!
I liked system monitor right off for it's similarity to task manager :twisted:*hehehe*:twisted:
but I couldn't find the keyboard shortcut. Glad to find that out. Thanks Zorael!

---

### Post by NinjaNumberNine on 2009-09-26
> **Locutus_of_Borg said:**
> kde 4.2 keyboard shortcuts can be added by opening System Settings from your Kmenu thing and going to Input Actions, then right clicking under the "Configure Hotkey Settings" and selecting new global shortcut > Command/URL
It's easier in System Settings > Keyboard & Mouse > Standard Shortcuts (or Global Shortcuts) :)

---

