---
title: "Disable Unity greeter screen permanently"
date: 2012-03-31
forum: General Help
---

### Post by iwaytalks on 2012-03-31
I am currently running an arm port of Ubuntu Oneiric on a Imx board.
My plan is to replace unity and start my custom application using lightdm and to avoid the use of login greeter screen completely. 

I did the following modifications, explained in detail below 
1) Created a custom session 
2) Enable autologin


1) Modified existing xsession ubuntu.desktop in /usr/share/xsessions/ folder. Changed file contents:

[INDENT]    [Desktop Entry]
    Name=ubuntu
    Comment=This logs you into a Customized session
    Exec=gnome-terminal
    Icon=
    Type=Application
[/INDENT]
Temporarily using gnome-terminal as my default app

2) Modified /etc/lightdm/lightdm.conf file to enable autologin and changed the autologin session (auto login session never works though due to the ~/.dmrc problem). Below are the contents of the modified conf file.

[INDENT]    [SeatDefaults] 
    greeter-session=unity-greeter
    user-session=ubuntu
    autologin-user=user1
    autologin-user-timeout=0
    autologin-session=ubuntu
    allow-guest=false
[/INDENT]

Autologin to the customsession after power cycle is working fine. But when I type exit in terminal (note : gnome-terminal is my current default app for new session) I endup in the greeter screen. 

Is it possible to disable login greeter screen completely and autologin / respawn the previous session when the currently running session terminates ? 

Thought of using a script with a conditional loop to restart my app if it terminates, but I personally disliked the idea :-( . Do we have any way to achieve this?

---

