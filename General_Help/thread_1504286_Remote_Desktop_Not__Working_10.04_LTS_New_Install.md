---
title: "Remote Desktop Not  Working 10.04 LTS New Install"
date: 2010-06-07
forum: General Help
---

### Post by I Use Dial on 2010-06-07
I just did a fresh install of 10.04 on my 64-bit system.  VNC worked great before I installed all of the recommended updates.  After that when I try to connect from my XP machine using TightVNC is says Status: Connection established.  But it never actually connects.  It just hangs there.

I can use SSH just fine and remote XDMC session no problem.

Any suggestions form e?

---

### Post by I Use Dial on 2010-06-10
Polite 'bump'.

---

### Post by I Use Dial on 2010-06-13
So here we have the standard response that I always get from the Ubuntu 'community', which is no response.  It seems like any problem I have with this software I can't get any help for.

Upgrades are incredibly irritating: fix one thing, break another.  The last time I upgraded Ubuntu was 8.04.  The 'only' thing wrong with it was that remote XDMCP login was not working, which, of course, no one here was able to help me with either.

With 10.04 I've traded no remote XDMCP for no VNC.  Given the option, I'd rather have a remote desktop to a remote session.

Thanks guys.  Thanks for giving me a worse product on upgrade and no support.  You're amazing.

---

### Post by an0dos on 2010-06-13
> **I Use Dial said:**
> Thanks guys.  Thanks for giving me a worse product on upgrade and no support.  You're amazing.

Try to be civil.

Have you tried disabling desktop effects on the remote desktop?

Have you checked out [FreeNX]("https://help.ubuntu.com/community/FreeNX")? It is SSH-based and therefore more secure than VNC.

---

### Post by Jimmythepad on 2010-07-11
Any update on this. I have a similar/the same problem. I can ssh in using remote desktop viewer but it won't let me connect using vnc. Its a windows xp machine I'm trying to connect to and have been doing so with no problem from vista.

---

### Post by scottuss on 2010-07-14
> **I Use Dial said:**
> So here we have the standard response that I always get from the Ubuntu 'community', which is no response.  It seems like any problem I have with this software I can't get any help for.

Upgrades are incredibly irritating: fix one thing, break another.  The last time I upgraded Ubuntu was 8.04.  The 'only' thing wrong with it was that remote XDMCP login was not working, which, of course, no one here was able to help me with either.

With 10.04 I've traded no remote XDMCP for no VNC.  Given the option, I'd rather have a remote desktop to a remote session.

Thanks guys.  Thanks for giving me a worse product on upgrade and no support.  You're amazing.

Ask for a refund... oh wait...

---

### Post by scottuss on 2010-07-14
OK, the reason is, I think, that the Vino starts when you log into the machine through gdm (the login window) and not before.

I fixed this by removing Vino and using x11vnc server, you can use the following command to start the server ready for connections:

x11vnc -display :0 -auth /home/USER/.Xauthority

Probably put it somewhere so it starts without having to log in

---

### Post by krunge on 2010-07-14
> OK, the reason is, I think, that the Vino starts when you log into the machine through gdm (the login window) and not before.

I fixed this by removing Vino and using x11vnc server, you can use the following command to start the server ready for connections:

x11vnc -display :0 -auth /home/USER/.Xauthority

Probably put it somewhere so it starts without having to log in
If one wants x11vnc to export the login screen (i.e. before anyone logs in) he will need to run the command as root and replace /home/USER/.Xauthority with the one gdm is using.

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

---

