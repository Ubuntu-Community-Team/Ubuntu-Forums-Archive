---
title: "New nx available from nomachine"
date: 2006-06-23
forum: General Help
---

### Post by mannheim on 2006-06-23
[nomachine.com]("http://www.nomachine.com") yesterday released a version 2.0.0 of their nx server, for free download as "NX Desktop Server", together with a new 2.0.0 version of nxclient.

I installed both, after uninstalling the freenx packages that I had been using (based on 1.4, I think). Some previous glitches have gone, but one thing I can't figure out.

With the freenx install, there's an option to create your own keypair for the nx "user" to connect to the server machine by ssh. On nomachine's web site, I can find almost no help on how to do this with this 2.0 version. I made a start, by guessing that "/usr/NX/bin/nxserver --keygen" was what I needed; but I am very confused about what keys this generates and where to put them.

Also, my fonts have colored fringes unless I use the "LAN" setting for connection speed.

Anyway, if anyone else has a look at the new nx, and if you have any insight to share, I'd be happy.

---

### Post by Fiyawerx on 2006-06-23
Well after spending all day yesterday trying to get freenx insatlled with no success, I did a fresh Dapper install this morning, ran the updates, and then decided to give this a shot.. WOW was it easy. (running Kubuntu)

If anyone's wondering, here's all I had to do.

Keep in mind, I believe nomachines server with its "free" license is max of 2 simul. connections or so, check their website to be sure if you're going to need more connections.

```
sudo apt-get install openssh-server

wget http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-90_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxnode_2.0.0-93_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/DS/nxserver_2.0.0-69_i386.deb

sudo apt-get install libstdc++2.10-glibc2.2 (needed for nxclient)
sudo dpkg -i nxclient_2.0.0-90_i386.deb
sudo dpkg -i nxnode_2.0.0-93_i386.deb
sudo dpkg -i nxserver_2.0.0-69_i386.deb
```

