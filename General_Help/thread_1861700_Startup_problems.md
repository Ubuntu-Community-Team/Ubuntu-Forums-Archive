---
title: "Startup problems"
date: 2011-10-15
forum: General Help
---

### Post by Samlboss on 2011-10-15
Hey. I just installed ubuntu 11.10, and I'm having some startup problems. The problem being that it's stuck in terminal mode and I don't know what's wrong. I hope someone here has had the same problem and can help me fix it because right now it's just kinda useless...

---

### Post by drs305 on 2011-10-15
We need some more information. Is it a "grub" or "grub-rescue" prompt, or is the system booting to a login prompt?

Have you tried booting to the recovery mode? If you don't see the Grub menu, try holding down the SHIFT key during the boot until the menu appears.

If you see any error messages during the boot please tell us what they are (if you can). What is the last thing you see before the boot stops (splash screen, error message, etc).

---

### Post by Samlboss on 2011-10-15
I just started it up, and it brings me to another terminal login and it says:
*Stopping automatic crash report generation [fail]
*Starting LightDM Display Manager [fail]

I think it has to do something with this. I'm sorry if it's not enough information. I'm not really good with this. Hopefully this is enough information

---

### Post by penguinslide on 2011-10-16
Hi, hope you don't mind me getting on this thread too, I may have a similar problem after upgrading to 11.10, mine goes to splash and stays there, have waited as long as 12 hrs for it to change, never does. I hit esc and gives me a big screen of details, the last few lines are:

Stopping user space bootsplash
Stopping flush boot log to disk
Startings CUPS printing spooler/server

Have tried the recovery option, that fails too, am messaging from back up hd

---

### Post by fixerdave on 2011-10-16
> **Samlboss said:**
> I just started it up, and it brings me to another terminal login and it says:
*Stopping automatic crash report generation [fail]
*Starting LightDM Display Manager [fail]

I think it has to do something with this. I'm sorry if it's not enough information. I'm not really good with this. Hopefully this is enough information


You can probably get to a working console via the cntrl-alt-F1 key (cntrl-alt-F7 to get back) and logging in.  From there, you will likely get to deal with video driver hell - from the command line.  Can't say any more without specific info, and my answers would probably be less useful than what you can get by searching these forums.  If it's any consolation, I had to use a liveCD to downgrade grub so I could see it, only to end up at a screen like yours.  From there, I had to install the "xorg edgers" ppa (search for it if that's where you need to go) and install their nvidia drivers.  Works fine now, but no fun getting there.

---

### Post by drs305 on 2011-10-16
*lightdm* is Ubuntu's display manager, and it appears that is where the problem lies. I can't offer much expertise in this area, but you might try booting the Recovery mode from the Grub menu and then reinstall that package:```

sudo apt-get install --reinstall lightdm
```

Another thing you could attempt although I wouldn't think this would have much chance = if you are at a normal prompt you could try again to start it:```

sudo service lightdm start
*or*
sudo service lightdm restart
```

---

### Post by Samlboss on 2011-10-16
Now it says:
Starting load fallback graphics devices [fail]

---

