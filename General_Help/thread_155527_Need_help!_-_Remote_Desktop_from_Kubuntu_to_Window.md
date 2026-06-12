---
title: "Need help! - Remote Desktop from Kubuntu to Windows XP (VNC)"
date: 2006-04-05
forum: General Help
---

### Post by Bristen Bourque on 2006-04-05
Hi all,

I have a notebook running Kubuntu 5.10 quite smoothly right now and a desktop running Windows XP Home.  I want to be able to run a VNC client on my notebook and connect to my Windows XP machine.  I am able to ping my Windows machine, and I'm also able to read and write files to/from shared folders on my Windows machine (this proves that the LAN is working, correct?).

After installing different VNC servers on my Windows box I was never able to connect from my Kubuntu notebook.  When using KDE's Remote Desktop application, I would not get any errors, the window would just close.  When running other VNC viewers I sometimes got errors like "connection reset by peer", "connection refused" and "Cannot cope with 24 bits-per-pixel color. Sorry." I tried so many viewers and servers that I can't be sure what combo I was using when receiving those errors.  Another thing is that I was able to connect to my VNC server from my Windows box using "localhost". 

Any clues as to what is going on? Any information I should of provided and I didn't? I tried playing around with "Terminal Server Client", "rdesktop", "xtightvncviewer" to no avail... prefered method would be the KDE Remote Desktop application if possible.

Any help would be greatly appreciated!  I really did not want to install Windows back on my notebook!! Please help :( 

Thanks in advance,
  Bristen.

---

### Post by Prospero2006 on 2006-04-05
I actually spent about 2 hours last night doing the same thing. Except I got the VNC working both ways. XP --> Kubuntu  Kubuntu --> XP.

Here's how I pulled up the XP machine:

Google for tightvncserver. On their website they offer a .zip file that you can extract. You run the .exe file on your xp machine. Then, what I did was opened up firefox. In the address bar I type: ip.address.of.xp:5800
This will bring up the desktop in your browser through a java applet. 

It worked great for me. I was real happy with the result.

I hope that helps.

Pros

---

### Post by dermotti on 2006-04-05
I would use Terminal Services (RDP). You need to make sure RDP is enabled on your windows box.

---

### Post by Bristen Bourque on 2006-04-05
[QUOTE=Prospero2006]I actually spent about 2 hours last night doing the same thing. Except I got the VNC working both ways. XP --> Kubuntu  Kubuntu --> XP.

Here's how I pulled up the XP machine:

Google for tightvncserver. On their website they offer a .zip file that you can extract. You run the .exe file on your xp machine. Then, what I did was opened up firefox. In the address bar I type: ip.address.of.xp:5800
This will bring up the desktop in your browser through a java applet. 

It worked great for me. I was real happy with the result.

I hope that helps.

Pros[/QUOTE]

hehe, 2 hours? That's about what I spent but I didn't manage to get it  working!! I saw that option to do it through a browser... the problem is I don't have the JRE on my notebook.. I know there are "how to's" out there on that topic, but I just haven't bothered... because of this, I didn't even try that... it is a valid option though, I just need to install a JRE and give it a shot.. 

thanks for the idea, I'll try that tonight once I get back home...

Bristen.

---

### Post by Bristen Bourque on 2006-04-05
[QUOTE=dermotti]I would use Terminal Services (RDP). You need to make sure RDP is enabled on your windows box.[/QUOTE]

my windows box is only WinXP Home.. I can't use RDP on Windows XP Home, right? It's only in the Professional version, is it not?

Thanks,
  Bristen.

---

### Post by pete on 2006-04-05
You can RDP out from an XP Home box, but it can't accept incoming connections (which is a shame, because RDP works a LOT better than VNC).

Do you have Service Pack 2 installed on the XP machine?  If so, have you checked to make sure the firewall isn't blocking whatever port the VNC server is listening for connections on?

---

### Post by Bristen Bourque on 2006-04-05
[QUOTE=pete]You can RDP out from an XP Home box, but it can't accept incoming connections [...][/QUOTE]
 uh, right.. that's what I meant :) Since I want to connect from my Kubuntu notebook to my WinXP box, I can't use RDP... I however connect at work from my WinXP box using RDP... it's not going "out" but going "in" using RDP that's the problem with WinXP Home :)

