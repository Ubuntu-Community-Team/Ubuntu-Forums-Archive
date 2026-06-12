---
title: "dbus-daemon rejected send messages every second"
date: 2010-11-09
forum: General Help
---

### Post by maphew on 2010-11-09
What does this error message in `/var/log/auth.log` mean? It's showing up at about a rate of 1 per second. My indicator applets are missing as are my status bar icons. The desktop icons are flashing on and off at a rate of about 1 per second. 

{{{
dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.1299" (uid=1000 pid=18184 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.7" (uid=0 pid=903 comm="/usr/sbin/console-kit-daemon))
}}}
(note the unbalanced quotes)

A little prior to this I installed Wine beta using Ubuntu Software Centre, then applied the multiuser wine recipe as noted here ([http://ubuntuforums.org/showthread.php?t=917422&](http://ubuntuforums.org/showthread.php?t=917422&)), then installed a game called ToonTalk3 ([www.toontalk.com](www.toontalk.com)), and then tried to install DirectX 10 as per these instructions [http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu](http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu)

The directx install stalled with a series of messages about being unable to copy certain dll files. I aborted the install, using the install wizard's abort command. It was a bit after this that I noticed the flashing symptoms. They may have been there earlier but I usually run my apps full screen so wouldn't have noticed.

I've reversed the wine multi-user configure, again using the recipe, and run `sudo apt-get purge wine1.2`, and logged off and on. The flashing and errors still occur. During logon there are bunch of indicator applet error message dialog boxes (which I'll post later after finishing this message and conducting another log off/on cycle).

I'm running Ubuntu 10.4 LTS 32bit on an Acer Asper 3500 notebook. The install is about 2 weeks old.

---

### Post by maphew on 2010-11-09
The error dialogs on login follow the form '''The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet". Do you want to delete the applet from your configuration? '''. This is repeated with different applet, e.g.  "OAFIID:GNOME_WorkspaceSwitcherApplet", "OAFIID:GNOME_FastUserSwitchApplet", for a total of 8 times.

The website for the directx10 install seems to unresponsive right now, here is a text only cache: [http://webcache.googleusercontent.com/search?q=cache:http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu&hl=en&strip=1](http://webcache.googleusercontent.com/search?q=cache:http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu&hl=en&strip=1)

The problem appears to be profile specific, other user account on the same laptop have no problems.

---

### Post by maphew on 2010-11-09
Some more seemingly related errors in /var/log/messaes:

{{{
kernel: [29756.766765] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
kernel: [29757.353786] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
kernel: [29966.831992] wnck-applet[23074] general protection ip:c4a264 sp:bfdbb6e0 error:890 in libbonoboui-2.so.0.0.0[c20000+5a000]
kernel: [29966.864566] trashapplet[23076] general protection ip:14f264 sp:bfe45dd0 error:890 in libbonoboui-2.so.0.0.0[125000+5a000]
kernel: [29968.638175] notification-ar[23108] general protection ip:b7a264 sp:bf927640 error:6890 in libbonoboui-2.so.0.0.0[b50000+5a000]
kernel: [29968.640400] indicator-apple[23107] general protection ip:b68264 sp:bfca70b0 error:890 in libbonoboui-2.so.0.0.0[b3e000+5a000]
kernel: [29968.643100] indicator-apple[23105] general protection ip:e99264 sp:bfba7d40 error:b890 in libbonoboui-2.so.0.0.0[e6f000+5a000]
kernel: [29968.731165] clock-applet[23106] general protection ip:769264 sp:bff97050 error:7890 in libbonoboui-2.so.0.0.0[73f000+5a000]
}}}

---

### Post by maphew on 2010-11-09
rebooting seems to have solved the flashing and errors. I'd still like to know what the heck happened, so if you have any insight please do say something. thanks :)

---

