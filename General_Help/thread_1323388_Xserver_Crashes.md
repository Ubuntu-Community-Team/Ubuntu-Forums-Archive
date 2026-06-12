---
title: "Xserver Crashes"
date: 2009-11-11
forum: General Help
---

### Post by Praveer on 2009-11-11
Hey. I'm running 9.04, and my problem is that x-server will randomly crash. It usually crashes when I'm doing important stuff :) Anyways, when I first installed 9.04 it didn't do it, but I can't seem to find out why it is happening.(I suspect it might have something to do with the theme, but I tried changing both the GDM and desktop themes, and it still happened) Here is the systemlog:

Nov 11 17:09:36 praveer-desktop gdmgreeter[3509]: WARNING: Theme broken: must have pam-message label! 
Nov 11 17:09:37 praveer-desktop console-kit-daemon[3104]: WARNING: Couldn't read /proc/3103/environ: Failed to open file '/proc/3103/environ': No such file or directory 
Nov 11 17:09:42 praveer-desktop x-session-manager[3972]: WARNING: Could not parse desktop file /home/praveer/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name' 
Nov 11 17:09:42 praveer-desktop x-session-manager[3972]: WARNING: could not read /home/praveer/.config/autostart/xfce4-settings-helper-autostart.desktop 
Nov 11 17:09:42 praveer-desktop x-session-manager[3972]: WARNING: Could not parse desktop file /home/praveer/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name' 
Nov 11 17:09:42 praveer-desktop x-session-manager[3972]: WARNING: could not read /home/praveer/.config/autostart/xfconf-migration-4.6.desktop 

Any help is greatly appreciated, thanks!

---

### Post by Giblet5 on 2009-11-11
What is a systemlog? Do you mean syslog?

Is there useful information in your $HOME/.xsession-errors file?

Can you post the Xorg log from a crash? (/var/log/Xorg.0.log.old perhaps)

---

### Post by Praveer on 2009-11-11
> **Giblet5 said:**
> What is a systemlog? Do you mean syslog?

Is there useful information in your $HOME/.xsession-errors file?

Can you post the Xorg log from a crash? (/var/log/Xorg.0.log.old perhaps)
Thanks for replying really fast!

Yeah, sorry, by systemlog I meant syslog. I don't know what you mean by the xsession-errors file, but I can post the full xorg.0 and syslogs. ~They are attached. 

The last crash happened at about 17:07:36, where in syslog you can see the warning I posted on my first post.


Thanks again! 

~One is a .txt, and one is a .odt

---

