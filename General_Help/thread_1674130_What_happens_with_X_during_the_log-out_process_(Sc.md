---
title: "What happens with X during the log-out process? (Screen jumbles and locks up.)"
date: 2011-01-23
forum: General Help
---

### Post by Th3Professor on 2011-01-23
What happens with X during the log-out process?

The reason I ask is because occasionally my screen graphics become jumbled and sometimes even lock up, though if I can quickly log out before things lock up then the log-out process actually corrects the jumbled screen and, from the log-in screen (and after logging back in), everything is back to normal.

However, if I don't log out in time, the jumbled screen leads to things locking up and I have to do a cold boot (hard reboot) of the computer.

I would like to know what happens during the log-out process, and if any of the X-related processes factor in how I might be able to implement a real quick means of logging out (the "ctrl-alt-f1" and similar shortcuts never work) or, better yet, if there's a way to entirely avoid having the screen jumble or computer lock-up.

Thanks!

---

### Post by Th3Professor on 2011-01-24
...

---

### Post by Verbeck on 2011-01-24
x is restarted when you logout
simply switching to a virtual console doesn't do the same but entering *sudo service gdm/kdm restart* in a vc would do it

---

### Post by Th3Professor on 2011-01-24
> **Verbeck said:**
> x is restarted when you logout
simply switching to a virtual console doesn't do the same but entering *sudo service gdm/kdm restart* in a vc would do it

Cool thanks. I had tried setting up "killall gnome-panel nautilus" as a quick-fix, and setting up a button to click on in the corner of the screen for somewhat-quick-easy access (though not really sure of a keyboard-shortcut) but that didn't really work anyway.

How could I set up "gdm restart" to work as a button-click (icon tray thing) or keyboard shortcut if it requires "sudo"?

---

### Post by Verbeck on 2011-01-25
just add the needed entry to the sudoers file and then you wont need to enter the password for sudo for that command
[I]
sudo EDITOR=nano visudo[/I]
add at the end of the file;
```

username ALL=(ALL) NOPASSWD: /etc/init.d/gdm

```(ctrl+X , then 'Y' to save the file)
after that, for a new launcher, use *sudo /etc/init.d/gdm restart* for the 'command' field

#sorry that i couldn't help much with the actual issue

---

### Post by Th3Professor on 2011-01-25
Thank you. I used a different text editor but went ahead and added that to the sudoers file. The updated button (in icon tray) now will come in handy.

Is there a keyboard shortcut, or perhaps a way to create one, for that action?

(In the event that the mouse starts behaving oddly but keyboard might still work.)

---

### Post by Verbeck on 2011-01-25
> **Th3Professor said:**
> 
Is there a keyboard shortcut, or perhaps a way to create one, for that action?


from option in system>preferences>keybord>layout tab, check ctrl+alt+backspace under 'key sequence to kill the x server'
(actually, then you wouldn't need to edit the sudoers file if you don't want to use an icon i suppose)

---

### Post by Th3Professor on 2011-01-25
Actually, I forgot about the menu-system-preferences-keyboard shortcuts option, I went ahead and did that, and just created one, like "<ctrl> <winkey> <esc>". Just tested it. It worked well.

It's odd that I'd even have to do that when the graphics or GPU or things gui-related start going on the fritz like jumbled display and locking up. It seems that if a simple log-out-and-back-in would put things back to normal, then it'd seem like there'd be some way to just bypass the whole quirky-graphics issue entirely. :confused:

---

### Post by Verbeck on 2011-01-25
> **Th3Professor said:**
>  It seems that if a simple log-out-and-back-in would put things back to normal, then it'd seem like there'd be some way to just bypass the whole quirky-graphics issue entirely. :confused:
you could start by looking at the Xorg.n.log files in /var/log for errors. i'm not sure that i'd be of much help though...

---

