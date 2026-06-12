---
title: "Need Help Troubleshooting x2go Server Problem"
date: 2012-02-29
forum: General Help
---

### Post by aquatone282 on 2012-02-29
Hi,

I have been using x2go Server on my 11.10 desktop machine with no problems for several months but today I can't connect.  When I try it looks like it's starting the session, but the full screen window closes before displaying the x2go splash screen.

I have no problems connecting via ssh using Putty.

The only thing I could find in the server's logs related to this was in auth.log:


Feb 29 07:51:28 ubuntu-desktop dbus[932]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=8512 comm="nm-applet ") interface="org.freedesktop.NetworkManager" member="GetPermissions" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=983 comm="NetworkManager ")

I used tail -f /var/log/auth.log to verify this message appears when attempting to connect via the x2go client.

Additional info 

uname -a: Linux ubuntu-desktop 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

x2go session type: custom desktop, command: gnome-session --session=ubuntu-2d

The only thing I can think of that changed was a routine package upgrade last night, but I don't know what packages were upgraded and don't know how to find out. Is there a log that shows package upgrade history? My guess is something is breaking the x2go authentication?

Thanks for any help anyone can provide to help me troubleshoot this.

Jim

---

### Post by FractalBrain on 2012-03-01
I'll help bump this as I also just started having the same problem.  It was after the upgrade.

---

### Post by Wlo on 2012-03-03
Same here.  Thanks.

---

### Post by dpippin on 2012-03-04
I saw this posted in the X2goserver mailing list.  I fixed the two symlinks and everything is fine.  Note the files are now located in /usr/lib/nx/X11

"Please fix two broken symlinks in /usr/lib/nx/X11/Xinerama manually  
and then your system should be online again."

[http://permalink.gmane.org/gmane.linux.terminal-server.x2go.user/489]("http://permalink.gmane.org/gmane.linux.terminal-server.x2go.user/489")

---

