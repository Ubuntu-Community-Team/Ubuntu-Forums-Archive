---
title: "GUI connect to remote server via SSH?"
date: 2012-09-05
forum: General Help
---

### Post by t0p on 2012-09-05
In the last LTS (10.04?) I used the utility under the Places menu (sorry, can't recall its name) to connect via SSH to my shell account on a remote server.  That allowed me to do simply transfer files copy n paste from one computer to the other, the tool automatically doing the SFTP stuff etc.

Now I'm running 12.04, and have the "ClassicMenu Indicator" on my top panel. That's the only place I can find to allow GUI SSH connection to the server - Remminer Remote Desktop Client.  Except it doesn't seem to work.  I created a new connection,  with my login name,  protocol SSH (also tried SFTP), server name, password authentication, and when I try to connect I get 

```
Failed to startup SSH session: Failed to resolve hostname server.org (Name or service not known)
```Obviously the server isn't called server.org.  But Remminer isn't able to resolve the hostname.

I'm confused by this.  In the 10.04 utility I identified the server as "server.org" and I had no problem connecting.  Then I could copy and paste, run programs remotely, via SSH and SFTP (which I didn't have to specify each time - it just *did* it.

I can still connect to the server using command line, ie.

```
ssh -l username server.org
```but I haven't learnt all the intricacies of command line SSH and SFTP; and I really don't feel I should have to.  The Places thing in 10.04 worked fine - is there a way I can get that back?

There's also this "Character set" drop-down menu, with loads of options.  Excuse me for being a n00b who should go and RTFM... but I don't know what I'm supposed to choose.  The server runs a BSD variation, FreeBSD or NetBSD, I don't know for sure... and I don't see why I should have to know.  The utility in 10.04 did all this automagically - why has the magic been removed?

Can anyone please tell me what I'm supposed to do here?  Or maybe how to use the old program?  This is severely annoying!

Cheers.

---

### Post by cryptotheslow on 2012-09-05
On 12.04 here Nautilus (the default file explorer) has a "Connect to Server..." entry in its File menu that gives the option to use SSH to connect to a remote server. Works fine for me.

---

### Post by t0p on 2012-09-05
> **cryptotheslow said:**
> On 12.04 here Nautilus (the default file explorer) has a "Connect to Server..." entry in its File menu that gives the option to use SSH to connect to a remote server. Works fine for me.
  
Heh heh thanks cryptotheslow.  The new GUI setup in 12.04 (Unity) has completely thrown me after the old Applications, Places and System menus.  I checked out the File menu in the file manager and, yes, I can connect just fine!

Thanks!!  :D

---

