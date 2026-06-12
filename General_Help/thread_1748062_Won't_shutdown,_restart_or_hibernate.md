---
title: "Won't shutdown, restart or hibernate"
date: 2011-05-03
forum: General Help
---

### Post by Lockheed on 2011-05-03
Whatever I do, I can't get my linux to reboot, shutdown or hibernate.

Here is some new info:

I am using stripped down xfce4 with compiz and emerald. 

Here's my .xinitrc
```
cairo-dock &
xfdesktop &
/home/juha/bin/startup.sh &
exec ck-launch-session compiz ccp

```

and my startup script
```

sh -c "sleep 5 && wicd-client" &
sh -c "python2 -u /usr/share/screenlets/Radio/RadioScreenlet.py" &
sh -c "python2 -u /home/juha/.screenlets/NowCalendar/NowCalendarScreenlet.py" &
sh -c "python2 -u /usr/share/screenlets/Tomboy/TomboyScreenlet.py" &
sh -c "xbindkeys" &
sh -c "xfce4-volumed" &  
sh -c "sleep 25 && conky" &
while true; do emerald --replace; sleep 1; done &

```

1. My login manager is SLIM which I use to autologin.
```
# Path, X server and arguments (if needed)
# Note: -xauth $authfile is automatically appended
default_path        /bin:/usr/bin:/usr/local/bin
default_xserver     /usr/bin/X
xserver_arguments   -nolisten tcp vt07

# Commands for halt, login, etc.
halt_cmd            /sbin/shutdown -h now
reboot_cmd          /sbin/shutdown -r now
console_cmd         /usr/bin/xterm -C -fg white -bg black +sb -T "Console login" -e /bin/sh -c "/bin/cat /etc/issue; exec /bin/login"
#suspend_cmd        /usr/sbin/suspend

# Full path to the xauth binary
xauth_path         /usr/bin/xauth 

# Xauth file for server
authfile           /var/run/slim.auth


# Activate numlock when slim starts. Valid values: on|off
# numlock             on

# Hide the mouse cursor (note: does not work with some WMs).
# Valid values: true|false
# hidecursor          false

# This command is executed after a succesful login.
# you can place the %session and %theme variables
# to handle launching of specific commands in .xinitrc
# depending of chosen session and slim theme
#
# NOTE: if your system does not have bash you need
# to adjust the command according to your preferred shell,
# i.e. for freebsd use:
# login_cmd           exec /bin/sh - ~/.xinitrc %session
login_cmd           exec /bin/bash -login ~/.xinitrc %session

# Commands executed when starting and exiting a session.
# They can be used for registering a X11 session with
# sessreg. You can use the %user variable
#
# sessionstart_cmd    some command
# sessionstop_cmd    some command

# Start in daemon mode. Valid values: yes | no
# Note that this can be overriden by the command line
# options "-d" and "-nodaemon"
# daemon    yes

# Available sessions (first one is the default).
# The current chosen session name is replaced in the login_cmd
# above, so your login command can handle different sessions.
# see the xinitrc.sample file shipped with slim sources
sessions            xfce4,icewm,wmaker,blackbox

# Executed when pressing F11 (requires imagemagick)
screenshot_cmd      import -window root /slim.png

# welcome message. Available variables: %host, %domain
welcome_msg         Welcome to %host

# Session message. Prepended to the session name when pressing F1
# session_msg         Session: 

# shutdown / reboot messages
shutdown_msg       The system is halting...
reboot_msg         The system is rebooting...

# default user, leave blank or remove this line
# for avoid pre-loading the username.
default_user        juha

# Focus the password field on start when default_user is set
# Set to "yes" to enable this feature
#focus_password      no

# Automatically login the default user (without entering
# the password. Set to "yes" to enable this feature
auto_login          yes


# current theme, use comma separated list to specify a set to 
# randomly choose from
current_theme       default

# Lock file
lockfile            /var/lock/slim.lock

# Log file
logfile             /var/log/slim.log (doesn't contain anything useful)

```





2. ```
$ ck-list-sessions
Session2:
    unix-user = '1001'
    realname = '(null)'
    seat = 'Seat1'
    session-type = ''
    active = TRUE
    x11-display = ':0.0'
    x11-display-device = '/dev/tty7'
    display-device = ''
    remote-host-name = ''
    is-local = TRUE
    on-since = '2011-05-02T07:37:59.343950Z'
    login-session-id = '1'
Session1:
    unix-user = '1001'
    realname = '(null)'
    seat = 'Seat2'
    session-type = ''
    active = FALSE
    x11-display = ':0.0'
    x11-display-device = ''
    display-device = ''
    remote-host-name = ''
    is-local = TRUE
    on-since = '2011-05-02T07:37:58.783769Z'
    login-session-id = '1'

```

3. Here is what happens when I try to reboot with the .xinitrc file I published above - it freezes on console login screen:
[http://www.youtube.com/watch?v=21NWeOvGwic](http://www.youtube.com/watch?v=21NWeOvGwic)

4. Here is what happens if I change the .xinitrc file to this:
```
#!/bin/sh
exec ck-launch-session dbus-launch --sh-syntax --exit-with-session /home/juha/.xstart

```
and script file:
```
#!/bin/sh
pcmanfm --desktop &
compiz ccp &
sh -c "python2 -u /usr/share/screenlets/Radio/RadioScreenlet.py" &
sh -c "python2 -u /home/juha/.screenlets/NowCalendar/NowCalendarScreenlet.py" &
sh -c "python2 -u /usr/share/screenlets/Tomboy/TomboyScreenlet.py" &
sh -c "xbindkeys" &
sh -c "xfce4-volumed" &  
sh -c "sleep 5 && conky" &
emerald --replace &
cairo-dock
```

It won't even login:
[http://www.youtube.com/watch?v=WzIjnbcocD4](http://www.youtube.com/watch?v=WzIjnbcocD4)

Help!

---

### Post by Lockheed on 2011-05-05
bump

---

### Post by Lockheed on 2011-05-08
bump2

---

### Post by Merenguey on 2012-04-17
Hi,


Same trouble for me : the "ck-list-session" command shows me two sessions opened - whereas I have only one.

So I can't GUI shutdown, nor reboot nor logout. I only can by doing "sudo shutdown -h now" through the terminal.

Anyone's an idea? 


Cheers

---