That was it, downloaded the new client and installed on my win xp pro machine ( I'm at work now ) configured a new session, and it worked! Damn this program is fast. I'm in heaven!

---

### Post by mannheim on 2006-06-24
[QUOTE=mannheim] I am very confused about what keys this generates and where to put them.
[/QUOTE]

I think I sorted myself out: on the server machine, 
```
sudo /usr/NX/scripts/setup/nxserver --server-keygen
```

Then copy the new key /usr/NX/share/keys/default.id_dsa.key to the client machine and paste it into the Key text box when configuring the nxclient session.

---

### Post by brargh on 2006-06-26
installed openssh.....then it was a piece of cake...
Don't forget to edit /usr/NX/etc/server.conf for access outside of the local device (that was where I stalled for minute or 2) :-k

did a connect from inside the vmware server that is running in the box (still need winblows sometimes) :rolleyes: - works now :-D

---

### Post by bullzebub on 2006-06-26
hello ...
i just installed the new NX .. and it seems great.
but i have a problem...
i only get Xterm when i log in? anyone know what could cause this?

and do you guys know how to make sessions with only one app (like the OOo example on nomachine)

---

### Post by mannheim on 2006-06-26
[QUOTE=bullzebub]hello ...
i just installed the new NX .. and it seems great.
but i have a problem...
i only get Xterm when i log in? anyone know what could cause this?

and do you guys know how to make sessions with only one app (like the OOo example on nomachine)[/QUOTE]

In the NX client login, click on "Configure ..." and look at the "General" tab. Under "Desktop", make sure that the drop-down menus say "Unix" and "GNOME" if you want a full gnome session.

To run a particular app, select "Unix" and "Custom" then click "Settings ...". Fill in the text box "Run the following command ... " entering the full path. Check the box for "Floating Window". Then log in.

---

### Post by bullzebub on 2006-06-27
oh! cool!
but if i dont have either kde or gnome installed? im running fluxbox you see...
i can run fluxbox as a command ... but that only give me the toolbar. and that is pretty useless!*laugh*

---

### Post by Fiyawerx on 2006-06-27
I havn't tried fluxbox, but I did have it working with e17, under the custom options I believe the command was ```
/usr/local/bin/enlightenment
```
Also, I had really weird issues unless I chose "new virtual desktop" instead of "floating window" on the custom settings window in the client.  After that it loaded up fine for me. Maybe try similar with fluxbox?

Oh, another thing I found hard to figure out for some reason, if you're using full screen, to get back to your windows desktop, put the mouse in the upper right corner (even above the X in a full screen window) and click, it should minimize the NX window. If you then right-click on the nx taskbar icon and hit close, and then click back INTO the nx icon, you have the option to terminate/suspend the session. Anyone know a way to do this from inside a full screen session?

---

### Post by bullzebub on 2006-06-27
Yes! it works when i select anything but "available area"
thnx alot!

cant you  just select custom resolution and set it to a few pixels less than your desktop area?

---

### Post by mannheim on 2006-06-27
[QUOTE=bullzebub]oh! cool!
but if i dont have either kde or gnome installed? im running fluxbox you see...
i can run fluxbox as a command ... but that only give me the toolbar. and that is pretty useless!*laugh*[/QUOTE]

In NX Client, select a "Custom" command, and under "Settings", try "/usr/bin/startfluxbox". Check "New Virtual Desktop" (not New Floating Window), and give it a try.

EDIT: Sorry, I see you've got it sorted out, thanks to Fiyawerx. I missed the post.

---

### Post by mannheim on 2006-06-27
[QUOTE=Fiyawerx]
Oh, another thing I found hard to figure out for some reason, if you're using full screen, to get back to your windows desktop, put the mouse in the upper right corner (even above the X in a full screen window) and click, it should minimize the NX window. If you then right-click on the nx taskbar icon and hit close, and then click back INTO the nx icon, you have the option to terminate/suspend the session. Anyone know a way to do this from inside a full screen session?[/QUOTE]

You just do "Ctrl-Alt-T" in full screen, and you get that dialog. Also, "Ctrl-Alt-M" is an alternative wasy to minimize the full screen session.

---

### Post by Fiyawerx on 2006-06-27
Thanks a lot mannheim, really starting to like this program.

---

### Post by jbinto on 2006-06-29
Hello,

I've got FreeNX 2.0 working in a ubuntu-to-ubuntu setup. I am even doing some sound editing via FreeNX's multimedia capabilities. Some latency but all in all acceptable considering it's over wireless.

My problem begins when I start using gtk1 apps. XMMS for example, preferences and menus appear as square boxes. Audacity complains once about "encoding" (I cannot reproduce this error, unfortunately) and it's menus too are only square boxes.

I confirmed this is a NX server issue by installing another NX Client on a Windows box, and with the addon 75-100-extra fonts for Windows, and still, boxes. I checked that both Linux boxes have the same font configurations, I tried running an strace on xmms to see if it was looking for fonts that it couldn't find, but alas, I could find nothing.

Anyone know what's up? FreeNX is otherwise flawless. Add GTK1 apps and it's perfect.

---

### Post by mannheim on 2006-06-29
[QUOTE=jbinto]
Anyone know what's up? FreeNX is otherwise flawless. Add GTK1 apps and it's perfect.[/QUOTE]

You could try using a different font in your gtk1 apps, if you haven't tried that already. You can configure the default gtk1 font somewhere (I don't remember where). There's an app you can install which will do this for you:

```
sudo apt-get install gtk-theme-switch
```

Run the app, click on the "menu" icon top-right, and change the default font. Might help.

EDIT: Of course, gtk-theme-switch is itself a gtk1 app. So trying to use it to fix your problem is a catch-22 unless you have local access to machine. You could experiment with an nx connection to localhost, I suppose.

---

### Post by mannheim on 2006-06-29
Possibly related: I don't have any gtk1 apps that I am aware of, but I do run an app that uses the really old-style x-fonts without freetype or whatever has repalced them. There are very few fonts available to this app when run via nx. I've no understanding of fonts in X unfortunately.

---

### Post by jbinto on 2006-06-29
While the gtk-themes-switch did tell me some things about my fonts:

1) 2 byte fonts may not be displayed correctly.
2) This font is not available
3) (in terminal window) The font "-adobe-helvetica-medium-r-normal-*-*-120-*-*-p-*-iso10646-1,*" does not support all the required character sets for the current locale "C"
  (Missing character set "ISO8859-1")

Even when picking a font that doesn't exhibit ANY of the above characteristics (there aren't many), XMMS and audacity still won't use it. The font is either hardcoded or set elsewhere, unfortunately.

---

### Post by jbinto on 2006-06-30
I decided to go the other way, this time, desktop-to-laptop. Both run Dapper, but the laptop is Flight 6 dist-upgraded and the desktop is the final. This way, XMMS and audacity both work, so there's something wrong with the config on my desktop(?).

Funny though, Audacity on the laptop-via-desktop has readable menus but still says "No font for displaying text in encoding "Western European (ISO-8859-1) found, but an alternative encoding "Western European with Euro (ISO-8859-15) is available".

So, it works the way I don't need it... I want to connect to my desktop from my laptop. Any tips on how I can compare the configs and isolate the problem on the desktop?

---

### Post by mannheim on 2006-06-30
[QUOTE=jbinto]
So, it works the way I don't need it... I want to connect to my desktop from my laptop. Any tips on how I can compare the configs and isolate the problem on the desktop?[/QUOTE]

The thing I would try first is to find out if the difference is between the home directories on the two machines. Eg, create a new user "joe" on both machines, and don't touch any settings in the new accounts. Then try and use nx, from "joe" to "joe", both ways.

---

### Post by MatBi on 2006-07-03
I just installed the 2.0 version from nomachine on both server (ubuntu) and client (XP).
The client looks weird, i get 3 windows in the taskbar, one for the desktop itself, one for the upper and one for the lower bars. All of them are called "Cygwin/XFree86 X rl"
I was running freenx from the ubuntu repositories until the new version of the nomachine client broke up.
I'm running xfce4.
Anyone else has the same issues?

---

### Post by matrooswolf on 2006-07-03
[QUOTE=brargh]installed openssh.....then it was a piece of cake...
Don't forget to edit /usr/NX/etc/server.conf for access outside of the local device (that was where I stalled for minute or 2) :-k
[/QUOTE]
Hi brargh, 
what did you edit in /usr/NX/etc/server.conf?
I still have issues with nxserver, one user works perfectly, and another gives server errors.  

I have no idea what is wrong.  So I'm looking for all possible clues ...

---

### Post by mannheim on 2006-07-03
[QUOTE=MatBi]I just installed the 2.0 version from nomachine on both server (ubuntu) and client (XP).
The client looks weird, i get 3 windows in the taskbar, one for the desktop itself, one for the upper and one for the lower bars. All of them are called "Cygwin/XFree86 X rl"
I was running freenx from the ubuntu repositories until the new version of the nomachine client broke up.
I'm running xfce4.
Anyone else has the same issues?[/QUOTE]

Just a guess, but it sounds like this might be caused by selecting "Floating Window" instead of "New Virtual Desktop" in the configuration dialog of NX client (Configure-->General-->(Desktop)Settings).

---

### Post by giuliastro on 2006-07-04
Does anyone know how I can have (or change) a different X resolution when I use nx? I have my desktop set as 1280x1024 but my client is only capable of 1024x768. When I connect to nxserver my screen gets cut off. I used to love some VNC clients that resize the desktop, unfortunately nx doesn't do this. I believe I must solve it by setting a different X size server side.. but where? If I place it on my xorg.conf, how am I able to switch resolutions when logged in with nxclient? Thanks in advance.

---

### Post by MatBi on 2006-07-04
You can specify the resolution in the client configuration, under Display.

---

### Post by giuliastro on 2006-07-04
[QUOTE=MatBi]You can specify the resolution in the client configuration, under Display.[/QUOTE]

Ok, sorry, I haven't been clear enough. No matter what resolution I choose, the client doesn't really change the server resolution. Actually what you can choose with nxclient is the SIZE of the window, not the resolution. If my server desktop is 1280x1024 and I choose 800x600 using the client I only get a clipped 1280 desktop displaying just a part of my whole desktop. This solution is not accettable since a clipped 1280 desktop is not at all the same as a 800x600 desktop. :)

Also, if you just launch an application (and not the whole X session), nxclient doesn't let you set any resolution. This shows even more that the resolution depends on the X server and not on the nxclient as you think.

Thanks again.

---

### Post by MatBi on 2006-07-04
Weird, i'm not getting the same behaviour, in my system the window size i set in the client IS the desktop resolution. It could be because i'm starting the windows manager manually (Unix -> custom -> startxfce4) but it's the first time i see something like this.
Is your client running under Linux or Windows?

---

### Post by giuliastro on 2006-07-04
I am connecting to a Dapper nxserver from a Windows client. Both server and client are latest versions, but actually it has happened ever since. My desktop icons get out of my nxclient window and I cannot reach them. The problem is that no matter what resolution I set on my client, my icons and fonts always have the same size.
As I said, I don't believe it's my system. You are probably connecting at the same resolution your nxserver desktop is, so you don't see the difference. But if your client has a smaller resolution than your nxserver than you can see what happens. I understand why this happens, I believe NX uses server's screen resolutions and this is why nxclient can't do much about it. I just need to find out how to switch resolutions while I am logged in since client can't do anything about it.

To let you understand how nx works, when you use nxclient to launch a floating window (and not KDE or Gnome or whatever), you cannot choose a resolution. This means the application you launch will always be set to your server's resolution. This is pretty much what happens when you launch KDE or Gnome with nxclient: what you change when you "select size of your remote desktop" is not the resolution but, as it says, the size of the window.

---

### Post by MatBi on 2006-07-04
I can quickly assure that this is not the case, i can set any of the available resolutions. In fact, i can open multiple session at different resolutions, and the resolution is shown when i'm prompted to restore one.

---

### Post by Fiyawerx on 2006-07-04
I don't have that problem either, I connect from a windows laptop @ 1024x768 to a server running default of 1280x1024, and i get a full screen 1024 sized kde session. Tried it with e17, and xfce, and had the same thing happen, seemed to work fine for me.

---

### Post by giuliastro on 2006-07-06
[QUOTE=MatBi]I can quickly assure that this is not the case, i can set any of the available resolutions. In fact, i can open multiple session at different resolutions, and the resolution is shown when i'm prompted to restore one.[/QUOTE]

You mean you can run a single application with "run the following command" and set the resolution for it? I really don't understand how this could work. Did you try using different resolutions? Your icons and fonts have different sizes? If not then I am right: you are not really changing your desktop resolution but your desktop size, which is different. Please, let me know.

---

### Post by trickyzach on 2006-07-06
How is this in regards to lag? I have had trouble with VNC not being nearly as fast as RDC on an xp machine?

Hoping to make the complete switch !!

---

### Post by mannheim on 2006-07-06
[QUOTE=trickyzach]How is this in regards to lag? I have had trouble with VNC not being nearly as fast as RDC on an xp machine?

Hoping to make the complete switch !![/QUOTE]

When I stopped using XP and started using ubuntu, the one thing I really missed was XP's Remote Desktop. I used to tunnel RDC through ssh for a secure connection from home to work between my two Windows XP machines. Anyone who says RDC is slow hasn't used it between two Windows XP machines. (Using RDC from a non-Windows client seems really slow however.)

But now I have nx set up, and really it is snappier even than RDC.

The things I still miss about RDC are:

[LIST]
[*]transparent sharing of printers without configuration;
[*]the ability to connect to a previous **local** session on the server; that is, I can work locally on the machine at work, and later connect to the same session from home. 
[/LIST]

To achieve the second thing using nx, you need to run your local session through nx (an nx connection to localhost), which isn't worth the trouble in my case. I sorted out the printing thing by using port forwarding and ssh.

---

### Post by trickyzach on 2006-07-06
Glad to hear about the speed. I agree XP RDC is great.

I can live with the other thing. 

Here we come ubuntu 100%

---

### Post by giuliastro on 2006-07-06
I agree about speed. It's amazingly fast, I set it as a modem connection and I still get a stunning speed. I'd say it's really comparable to XP remote desktop.
Even more: I set up thunderbird on my server and use nx to launch just that application. This means I have all my mail wherever I go pretty easy without loading the whole remote desktop. ;)

Again, what I don't like is resolution settings and session options which are not comparable to UltraVNC or TightVNC.

---

### Post by brargh on 2006-08-03
> **matrooswolf said:**
> Hi brargh, 
what did you edit in /usr/NX/etc/server.conf?
I still have issues with nxserver, one user works perfectly, and another gives server errors.  

I have no idea what is wrong.  So I'm looking for all possible clues ...
Can't remember, I installed the .tgz-s at that time.
Last week did an install with the newly provided .deb files - that worked immediately in my Xubuntu box...
I know it sounds winblows like, but try reinstalling the faulty client - maybe minor version mismatch???

brgds,

---

### Post by skorpi0wn on 2006-09-26
> **Fiyawerx said:**
> Well after spending all day yesterday trying to get freenx insatlled with no success, I did a fresh Dapper install this morning, ran the updates, and then decided to give this a shot.. WOW was it easy. (running Kubuntu)

If anyone's wondering, here's all I had to do.

Keep in mind, I believe nomachines server with its "free" license is max of 2 simul. connections or so, check their website to be sure if you're going to need more connections.

```
sudo apt-get install openssh-server

wget http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-90_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxnode_2.0.0-93_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/DS/nxserver_2.0.0-69_i386.deb

sudo apt-get install libstdc++2.10-glibc2.2 (needed for nxclient)
sudo dpkg -i nxclient_2.0.0-90_i386.deb
sudo dpkg -i nxnode_2.0.0-93_i386.deb
sudo dpkg -i nxserver_2.0.0-69_i386.deb
```

That was it, downloaded the new client and installed on my win xp pro machine ( I'm at work now ) configured a new session, and it worked! Damn this program is fast. I'm in heaven!

I followed this method above (even a fresh install of Kubuntu) and it still gets an error message when trying to connect remotely (from a WinXP) machine.

NX> 203 NXSSH running with pid: 3652
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 72.40.60.240 on port: 22
NX> 211 The authenticity of host 'www.ryryonline.com (72.40.60.240)' can't be established.
RSA key fingerprint is d1:a5:0c:e1:4d:21:0c:7d:ca:7d:59:2b:af:f4:f6:16.
Are you sure you want to continue connecting (yes/no)? 
Warning: Permanently added 'www.ryryonline.com,72.40.60.240' (RSA) to the list of known hosts.
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.0.0-76 - LFE
NX> 105 Hello NXCLIENT - Version 2.0.0
NX> 134 Accepted protocol: 2.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: admin
NX> 102 Password: ******
NX> 103 Welcome to: steve user: admin
NX> 105 Listsession --user="admin" --status="suspended\054running" --geometry="1280x1024x32+render" --type="unix-kde" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: admin
NX> 105 Start session with: --link="adsl" --backingstore="1" --streaming="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="RyRy" --type="unix-kde" --geometry="1280x964" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1280x964x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 50D7EF0F. To get detailed information about
NX> 595 ERROR: the error search for the string 50D7EF0F in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Ignoring EOF on the monitored channel
NX> 280 Ignoring CLOSE on the monitored channel
Killed by signal 15.

---

### Post by gwyrlim on 2006-09-26
Hi.
Im getting the same fault as skorpi0wn but I run Ubuntu. Looking in the /var/log/messages givs this. 

Sep 27 00:03:13 dragon NXSERVER 2.0.0-76[7275]: User 'markus' logged in from '192.168.0.2'. 'NXLogin::set'
Sep 27 00:03:15 dragon NXSERVER 2.0.0-76[7275]: Selected node host:localhost with port:22 'main::selectNode'
Sep 27 00:03:15 dragon NXSERVER 2.0.0-76[7275]: Current selected node: localhost is in status: running  'main::selectNode'
Sep 27 00:03:18 dragon NXSERVER 2.0.0-76[7275]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 ERROR: NXNODE Ver. 2.0.0-100  (Error id eF108FB) [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 ERROR: Wed Sep 27 00:03:21 2006 running as user: 'markus' (uid: 1000) on '' [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 ERROR: execution of last command failed [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/markus/.nx/C-dragon-1013-559CDA1F83245E5090FCF83DB8660A59/scripts/authority' [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 exit value: 1 [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 stdout:  [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 stderr: xauth:  /home/markus/.Xauthority not writable, changes will be ignored [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 . [eF108FB] 'main:nxnode:2671'
Sep 27 00:03:21 dragon NXNODE 2.0.0-100[7296]: ERROR: NX> 596 init: stdin arguments: user=markus,userip=192%2e168%2e0%2e2,uniqueid=559CDA1F83245E5090FCF83DB8660A59,display=1013,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e0%2e5,encryption_mode=3,connection=local,images=32M,cache=8M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=Ubuntu,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1024x768x32%2brender,nodelay=1,streaming=1,keyboard=pc102%2fse,geometry=1024x768,link=lan 'main:nxnode:2671'
Sep 27 00:03:22 dragon NXNODE 2.0.0-100[7296]: INFO: getting agent pid: cannot read pid file '/home/markus/.nx/C-dragon-1013-559CDA1F83245E5090FCF83DB8660A59/pids/agent'. Exiting. 'main:nxnode:7874'
Sep 27 00:03:22 dragon NXNODE 2.0.0-100[7296]: INFO: directory '/home/markus/.nx/C-dragon-1013-559CDA1F83245E5090FCF83DB8660A59' moved into '/home/markus/.nx/F-C-dragon-1013-559CDA1F83245E5090FCF83DB8660A59' for investigation 'main:nxnode:7929'
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 ERROR: NXNODE Ver. 2.0.0-100  (Error id eF108FB)
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 ERROR: Wed Sep 27 00:03:21 2006 running as user: 'markus' (uid: 1000) on ''
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 ERROR: in node start session: create session: run commands
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 ERROR: execution of last command failed
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/markus/.nx/C-dragon-1013-559CDA1F83245E5090FCF83DB8660A59/scripts/authority'
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 exit value: 1
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 stdout: 
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 stderr: xauth:  /home/markus/.Xauthority not writable, changes will be ignored
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NX> 596 init: stdin arguments: user=markus,userip=192%2e168%2e0%2e2,uniqueid=559CDA1F83245E5090FCF83DB8660A59,display=1013,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e0%2e5,encryption_mode=3,connection=local,images=32M,cache=8M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=Ubuntu,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1024x768x32%2brender,nodelay=1,streaming=1,keyboard=pc102%2fse,geometry=1024x768,link=lan
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NXNodeExec::exec('startsession', 'user=markus&userip=192%2e168%2e0%2e2&uniqueid=559CDA1F83245E5090...', 'localhost', 22) called at handlers/nxserver.pl line 2851
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NXShell::handler_session_start('--link="lan" --backingstore="1" --streaming="1" --nodelay="1" --...') called at NXShell.pm line 374
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NXShell::handle_command('startsession', '--link="lan" --backingstore="1" --streaming="1" --nodelay="1" --...') called at NXShell.pm line 145
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) NXShell::run() called at nxserver.pl line 4492
Sep 27 00:03:22 dragon NXSERVER 2.0.0-76[7275]: ERROR: (exception id F4B675EB) eval {...} called at nxserver.pl line 4451

I have read all thread I have found, but found no solution to the problem.
Hope this can help someone to find it.
Gwyrlim

---

### Post by gwyrlim on 2006-09-27
Solved my problem. 
.Xauthority was owned by root, don't know why. I made a new user and tryed to connect to that one and had no problems. The new user owned it's own .Xauthority. After change the file owner for the first user I can connet to that one to. 
Hope it helps someone.
/gwyrlim

---

### Post by jbuberel on 2006-09-30
Just for reference, this same error message will be reported when you configure your NX client session to use the 'KDE' desktop then try to connect to a standard Ubuntu host, which does not have the full set of KDE packages installed (as would a Kubuntu host).

By changing the desktop type to 'Gnome' in the NXClient configuration for the connection will resolve the problem.

> **gwyrlim said:**
> Sep 27 00:03:18 dragon NXSERVER 2.0.0-76[7275]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'

---

### Post by mukatira on 2006-10-09
HI all,

I installed nx following the instructions from [http://www.nomachine.com/ar/view.php?ar_id=AR07D00407](http://www.nomachine.com/ar/view.php?ar_id=AR07D00407)

When I test it: I get the follwing error.

**@SM-ubuntu:/usr/NX/bin$ ./nxserver --status**
NX> 595 ERROR: Initialization failed: Can't open file: /usr/NX/etc/server.cfg.
NX> 595 ERROR: No such file or directory. Please try to fix the problem by
NX> 595 ERROR: running /usr/NX/scripts/setup/nxserver --install.

Could anyone point me to what I am doing wrong?
Thanks

-Sm

Here are the errors during installation:

**@SM-ubuntu:~/Desktop$ sudo dpkg -i force-architecture nxclient_2.1.0-6_i386.deb**
dpkg: error processing force-architecture (--install):
 cannot access archive: No such file or directory
Selecting previously deselected package nxclient.
(Reading database ... 80576 files and directories currently installed.)
Unpacking nxclient (from nxclient_2.1.0-6_i386.deb) ...
dpkg: dependency problems prevent configuration of nxclient:
 nxclient depends on libstdc++2.10-glibc2.2; however:
  Package libstdc++2.10-glibc2.2 is not installed.
dpkg: error processing nxclient (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 force-architecture
 nxclient
**@SM-ubuntu:~/Desktop$ sudo dpkg -i force-architecture nxnode_2.1.0-7_i386.deb**
dpkg: error processing force-architecture (--install):
 cannot access archive: No such file or directory
Selecting previously deselected package nxnode.
(Reading database ... 80716 files and directories currently installed.)
Unpacking nxnode (from nxnode_2.1.0-7_i386.deb) ...
dpkg: dependency problems prevent configuration of nxnode:
 nxnode depends on nxclient (>= 2.1.0); however:
  Package nxclient is not configured yet.
dpkg: error processing nxnode (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 force-architecture
 nxnode
**@SM-ubuntu:~/Desktop$ sudo dpkg -i force-architect nxserver_2.1.0-7_i386.deb**
dpkg: error processing force-architect (--install):
 cannot access archive: No such file or directory
Selecting previously deselected package nxserver.
(Reading database ... 80921 files and directories currently installed.)
Unpacking nxserver (from nxserver_2.1.0-7_i386.deb) ...
dpkg: dependency problems prevent configuration of nxserver:
 nxserver depends on nxclient (>= 2.1.0); however:
  Package nxclient is not configured yet.
 nxserver depends on nxnode (>= 2.1.0); however:
  Package nxnode is not configured yet.
dpkg: error processing nxserver (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 force-architect
 nxserver

---

### Post by eagle63 on 2006-10-09
I'm a new Ubuntu user who just installed nx as well.  Like everyone else has said, it's great - very fast.  However, like someone else on this thread I'm having problems setting the resolution too.

Here's my scenario:  

I've got a laptop with a 15" screen, 1200 x 1024.  (roughly)  Connected to my laptop is a 21" Dell Ultrasharp monitor, 1600 x 1200 resolution.  My laptop runs windows xp, and in the settings I choose "extend my windows desktop" onto the 21" monitor. I've got a headless workstation running Ubuntu that I connect to from my laptop.  

I used to run windows on that headless workstation, and using Remote Desktop I could connect to it from my laptop, drag the Remote Desktop "window" onto my 21" monitor, and it would all scale properly so that I was viewing the workstation at fullscreen 1600 x 1200 resolution via Remote Desktop.  

Now that my workstation is running Ubuntu and using NX to connect to it, I can't seem to find a way to do the same thing.  In other words, the NX Client connection screen expands to fit my 15" laptop screen, but when I drag it to my 21" monitor it doesn't change size.  Even if I choose "custom" in the NX client settings, and force it to 1600 x 1200, it doesn't change size at all.  

Does anyone have any ideas or see something I may be missing??  Sorry for the long-winded explanation but I just wanted to lay the whole scenario out for clarity.  Thanks!!

---

### Post by acegolfer on 2006-11-11
I have been using FreeNX so far. Is Nomachine NX better?

---

### Post by mbailey on 2006-11-18
Fiyawerks - thanks! I have been trying to get nx working for MONTHS - your  post in June finally got me there. I believe I owe you a beer :-D

---

### Post by ollyshaw on 2006-12-18
wow it really is pretty much as good as remote desktop! Very very impressed, miles better than VNC.

Olly

---

### Post by numa666 on 2007-03-09
I'm using my dapper box as a router and for running LinuxDC++. Thing is, there is a rule on our internal network that DC++ can't run from 20:00 till 02:00. It's very important for me that an diplay session runs on a same display number all the time, so I can simply start/kill DC++  with DISPLAY=:SOME_DISPLAY_NUMBER prefix in crontab. 

It worked with VNC but I don't have much of an upload capability on my ADSL and a real remote control would be nice.

I've been using FreeNX for a week now and suspend is simply not working reliably. Sometimes it throws an error while negotiating link parameters. After that a display (usually :1000) is "spent". All new connections end up at higher numbers.

So, I decided to try NoMachine NX. Quicky a problem appeared: after terminating a session I can't reconnect on the same display number!

I've tried restarting nxserver (./nxserver --restart), clearing history (./nxserver --history clear) but to no avail.

If some good soul knows how to solve the display issue or simply knows a simpler solution to my problem I'd be most grateful!

---

### Post by p_schott on 2008-02-12
> **giuliastro said:**
> Ok, sorry, I haven't been clear enough. No matter what resolution I choose, the client doesn't really change the server resolution. Actually what you can choose with nxclient is the SIZE of the window, not the resolution. If my server desktop is 1280x1024 and I choose 800x600 using the client I only get a clipped 1280 desktop displaying just a part of my whole desktop. This solution is not accettable since a clipped 1280 desktop is not at all the same as a 800x600 desktop. :)
Hi, I'am experiencing the same problem (nxserver on a 1280x1024 desktop running Gutsy and nxclient on a 1024x768 desktop running XP). Did you find a solution since then ?

---

### Post by mulpuru on 2008-04-29
I followed all the instructions
```
wget http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-9_i386.deb
wget http://64.34.161.181/download/3.2.0/Linux/nxnode_3.2.0-5_i386.deb
wget http://64.34.161.181/download/3.2.0/Linux/FE/nxserver_3.2.0-7_i386.deb
apt-get install libstdc++2.10-glibc2.2
dpkg -i nxclient_3.2.0-9_i386.deb
dpkg -i nxnode_3.2.0-5_i386.deb
dpkg -i nxserver_3.2.0-7_i386.deb
/usr/NX/scripts/setup/nxserver --server-keygen
copied /usr/NX/share/keys/default.id_dsa.key to the nxclient machine and used it


```

But when i try to connect it gives me host not found error (it was able to authenticate though)

Error log From Nxclient (using winxp and NX win client 1.50-13)
```
NX> 203 NXSSH running with pid: 2948
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 131.183.16.47 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-7 - LFE
NX> 105 Hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: siva
NX> 102 Password: ******
NX> 103 Welcome to: laptop user: siva
NX> 105 Listsession --user="siva" --status="suspended\054running" --geometry="1600x1200x32+render" --type="unix-kde" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: siva
NX> 105 Start session with: --session="laptop" --type="unix-kde" --cache="8M" --images="32M" --link="lan" --kbtype="pc102\057en_US" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="1600x1170" --media="0" --agent_server="" --agent_user="" --agent_password="" --agent_domain="" --screeninfo="1600x1170x32+render" 
NXSERVER - Version 3.2.0-7 - LFE
Tue Apr 29 14:56:37 2008 running as user: 'nx' (uid: 110, pid: 5685) on 'laptop'
Info: user login is siva (NXShell)
Info: user password is '******' (NXShell)
Info: using 'sshd authentication' (NXShell)
Info: selected user 'siva' is authenticated (NXNodeExec)
Info: password for selected user is in 'text' mode (NXNodeExec)
Info: preferred auth method is '' (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l siva localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 5695 (NXNodeExec)
[B]Info: received data in err channel from NX Node: 'nxssh: localhost: Name or service not known
' (NXNodeExec)
[/B]Info: NX Node out channel was closed (NXNodeExec)
Info: Removing not recognized buffer from stdout:[] (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
Killed by signal 15.

```

**/Var/log/messages**
```
Apr 29 14:56:36 laptop NXSERVER-3.2.0-7[5685]: User 'siva' logged in from '131.183.21.137'. 'NXLogin::set'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: Selected node host:localhost with port:22 'main::selectNode'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: Current selected node: localhost is in status: running  'main::selectNode'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: Selected session type: unix-kde allowed in the profile of user: siva 'NXShell::Static'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) Error: no 'CONNECTED' message from NX Node
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) nxssh: localhost: Name or service not known^M
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXNodeExec::exec('startsession', 'user=siva&userip=131%2e183%2e21%2e137&uniqueid=84AF740D79C212559...', 'localhost', 22) called at handlers/nxserver.pl line 3275
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXShell::handler_session_start('--session="laptop" --type="unix-kde" --cache="8M" --images="32M"...') called at NXShell.pm line 373
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXShell::handle_command('startsession', '--session="laptop" --type="unix-kde" --cache="8M" --images="32M"...') called at NXShell.pm line 145
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXShell::run() called at nxserver.pl line 4430
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) eval {...} called at nxserver.pl line 4389
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'


