---
title: "TS. RemoteApp?"
date: 2010-01-28
forum: General Help
---

### Post by hdpete on 2010-01-28
Hi all,
 
I've decided to make the switch and use ubuntu as my OS of choice at home. I have an old-ish Sony Vaio laptop which I wish to rebuild with ubuntu, and I'm happy about how I go about doing that. I've had a play with ubuntu in a VM first off, but there's one thing that's holding me back from installing.
 
The Mrs uses Family Tree maker Pro on the laptop (Windows genealogy app). I have a development server (Win 2008) which I run RemoteApps from and I've set FTM to run as a remoteapp. It runs great from any Windows machine with RDP6.1 or IE7/8 installed. It doesn't want to play with Firefox because the active-x RDP client isn't compatible with the FF browser.
 
Does anyone know of a way that I can get ubuntu onto the laptop, whilst retaining the FTM app capability for the wife? Needless to say, it needs to be a seemless experience for her, which is why I started down the RemoteApp route.
 
Thanks for any advice!
 
Regards
Peter

---

### Post by pawnrocket on 2010-01-29
I am also looking for a solution.

The Question: How can I use RemoteApps in ubuntu?

I am at work now and have to swap backup drives on the server so I can dig into it now, but I wanted to let you know that you are not alone.

I thought it was possible to load different profiles in FF and that IE8 was one of them. As I recall this was an add-on from the extensions library.

gotta go!

---

### Post by themtx on 2010-01-29
If I'm understanding correctly, it's an option to run "FTM" on your 2000 dev box, correct?  In that scenario, you could set up:

[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

on your dev box running FTM, then create a link to shortcut that launches it via rdesktop to display on yr Ubuntu laptop.  I use a fullscreen rdesktop session to a remote Win host for similar reasons (Outlook, AD tools, Exchange admin, IE) on my primary Xubuntu desktop.

---

### Post by foxmajik on 2010-04-17
> **pawnrocket said:**
> I am also looking for a solution.

The Question: How can I use RemoteApps in ubuntu?

I am at work now and have to swap backup drives on the server so I can dig into it now, but I wanted to let you know that you are not alone.

I thought it was possible to load different profiles in FF and that IE8 was one of them. As I recall this was an add-on from the extensions library.

gotta go!

There's a free version of [Nomachine NX]("http://www.nomachine.com/download.php") that does exactly what you want.

---

### Post by gemeinschaft on 2011-03-17
I am also looking for a solution, but I do not have Network Admin rights to the Servers that I need to receive Remoteapps from. 

The company that I work for uses Windows Server 2008 TS Remoteapps for our business programs and I would like to find a way (if possible) to use those apps without having to run a VM on my Ubuntu machine.

I know that the Plug-in for TS Remoteapps is designed only for IE, but thought if I could find a stripped version of IE, I could run it in Wine giving me the opportunity to at least bee able to multitask on my machine. 

Any suggestions are welcome, thanks.

---

### Post by foxmajik on 2011-03-17
> **gemeinschaft said:**
> I am also looking for a solution, but I do not have Network Admin rights to the Servers that I need to receive Remoteapps from. 

The company that I work for uses Windows Server 2008 TS Remoteapps for our business programs and I would like to find a way (if possible) to use those apps without having to run a VM on my Ubuntu machine.

I know that the Plug-in for TS Remoteapps is designed only for IE, but thought if I could find a stripped version of IE, I could run it in Wine giving me the opportunity to at least bee able to multitask on my machine. 

Any suggestions are welcome, thanks.

Download the installer for Internet Explorer 7 or 8 and run it under Wine.  It's worked fine for me before.

---

### Post by gemeinschaft on 2011-03-18
> **foxmajik said:**
> Download the installer for Internet Explorer 7 or 8 and run it under Wine.  It's worked fine for me before.

Thanks, I am trying that now. Once I install IE, I am using "wine wineboot" in Terminal to reboot, but IE does not show up under the programs folder and when I find the .exe file to start IE, it fails. 

Any suggestions?

---

### Post by foxmajik on 2011-03-18
> **gemeinschaft said:**
> Thanks, I am trying that now. Once I install IE, I am using "wine wineboot" in Terminal to reboot, but IE does not show up under the programs folder and when I find the .exe file to start IE, it fails. 

Any suggestions?

Try a different major version of IE.

If you're using 7 try 8; if you're using 8 try 7.  If neither of those work try 6.

If you're using 6 or 7 check that your Wine is set to emulate Windows XP.

---

### Post by whatspaz on 2011-11-29
A Microsoft Windows Remote Desktop Services RemoteApp RDP client in Linux/Ubuntu is now becoming a reality thanks to the FreeRDP project. As of this writing, the master repository build is working great with some of the plugins. I was able to connect the local Ubuntu filesystem via the \\tsclient disk protocol to the guest Windows Server 2008 R2 w/ Terminal Services and RemoteApp programs.

There are some great directions in the FreeRDP Wiki.

[http://www.freerdp.com/]("http://www.freerdp.com/")

Now as for integrating some of the FreeRDP-enabled RemoteApps in GNOME, I have developed a script to do this. It reduces the complexities of the RemoteApp command-line configuration to a single one-liner. I encourage anyone wanting to run RemoteApps to take a look at the configuration I have developed to do this. It requires a great amount of patience to configure this environment for the first time and the few glitches that remain in FreeRDP should probably start clearing up soon I would expect. But for the brave willing to compile your own code, head over and check out these scripts I've crunched to try to bring together Ubuntu and Windows under one GNOME.

[http://www.daball.me/2011/11/windows-meet-linux-linux-meet-remoteapp.html]("http://www.daball.me/2011/11/windows-meet-linux-linux-meet-remoteapp.html")

---