[QUOTE=pete]Do you have Service Pack 2 installed on the XP machine?  If so, have you checked to make sure the firewall isn't blocking whatever port the VNC server is listening for connections on?[/QUOTE]
 uh yes, SP2 is installed.. and no I did not check the Windows firewall settings.. it's a new box and I haven't played a lot with it yet... I wouldn't be suprised there could be an issue with that... good call.. I'll check that out tonight too!

Thanks,
  Bristen.

---

### Post by Bristen Bourque on 2006-04-05
well first thing I did is check the WinXP firewall... I thought that was going to be it.. however, it still does the same thing and I made sure the firewall was off (it appeared to have been off from the start)...

When attempting to use "Terminal Server Client" I get the following error:
[INDENT]
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
[...copyright and URL lines snipped...]
VNC server supports protocol version 3.3 (viewer 3.3)
No authentication needed
Desktop name [...snip...]
Connected to VNC server. using protocal version 3.3
VNC server default format:
[INDENT]
32 bits per pixel.
Least significant byte first in each pixel.
True colour: max red 255 green 255 blue 255. shift red 16 green 8 blue 0
[/INDENT]
Can't cope with 24 bits-per-pixel. Sorry.
[/INDENT]

As far as the Remote Desktop Connection (krdc), I enter the WinXP box IP as follows: "vnc:/192.168.0.120:5900" (my server is not automatically detected), I would get the password dialog when the server had a password setup, but then a window would open and just close... no errors, nothing...

I did notice the RealVNC server was "RealVNC Server 4", so I imported the old 3.3 settings in case there was a version issue... this has not changed anything...

I could ping the VNC server machine, read files from shared folders on that machine, etc...  I'm still in the same jam I used to be.. help!

Thanks,
  Bristen.

ps: next, to install JRE and try web connection...

---

### Post by Bristen Bourque on 2006-04-05
couldn't find any Sun packages, so the JRE package couldn't be found in adept (or apt-get on command line). From the Unofficial Ubuntu guide, I was not able to get the JRE (j2re1.5)... any clues? Links I could go to for more information?

See this is what I don't like about Linux... is still very painful to get anything done... I've been programming for years (but have done very little sys admin stuff), but I still find this painfully slow.. I need this to work today, not in 3 weeks (or more) after countless hours of messing around *sigh*

Anyways, hopefully some kind person out there will know what's going on and let me know...

Thanks,
  Bristen.

---