```

```
root@laptop:~# cat /etc/hostname
laptop
root@laptop:~# cat /etc/hosts
127.0.0.1 laptop
127.0.1.1 laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

could some please help me...? :KS

---

### Post by mulpuru on 2008-04-29
I solved the problem guys,

changed /etc/hosts
**cat /etc/hosts**
```
root@laptop:~# cat /etc/hosts
127.0.0.1 laptop
127.0.1.1 laptop

```

to 
**cat /etc/hosts**
```
root@laptop:~# cat /etc/hosts
127.0.0.1 localhost laptop
127.0.1.1 laptop

```

---

### Post by drifting on 2008-05-27
this is driving me to distraction, anyone got an idea why this keeps failing ? Latest versions of everything,and on an previously working version on Gutsy, not upgraded Hardy, must be Kismet Hardy !

Paul.

NX> 203 NXSSH running with pid: 13172
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.0.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-7 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: paul
NX> 102 Password: ********
NX> 103 Welcome to: vs user: paul
NX> 105 Listsession --user="paul" --status="suspended\054running" --geometry="2560x1024x24+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: paul
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="10.0.0.1" --type="unix-gnome" --geometry="2560x993" --client="linux" --keyboard="pc105\057gb" --screeninfo="2560x993x24+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: BE2753A0. To get detailed information about
NX> 595 ERROR: the error search for the string BE2753A0 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

---

