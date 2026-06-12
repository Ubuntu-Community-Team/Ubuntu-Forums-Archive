---
title: "VNC Setup"
date: 2011-07-17
forum: General Help
---

### Post by kenny3794 on 2011-07-17
I have an Ubuntu 11.04 desktop with several user logins available. During the day, my wife is logged in while I'm at work.  However, there are times I wish to be able to view information from my local PC at work, but without disrupting my wife.  At the same time, I would like to be able to utilize the display :0 configuration that is up an running for my login.  Is this possible?

Let me provide a potential workflow:
1.) I login to the PC before leaving for work.  I lock the PC on my way out.
2.)  The wife logs into the PC while I'm at work.  My applications are still running, but aren't on the current displayed terminal.
3.)  From work, I wish to VNC to the desktop and see the applications I had running, while my wife continues to use the PC.


Is this possible?  I've played some recently with NX and with vnc4server, both seem to create a whole new display/terminal for my login, thereby not porting over my unity settings, currently running applications, etc. I was looking at x11vnc, but it seems to "link" only to the current :0 display. (i.e., my wife's desktop/work)

And for those curious, yes I'm planning to run this through an SSH tunnel, but I want to get the local VNC working *first*, then I'll finish my configuration of a VNC tunnel, as I've already had this running in the past.

Thanks,
Kenny3794

---

### Post by HereInOz on 2011-07-17
With VNC, you are always going to end up connected to the current active console.  This is the great thing about VNC, that you do end up looking at the active console, and can use it for training, etc, and more than one person can look at the same thing.

Remote desktop solutions such as NX get you in to a new session, as you have already discovered.  

If your wife uses the computer while you are at work, then your only option (unless you want to sit there watching her work), is to log off the machine when you leave for work, and then establish a new NX session to your user account when you arrive at the factory.

Sorry I can't be of more assistance.

---

### Post by kenny3794 on 2011-07-17
Very well then. What about having my login via NX or vnc4server at least have the same settings as my local login?  Is there an easy way to do that?

---

### Post by HermanAB on 2011-07-17
Hmm, on Linux, VNC is almost always the wrong solution and it is the favourite way to get your machine hacked...

I'd suggest using SSH.  Read the snailbook.

---

### Post by kenny3794 on 2011-07-17
Herman,

I assume you read my first post, I plan on using SSH.  I even stated this, using SSH as a tunnel through which I will utilize VNC.  Just using SSH though does not provide me the x-windows interface I'm seeking.  Does anyone have a solution to help me port my current desktop settings (Unity) into the the Xwindows interface used by NX?

---

### Post by krunge on 2011-07-18
The only way I know to do what you want (i.e. view display :0 when your wife's display :1 is on the active linux console terminal) is to run a Virtual X session (e.g. either nx or vnc4server) and EVEN when you are LOCAL to the PC you use the viewer in a naked X session (i.e. the X session only runs nxviewer or vncviewer; no desktop or window manager.)

Most people won't stand for using the viewer locally as well as remotely. But AFAIK there is no way to get the contents of DISPLAY :0 when it is not on the active linux terminal.

I use this method (a virtual X session viewed locally and remotely via VNC) for my desktop at Work. That way I can access my work desktop from anywhere. The local performance is more than acceptable for my purposes.

More info here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc](http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc)[/INDENT]
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb](http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb)[/INDENT]

---