### Post by Bristen Bourque on 2006-04-06
for whatever it is worth, I managed to get VNC working fine with DS Linux... I then however got errors with my hard drive... it appears that I got an error (that I don't understand)... something about "Inodes", "linked file", my hard drive needed to be manually fixed and needed to be remounted, etc etc... I've decided to reinstall Kubuntu 5.10 because I had messed around with it quite a bit (installed GNOME, XCFE various packages, etc etc)... since it was my first Linux install I'll restart from scratch.. I wouldn't be surprised that the VNC viewer will work fine after a reinstall.. I must of done something to break it (thinking this because DSL worked immediately)...

Bristen.

---

### Post by Bristen Bourque on 2006-04-07
update: reinstall Kubuntu 5.10 last night... today, I tried connecting to my WinXP box using "Remote Desktop Connection" (krdc) which is supposed to support VNC.  No luck, same as before! A window attempts to open and just closes...

So then I installed packages "vnc4-common" and "xvnc4viewer" from Adept... from Konsole, I start the viewer typing "vncviewer"... A dialog pops up, I type in the IP to my machine (which I can still ping and read files from shared WinXP folders)... when I click on the "ok" button on the dialog, I and error.  Here's the output I got from my terminal window:

[INDENT]
VNC viewer for X version 4.0 - built Apr 19 2005 04:20:29
Copyright (C) 2002-2004 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Apr  7 18:48:20 2006
 CConn:       connected to host 192.168.0.103 port 5900
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 main:        Error: couldn't find suitable pixmap format
*** glibc detected *** double free or corruption (out): 0x080bd308 ***
Aborted
[/INDENT]

Why does it work instantly with DamnSmallLinux?  Anybody going to help me out here?  Could I get somebody to at least say "I don't know what's going on"...?

Thanks,
  Bristen.

---

### Post by binarysleeper on 2006-04-07
> As far as the Remote Desktop Connection (krdc), I enter the WinXP box IP as follows: "vnc:/192.168.0.120:5900" 
I just used my krdc now and I input it differently. In your case it would be
```
192.168.0.120:0
``` no vnc:/ or anything.

the :0 indicates the screen/server you want to connect to and in windows this is always 0 unless you have a very special setup. You are specifying you want to connect to screen number 5900. It already knows the default vnc port. Give it a try and let me know how you get on.

HTH

---

### Post by Bristen Bourque on 2006-04-07
[QUOTE=binarysleeper]I just used my krdc now and I input it differently. In your case it would be
```
192.168.0.120:0
``` no vnc:/ or anything.
[...] Give it a try and let me know how you get on.
HTH[/QUOTE]

Hi HTH! Thanks for the reply... it's so strange... it still does the same thing.. a window tries to open, but closes immediately without any errors.. there's obviously something wrong somewheres, but I have no idea where the problem is yet... I'm a Linux newbie, so I have no idea where to start.. been fighting with this for a while now (like four days, average an hour or two per day)...

Anyways, any help would be greatly appreciated.. still works fine with DSL live CD, but still doesn't work in Kubuntu :(

Bristen.

---

### Post by binarysleeper on 2006-04-07
OK, re-reading your post and remembering back in the long long ago when there was only one VNC, I occasionaly experienced probs with colour depth mis-matches between the server and the viewer. I suspect in this case you will find that the Xwindow (KDE) colour depth is set to 24bpp (bits per pixel). Change it to 32 or 16 bpp, restart X (ctl +alt + backspace)  and I suspect your problem may disappear. You can probably confirm this by checking what colour depth DSL was running in.
Let me know if this sorts it.

Oh yeah, HTH = hope this helps. :)I'm actually Binarysleeper

---

### Post by Bristen Bourque on 2006-04-07
[QUOTE=binarysleeper]OK, re-reading your post and remembering back in the long long ago when there was only one VNC, I occasionaly experienced probs with colour depth mis-matches between the server and the viewer. I suspect in this case you will find that the Xwindow (KDE) colour depth is set to 24bpp (bits per pixel). Change it to 32 or 16 bpp, restart X (ctl +alt + backspace)  and I suspect your problem may disappear. You can probably confirm this by checking what colour depth DSL was running in.
Let me know if this sorts it.[/QUOTE]
 YOU'RE MY HERO!! I'm replying to you on my freshly installed Kubuntu notebook using a VNC connection to my WinXP box in krdc!! What's your address so I can send you some flowers or something!?!?  My notebook was in fact running at 24-bit depth... the vncviewer application did tell me an error about not knowing how to handle 24-bit color, but I did not understand the error... DSL almost certainly was using 16-bit color... Thank you so much!  I think krdc should be corrected to display an error message in this case.. it's very bizare that no error message was displayed!  Has this been reported as a bug yet? Probably a problem that happens often on older hardware such as my old beater ThinkPad i1200 (Celeron 500MHz, 192MB RAM and 6GB HD)...

[QUOTE=binarysleeper]Oh yeah, HTH = hope this helps. :)I'm actually Binarysleeper[/QUOTE]
 sorry, I can be an idiot at times LOL!

Well, thank you so much for your help! Ends up being a rather simple problem with an easy fix!

ps: I couldn't get myself to install WinXP on my notebook again heh

Bristen.

---

### Post by binarysleeper on 2006-04-07
No worries Bristen. It's always simple once you know the answer ;). If you hadn't run the vncviewer from the terminal, you'd never would have known what was wrong. Kudos for perservering. 

You may want to file a bug report on this, as it is likely to crop up again for others, and it should report an error rather than just quitting (rather like a badly written windows app:-k) . 

 You can file the bug with Ubuntu Bugzilla (top right link on this page) after checking one hasn't been filed already of course. Be as descriptive of the problem as possible and mention how to re-create it (i.e. have a client running in  24bpp).

Have fun VNCing

Cheers,

Binarysleeper

---

