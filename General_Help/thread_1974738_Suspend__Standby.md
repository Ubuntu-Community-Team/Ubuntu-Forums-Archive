---
title: "Suspend / Standby"
date: 2012-05-06
forum: General Help
---

### Post by iranai on 2012-05-06
Running a desktop with 12.04.  The only shutdown / power management options I have are Suspend, Restart, and Shutdown. I do not have any Standby, Hibernate or Sleep options.     

Issue: When I do a Suspend, the system saves my state and powers down fully. However, moving the mouse, clicking a button etc. does not wake it back up. To wake it back up, I have to press the PC power button.  My PC then goes through post and as long as I select my Ubuntu install in the grub, it will come back up. I am hoping to have an option like Standby in Windows.

---

### Post by codingman on 2012-05-06
suspend IS standby, only it is called suspend in linux. Are you sure you are pressing suspend?

---

### Post by iranai on 2012-05-06
> **codingman said:**
> suspend IS standby, only it is called suspend in linux. Are you sure you are pressing suspend?

That's what I thought and yes, I am clicking on Suspend.  It seems to be acting like Hibernate which I do not have in my menu or power management settings.  If I knew what packages Suspend are a part of I'd do a reinstall via synaptic. Otherwise I'm at a loss.  I have been upgrading since 9.04, maybe its time for a fresh install as I get an error running: 
```
sudo dpkg-reconfigure -a
```

Error is:
** (accounts-daemon:26078): WARNING **: Failed to acquire org.freedesktop.Accounts
** (accounts-daemon:26078): WARNING **: Could not acquire name

---

### Post by grahammechanical on 2012-05-06
If you go to the Ubuntu Desktop Guide (Help) under Power & battery and then scroll down to Problems and select Why won't my computer turn back on after I suspended it, You will see this:

> This could be because suspend and hibernate aren't properly supported by your hardware

and

> try pressing the power button (don't hold it in, just press it once).

If you then click the link to hibernate at the top of the page, you will see this:

> Unfortunately, hibernate doesn't work in many cases with Ubuntu, which can cause you to lose data if you expect your documents and applications to re-open when you switch your computer back on. Therefore, hibernate is disabled by default in Ubuntu 12.04.

Regards.

---

### Post by iranai on 2012-05-06
> **grahammechanical said:**
> If you go to the Ubuntu Desktop Guide (Help) under Power & battery and then scroll down to Problems and select Why won't my computer turn back on after I suspended it, You will see this: ... 

Okay I took a look at that help doc.

I have a dual boot system with Win7 and Standby works fine in that OS so I very much doubt its a hardware issue.  It's more likely that upgrading every revision from 9.04 has overwritten/removed something needed.  When I click on Suspend, it shows a text screen then ubuntu load screen and finally it fully turns off the power (as if going into hibernation). In Win7 my mouse and case light will blink every few seconds showing it is in Standby.  Thus, it may be that my PC is actually going to hibernation and not suspend.  On the case, I have to just press and release the power button to have it come back on, but it goes through the whole POST and Grub process (again not something the Suspend sleep mode is supposed to do).

I will try to suspend the machine from the terminal instead of the system menu and see what that does.

EDIT: Running[COLOR=Black] sudo pm-suspend just puts it to sleep with the click of the fingers. I still need to click to press the power button to have it come back on, but it is then up right where I left it (no post, no grub, no login screen as if I click suspend in system menu and then turn it back on).  Now I am sure that Suspend in my system menu actually runs a type of sudo pm-hibernate command.  So how do I fix that at least? 
[/COLOR]According to the help file I can enable hibernate by doing the following, but there is nothing in the surrounding folders/files that have anything to do with Suspend. :(
[COLOR=Black]
[/COLOR] [COLOR=Black][FONT=sans-serif]Enable hibernate
If the hibernate test works, you can continue to use the sudo pm-hibernate command when you want to hibernate.
You can also enable the hibernate option in the menus. To do that, use your favorite text editor to create /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla. Add the following to the file and save:
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes[/FONT][/COLOR][COLOR=Black]
[/COLOR]

---

