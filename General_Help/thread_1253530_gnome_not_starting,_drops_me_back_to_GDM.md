---
title: "gnome not starting, drops me back to GDM"
date: 2009-08-30
forum: General Help
---

### Post by novey on 2009-08-30
Hiya all, i recently updated from a pretty much unused 8.10 to the latest. 

gnome was working ok, i was setting up synergy server via the GDM scripts but have ince removed those settings and just added it to the startup through the gnome menus.

i also installed KDE to try out, which started ok, and still does. 

the problem is that now gnome doesnt start, it gives the error
[I]'Your session only lasted less than 10 seconds. If you have note logged out yourself,this could meant that there is some installing problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem'
[/I]this error pops up pretty much instantly and only gives an "OK" to click which drops me back to the GDM. 

Logging into a gnome failsafe session works fine however isnt a long term solution

.xsession-errors : 
> 
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
the xsession errors doesnt ive me anything much to go on as you can see, does anyone have a suggestion on how to fix this? or where / how i can get more info on what exactly is going wrong?

any help greatly appreciated.

---

### Post by SuaSwe on 2009-08-30
Have you checked to make sure that you aren't out of diskspace?

```

df -h

```

Also, your syslog might help tell you what's going on with it. :)

---

### Post by novey on 2009-08-30
indeed i have checked disk space, 17% used. 

Info i probly should have mentioned its Ubuntu 8.10 64bit that was upgraded to 9.04. 
running on a couple of xeon quads, geforce 9800gtx. 

i just rebooted, tried logging in normaly and got the same message heres the errors in the syslog at about the time i tried logging in. 

> 
Aug 30 13:27:48 yang console-kit-daemon[5652]: WARNING: Couldn't read /proc/5651/environ: Failed to open file '/proc/5651/environ': No such file or directory 
Aug 30 13:27:50 yang gdm[6502]: Gtk-WARNING: Ignoring the separator setting 
Aug 30 13:27:53 yang acpid: client 5923[0:0] has disconnected 
Aug 30 13:27:53 yang acpid: client 5923[0:0] has disconnected 
Aug 30 13:27:53 yang acpid: client connected from 6558[0:0] 
Aug 30 13:27:54 yang acpid: client connected from 6558[0:0] 
Aug 30 13:27:55 yang kernel: [   36.256507] eth1: no IPv6 routers present
Aug 30 13:28:08 yang gdm[5918]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Aug 30 13:28:08 yang gdm[5918]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Aug 30 13:28:08 yang gdm[6612]: Gtk-WARNING: Ignoring the separator setting 
Aug 30 13:28:13 yang Synergy 1.3.1: NOTE: synergys.cpp,500: started server
Aug 30 13:28:13 yang pulseaudio[6775]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Aug 30 13:28:13 yang pulseaudio[6775]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Aug 30 13:28:13 yang pulseaudio[6775]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Aug 30 13:28:14 yang pulseaudio[6807]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Aug 30 13:28:14 yang pulseaudio[6807]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Aug 30 13:28:14 yang pulseaudio[6807]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Aug 30 13:28:15 yang pulseaudio[6826]: pid.c: Daemon already running.
Aug 30 13:28:52 yang Synergy 1.3.1: NOTE: CClientListener.cpp,127: accepted client connection
Aug 30 13:28:52 yang Synergy 1.3.1: NOTE: CServer.cpp,278: client "yin" has connected


---

### Post by novey on 2009-08-31
still got this problem :(

i found that i can set debug in gdmsetup so heres a syslog for a failed attempt with debug on:

> Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling message: 'QUERYLOGIN 5918 daniel' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Got QUERYLOGIN daniel 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling message: 'LOGGED_IN 5918 1' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Got logged in == TRUE 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling message: 'LOGIN 5918 daniel' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Got LOGIN == daniel 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling message: 'GREETPID 5918 0' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Got GREETPID == 0 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling message: 'WRITE_X_SERVERS 5918 0' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling message: 'SESSPID 5918 14225' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Got SESSPID == 14225 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: gdm_socket_handler: Accepting new connection fd 7 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling user message: 'VERSION' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling user message: 'GET_CONFIG greeter/GraphicalThemedColor :0' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling GET_CONFIG: greeter/GraphicalThemedColor for display :0 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Looking up per display value for greeter/GraphicalThemedColor 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: greeter/GraphicalThemedColor 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: greeter/GraphicalThemedColor 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Requesting group=greeter key=GraphicalThemedColor locale=(null) 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Looking up key: greeter/GraphicalThemedColor 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: greeter/GraphicalThemedColor 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling user message: 'CLOSE' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Handling message: 'opcode=SHOW_ERROR_DIALOG$$pid=5918$$type=1$$error_msg=Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space.  Try logging in with one of the failsafe sessions to see if you can fix this problem.$$details_label=View details (~/.xsession-errors file)$$details_file=/home/daniel/.xsession-errors$$uid=0$$gid=0' 
Aug 30 15:33:05 yang gdm[5915]: DEBUG: Forking extra process: error dialog 
Aug 30 15:33:05 yang gdm[14335]: DEBUG: Attempting to parse key string: xdmcp/Enable=false 
Aug 30 15:33:05 yang gdm[14335]: DEBUG: Attempting to parse key string: daemon/User=gdm 
Aug 30 15:33:05 yang last message repeated 3 times
Aug 30 15:33:05 yang gdm[14335]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm 
Aug 30 15:33:05 yang gdm[14335]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm 
Aug 30 15:33:05 yang gdm[14335]: DEBUG: Attempting to parse key string: daemon/AddGtkModules=false 
Aug 30 15:33:05 yang gdm[14335]: DEBUG: Attempting to parse key string: gui/GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc 
Aug 30 15:33:05 yang gdm[14335]: DEBUG: Attempting to parse key string: gui/GtkTheme=Default 
Aug 30 15:33:05 yang gdm[14335]: Gtk-WARNING: Ignoring the separator setting 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: mainloop_sig_callback: Got signal 17 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Handling message: 'SESSPID 5918 0' 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Got SESSPID == 0 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Handling message: 'LOGGED_IN 5918 0' 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Got logged in == FALSE 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Handling message: 'LOGIN 5918 ' 
Aug 30 15:33:06 yang gdm[5915]: DEBUG: Got LOGIN ==  

---

### Post by novey on 2009-09-01
bump, still not working. still cant see any errors in logs thats of any use, can someone help me, tried googling any suspicious looking log lines with no joy. 

could someone suggest any way to get more info on whats going wrong ? 

thanks.

---

