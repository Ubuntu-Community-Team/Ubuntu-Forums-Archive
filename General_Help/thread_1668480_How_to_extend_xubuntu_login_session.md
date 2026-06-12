---
title: "How to extend xubuntu login session"
date: 2011-01-16
forum: General Help
---

### Post by artful2 on 2011-01-16
I'm running xubuntu 10.10 on an old toshiba P3 laptop and I'm very new to linux but am learning day by day. How can I either extend the login session or stop it auto logging me out as I want to leave a program running continuously. I've searched all over the web but can't find anything.

---

### Post by ajgreeny on 2011-01-16
Can you give more details of this "auto-logout" please.  I think you may simply have a  a screensaver or power-management setting that asks for a password when you return to use the mouse or keyboard.  I have never heard of any form of auto-logout in a default install.

I am not totally familiar with xubuntu, so I can not give you more details, but have a look somewhere in the System->Preferences menu.

---

### Post by ajgreeny on 2011-01-16
This double post problem has improved a lot, but obviously not gone away completely!

---

### Post by efflandt on 2011-01-16
Is it actually logging you out, or you just think it is logging you out because the default requires you to enter your password when it goes into screensaver mode?  Screensaver mode should not stop programs that are running, but they will stop if your computer goes into suspend or hibernate.

Check your Screensaver and Power Management settings.

---

### Post by artful2 on 2011-01-16
I haven't set a screensaver, however I did initially try to set one up but there is a bug reported elsewhere that crashes the session when I attempt to. The first time this caused a problem was doing an xubuntu update after first install. I went off for a cupa after starting it off and when I returned the screen was black. I moved the mouse and the xfce login screen appeared. The update had not finished - on restarting the update it went through a recovery following a partial update which I then completed. In the power settings I have the monitor to sleep after 30 mins (max is 60) and switch off after 50 (the max) when on AC power - it's a Toshiba Portege 7220 laptop. I have "never" set for putting the PC to sleep and "nothing" set for when the laptop lid is closed.

The screen goes black after exactly 10 mins of inactivity but I have not altered any settings anywhere for this.

I have auto login set up which works fine when first booted.

Could this be connected to the screensaver bug? I can't select the option because it crashes the session but is there a configuration file I can edit manually to make sure it's not set.

I've spent time every night for a week trying to sort this and got nowhere so any help would be greatly appreciated.

PS. there's no screen timeout in the BIOS either, I've checked that already.

On further testing:
After 10 mins of inactivity the Xfce login screen appears. After a further 5 minutes the screen goes blank.

---

### Post by artful2 on 2011-01-17
I've now resolved this problem which is totally related to an issue with xscreensaver.

On this P3 laptop the xscreensaver setup will not run, crashing to the login screen. By default the screensaver is set to start after 10 minutes - this I discovered by reading the .xscreensaver file in the home folder. Editing this manually and setting the mode variable to "off" disables the screensaver and solves the problem.

Running the screensaver setup manually (executing xscreensaver-demo in Terminal) also crashes to the login screen so there is obviously a hardware dependant bug in this program.

Is it possible to remove the X11 xscreensaver package from the installation without any detrimental effect?

---

