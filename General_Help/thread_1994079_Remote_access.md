---
title: "Remote access"
date: 2012-06-02
forum: General Help
---

### Post by Mex5150 on 2012-06-02
Hi all

(apologies if this is in the wrong place, or been covered before, I did search but found nothing of use)

What I want to do: Connect to my Ubuntu (11.10) desktop via my Fedora (14) laptop so I can edit/move/rename files while I am not at home.

What I can do: connect via local network with Vinagre, and Remmina. Not tried over the Internet as there are problems that need fixing first.

Problems:
1) Although I can connect, click on things, and see the desktop, the desktop does not update. I think this may have something to do with Compiz, I read about a workaround, but this didn't help, so it may be caused by something else.

2) I can only connect after clicking OK on the desktop (something I obviously will not be able to do if I am trying to access it from afar).

Any ideas on how to fix these problems (or indeed do the whole thing in a better way)?

-Mex

---

### Post by TheFu on 2012-06-02
Using a GUI over the internet is a little more involved and requires significantly more bandwidth.

A few options:

a) The easiest way with the least bandwidth and greatest security is to use ssh or scp or sftp.

b) If you **must** have a GUI, then you need either an ssh-tunnel or a VPN of some kind to run a GUI client/server program inside.  Google "vnc ssh tunnel" for step by step instructions. Using FreeNX and an NX client would be a good idea too.  I use FreeNX whenever possible. It includes an ssh-tunnel and is much more efficient compared to either RDP or VNC protocols.  For VNC, I've never tried either of those tools - I just use vncconnect myself.  This requires a little setup on the "server side" so a desktop is running or a terminal is available.  For any VNC connection over the internet, be certain you use a tunnel.

c) Setup access to your files using apache or some other webserver tool. There are pretty heavy security issues doing this.

If you have allowed samba or smb access over the internet, that is a **really, really, really BAD idea.**

ssh is the best way to do this stuff over the internet.

---

### Post by Mex5150 on 2012-06-02
> **TheFu said:**
> Using a GUI over the internet is a little more involved and requires significantly more bandwidth.I am aware of this, and my skills are improving, but I still need to use the GUI for a lot of stuff.

> A few options:

a) The easiest way with the least bandwidth and greatest security is to use ssh or scp or sftp.See above.

> b) If you **must** have a GUI, then you need either an ssh-tunnel or a VPN of some kind to run a GUI client/server program inside.  Google "vnc ssh tunnel" for step by step instructions. Using FreeNX and an NX client would be a good idea too.  I use FreeNX whenever possible. It includes an ssh-tunnel and is much more efficient compared to either RDP or VNC protocols.  For VNC, I've never tried either of those tools - I just use vncconnect myself.  This requires a little setup on the "server side" so a desktop is running or a terminal is available.  For any VNC connection over the internet, be certain you use a tunnel.Sounds like what I'm after.

> c) Setup access to your files using apache or some other webserver tool. There are pretty heavy security issues doing this.This never even crossed my mind, but I think option two sounds better for me.

> If you have allowed samba or smb access over the internet, that is a **really, really, really BAD idea.**Not done anything over the internet so far,  I've just been trying to get it working on the local network.

> ssh is the best way to do this stuff over the internet.Great, now I have something to start researching (this is often the biggest problem with Linux, I know what I want to do, but have no idea how to start researching it).

Do you know any good tutorials on this?

-Mex

---

### Post by steeldriver on 2012-06-02
this one seems pretty good - the only thing I don't think it mentions is connecting to a remote system that uses a non-default ssh port (which won't be an issue for you if you are setting it up yourself)

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_11.04_Unity_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_11.04_Unity_Desktop)

it is a bit unity-specific to start but after that everything is generic

fwiw the Vinagre VNC client *supposedly* allows you to set up the ssh tunnel right in the connect gui but I've *never* got it to work for me - possibly because the remote system *is* using a non-default port and there doesn't seem to be anywhere in the GUI to specify that

good luck

---

### Post by TheFu on 2012-06-03
> **Mex5150 said:**
> Great, now I have something to start researching (this is often the biggest problem with Linux, I know what I want to do, but have no idea how to start researching it).

Do you know any good tutorials on this?

-Mex
A Google for "ssh tunnel vnc" found this: [http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)  Hopefully, that will help. Often, using the generic protocol will find solutions where using a specific program in your search does not.

However, if your client platform supports NX, I'd use that over rdp or vnc.  That means some nx-client and an nx-server need to be loaded and configured on the client and the server systems.  FreeNX is the server I run. It works well even on low bandwidth connections, with a tunnel built-in AND it is very efficient compared to other alternatives.  The down-side is no android client that I've found, but non-portable platforms are pretty well supported.  I'm running it on a 10.04 box - 12.04 is too new for me. I prefer LTS.  It has been a few years, but I think it was just adding the PPA for the server and 'apt-get install'.  Newer releases any not be as easy - I don't know.

---

