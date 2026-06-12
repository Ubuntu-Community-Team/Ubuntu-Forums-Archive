---
title: "Having trouble with Remote Desktop in 9.04"
date: 2009-08-03
forum: General Help
---

### Post by ninjapirate89 on 2009-08-03
Ok I had this working in 8.10 and then reinstalled when 9.04 first came out and I haven't bothered to reconfigure it since. Anyway, I have 9.04 on my desktop and my laptop and I want to be able to have remote access only on my local network. 
My settings for remote desktop are:
Allow other users to view your desktop
Allow other users to control your desktop
Require the user to enter this passord
Configure network automatically to accept connections
ONly display an icon when there is someone connected

With these settings it tells me "Your desktop is only reachable over the local network. Others can access your computer using the address localhost.

On my laptop I go to Applications -> Internet -> Remote Desktop Viewer and use the local ip from my desktop to try and connect but it says "Connection to host 192.168.1.69:5900 was closed."

Are there more settings somewhere that I should change?

Both computers are connected through wireless if that makes any differencec.

---

### Post by wojox on 2009-08-03
Try Places > Connect to Server

---

### Post by ninjapirate89 on 2009-08-03
> **wojox said:**
> Try Places > Connect to Server

When I do that I am given the choice of:
SSH
FTP (with login)
Public FTP
Windows Share
WebDAV (HTTP)
Secure WebDAV (HTTPS)
and 
Custom Location

Which would I need in this case? I tried SSH but it didn't connect.

---

### Post by wojox on 2009-08-03
Ooops, I guess you have gui's on both. Sorry I have a headless server I can ssh into that way. How about opening nautilus and clicking network. Does it see it?

---

### Post by ninjapirate89 on 2009-08-03
> **wojox said:**
> Ooops, I guess you have gui's on both. Sorry I have a headless server I can ssh into that way. How about opening nautilus and clicking network. Does it see it?

If I go through network I can see my desktop but the only thing I can connect to is my shared external hard drive.

Edit -> And yeah I am using a gui on both.
Edit2 -> Under Remote Desktop on my desktop, where it says "Your desktop is only reachable over the local network. Others can access your computer using the address localhost." localhost is a link and if I click on it, it opens says vnc://localhost::5900
I tried using this under the Remote Desktop Viewer on my laptop and it still didn't connect.
Edit3 -> Also tried that address in Connect to server using custom location and that didn't work either.
Edit4 -> Hmm..followed this link I found on Google [http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop) and installed vncviewer and I can't connect using that either.

---

### Post by ninjapirate89 on 2009-08-03
Ok I booted into Vista *shudder* and installed tightvncserver and I can connect to it just fine. Any ideas what the problem could be?

---

### Post by ninjapirate89 on 2009-08-03
Solved....not the way I would have liked it, but it works.

I installed tightvncserver on my desktop.

sudo apt-get install tightvncserver

then ran tightvncserver and configured a password

Then I used Remote Desktop Viewer from my laptop and connected to 192.168.1.69:1 and it worked. Don't know why the default Remote Desktop isn't working right for me. I would have preferred to use it.

---

### Post by wojox on 2009-08-03
No idea. How's it look in tightvncserver?

---

### Post by ninjapirate89 on 2009-08-05
Tightnvcserver made it work for me....kinda...it doesnt quite work right though so I removed it and gave up.

When it connected to my desktop I couldn't see the windows that I already had open on it for some reason.

---

### Post by bodhi.zazen on 2009-08-05
There are different VNC servers. Some connect to a shared X session , so you get the same screen on both client and server.

Some vnc servers when you connect with a client you get a new vnc (X) session, independent from the user loged into the server.

The default vnc server is vino. For vino to work you must be logged into the server. You then connect with "Remote Desktop Viewer".

---

### Post by mark.0 on 2010-12-08
I have this EXACT problem as well. Very frustrating. Displays "Your desktop is only reachable over the local network. Others can access your computer using the address localhost."

What's the point of a remote session if it's from localhost?!

Isn't there a way to fix this? I'd really like to be able to use the remote desktop viewer

---

### Post by bodhi.zazen on 2010-12-08
> **mark.0 said:**
> I have this EXACT problem as well. Very frustrating. Displays "Your desktop is only reachable over the local network. Others can access your computer using the address localhost."

What's the point of a remote session if it's from localhost?!

Isn't there a way to fix this? I'd really like to be able to use the remote desktop viewer

VNC, or remote desktop as you are calling it, is the #1 security breach on these forums.

Because of that it is best of you are "forced" to enable it to allow remote connections, IMO at least.

I know it is frustrating, but please understand the security implications of what you are doing. Otherwise you next post is likely to be one complaining about how Ubuntu sucks because you were cracked.

At any rate, I highly advise you use Freenx or vnc over ssh.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

With ssh, use keys and disable passwords.

---

