---
title: "karmic lost xdmc option"
date: 2009-10-30
forum: General Help
---

### Post by mixmaster on 2009-10-30
On previous versions I can choose xdmc at the login screen.  This option appears to have vanished from Karmic.  Anyone know how to get it back.

Comes to that, is it possible to restore the 9.04 login screen so I can get rid of the user list until the gdm folk get their configuration tools to work?

---

### Post by Giblet5 on 2009-10-30
I installed kdm to get around this.

The default kdm splash has Session and Menu menus.

Not sure who's idea it was to name one of two menus "Menu", but that menu contains a "Remote Login" item that implements XDMCP.

If you want to be able to easily change the kdm theme, you'll need to install kubuntu-desktop.

---

### Post by joddy on 2009-10-31
While the XDMCP option seems to have (unfortunately) disappeared from the "Login Screen" options in GDM2.28/Ubuntu9.10 it can still be manually enabled.

You need to edit (or create if it does not exist) the file

/etc/gdm/custom.conf

and add these lines:

[xdmcp]
Enable=true
MaxSessions=16
DisplaysPerHost=2

Then, restart gdm or reboot the PC:

sudo /etc/init.d/gdm restart

Further configuration parameters for custom.conf are available at:
[http://library.gnome.org/admin/gdm/2.28/configuration.html.en](http://library.gnome.org/admin/gdm/2.28/configuration.html.en)


Apparently, file /etc/gdm/custom.conf is used now, instead of the old /etc/gdm/gdm.conf used in previous GDM and Ubuntu releases

Notes:
- In my case the file /etc/gdm/custom.conf existed already, because I had the AutoLogin option enabled. Alternatively, you may need to create it.  
- The "DisplaysPerHost=2" is a workaround for a bug. Without this line I was able to connect only once, the second attempt failed with a message saying 

"XDMCP fatal error: Session declined maximum number of open sessions from your host reached "


My /etc/gdm/custom.conf file looks like this now:
----------------------------
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=myusername
TimedLoginEnable=true
TimedLogin=myusername
TimedLoginDelay=10

[xdmcp]
Enable=true
MaxSessions=16
DisplaysPerHost=2
----------------------------

To verify that it worked I used another Ubuntu PC and entered:

Xnest :1.0 -query 192.168.2.101

192.168.2.101 being the IP address of the server on which XDMCP was enabled.

Hope this helps.

---

### Post by undfined on 2009-11-07
Just for clarification, I needed to install xnest on the client computer and joddy's /etc/gdm/custom.conf file needed to be edited on the XDMCP server computer.  I could then log in via Terminal Server Client (which is ideal for me).

After about a minute of being logged in, though, I get the attached error box.

---

### Post by undfined on 2009-11-26
FWIW I upgraded my laptop and installed Xnest.  Was able to connect to my server without any issue.  I updated the server via Xnest and rebooted.  When I tried to reconnect I got the minute of usability and then was logged off with a similar error as above.

---

### Post by undfined on 2009-11-29
Gah.  I did a fresh re-install on the "server" and now I get the attached error.  I think the meat is:

X error of failed request  BadDrawable (invalid Pixmap or Window parameter) .

followed by:

Major opcode of failed request:  70 (X_PolyFillRectangle)
Resource id in failed request:  0x0


Any help is appreciated.  All I want to do is look at one ubuntu desktop from another ubuntu machine on the same network.

---

