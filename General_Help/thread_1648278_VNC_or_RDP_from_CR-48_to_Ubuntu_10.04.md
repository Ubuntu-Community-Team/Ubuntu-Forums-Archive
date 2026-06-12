---
title: "VNC or RDP from CR-48 to Ubuntu 10.04"
date: 2010-12-18
forum: General Help
---

### Post by JonnyPickel on 2010-12-18
Hey guys,

I was lucky enough to be one of the privileged few that got a shiny new CR-48 from Google.  I like the spirit of cloud computing but I'm not quite ready to cut myself off from my 500GB NAS yet, though.  So here's my question.

I'd like to find a RDP or VNC server that I can run on a tower running Ubuntu 10.04 which will allow me to use a browser (specifically Chrome OS) as the client.  Essentially I'd like to type http://192.168.1.1**:** into my omnibar and view the remote desktop instead of a web page.

A quick search on the intertubes brings up a bunch of options for Windows- and Mac-based software that will do this for me, but I need recommendations for server software that is compatible with Ubuntu.  Right now I have the built-in RDP software running on that machine, and if I use http://192.168.1.1**:5900 the page displays "RFB 003.007" on a white page.  I have no idea what that means.

Thanks in advance for all your help!

---

### Post by JonnyPickel on 2010-12-31
Shameful self-bump.  I'm still coming up short on finding something that works, has anyone come across this same problem?

Thanks!

---

### Post by strozykowski on 2011-01-14
I also have the CR-48, and normally, a Chrome browser would be fine to connect to the Java VNC port, if it is enabled on the PC you are going for. But ChromeOS is currently a different beast, and seems to be without that Java component.

The ChromeOS Lounge has a few threads that are ongoing, related to both VNC clients and servers on the CR-48 and ChromeOS:

[http://www.chromeoslounge.com/general-chrome-os/62-remote-desktop-access.html](http://www.chromeoslounge.com/general-chrome-os/62-remote-desktop-access.html)
[http://www.chromeoslounge.com/apps-extensions/271-rdp-client-chrome-os.html](http://www.chromeoslounge.com/apps-extensions/271-rdp-client-chrome-os.html)
[http://www.chromeoslounge.com/cr-48-chrome-notebook/600-anybody-running-vnc-s-there-cr-48-a.html](http://www.chromeoslounge.com/cr-48-chrome-notebook/600-anybody-running-vnc-s-there-cr-48-a.html)

There is also mention of the "Remoting" feature hidden in ChromeOS, which has yet to be fully implemented. I hope that turns into something pretty useful.

---

### Post by strozykowski on 2011-01-14
OK, that was completely accidental. How do I delete multiple posts?

---

### Post by choochus on 2011-02-09
I am successfully controlling my Ubuntu Linux desktop via vnc from my cr-48 laptop. There seems to be a few (possibly easier) methods, but what is working for me is the [Guacamole project]("http://guacamole.sourceforge.net/").

You can use the built-in remote desktop feature of Ubuntu (system/preference/remote desktop) for the vnc portion, then follow the instructions on the Guacamole page to install Apache, Tomcat and configure guacamole.

I'm guessing that things will be made even easier once the official Chromoting support is implemented, but given that Google is releasing other features (like remote printing) on Windows and Mac first, this may be our only option for a long time.

cheers!

 {c}

---

