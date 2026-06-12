---
title: "X won't start if no screen attached"
date: 2009-07-22
forum: General Help
---

### Post by Jelly2003 on 2009-07-22
I want to run a Ubuntu 9.04 box headless over the LAN and then use VNC to access it. 

My problem is that X will not start when I have no monitor plugged in (as opposed to Windows which starts the GUI regardless of whether a monitor is plugged in). 

So I've set the machine up, enabled VNC via the default Ubuntu remote desktop, and I am able to connect to it via Windows using Tight VNC. 

However, whenever I start the machine with no monitor plugged in I can not access the machine via VNC, I can ping it, but I can't VNC into it (SSH isn't enabled yet, will be enabling that soon). 

At this point I am sure that people will suggest that connect to it via SSH and tunnel VNC over SSH, unfortunately this will not work for me. 

I want the X server to run ALL THE TIME, and I need it to start instantly when the computer boots. If I use the tunnel via SSH option, I think the problem is that when I disconnect from VNC / SSH the X session will end and the GUI based applications that I need to run will all quit. 

Can anyone please tell me how to force X to start despite the fact that there is no monitor attached to the system?

Thanks

---

### Post by Pritamsng on 2009-07-24
Hi, All,
 Same prob here.......Actually i m trying to configure **[COLOR=#ff0000]vnc[/COLOR]** server(multy user) on **[COLOR=#ff0000]ubuntu[/COLOR]**.. its working fine but one problem i m getting that is from the client system when i m connect to server through **[COLOR=#ff0000]vnc[/COLOR]** i cant able to get the g[FONT=Times New Roman][SIZE=3]raphic.. a screen shoot i m attetching here. please any one can solve my prob then replay me..[/SIZE][/FONT]
[IMG]http://i620.photobucket.com/albums/tt288/pritamsng/vncprob.jpg[/IMG]

---

### Post by SgtDude on 2009-11-15
Pritamsng, I am familiar with that screen.  In that little xterm window type:

gnome-session
(for Ubuntu)
or
xfce-session
(for Xubuntu/Mythbuntu)

I'd guess if you're running Kubuntu it'd probably be:
kde-session
but I can't confirm that.

Anyway, I came to this thread hoping it'd have a better solution than the one I'm using, but it looks like it doesn't, so here's the solution I use:

boot server
ssh into server
type:
vncserver -geometry 1280x768
(this happens to be the resolution of my laptop monitor)
vncserver reports that it's built a vnc session on :1
use vnc client app to connect to server:1 (if you're typing the port number in manually, just add 1 to the default vnc port, which I can't remember off the top of my head).
Upon connection, I see Pritamsng's screen
type:
xfce-session
bada-bing, I now have a persistent session, it's just that rebooting is a pain in the bum.

---

### Post by Pritamsng on 2010-02-10
He i got the solution,
just write "sh" in place of "exec"

---

