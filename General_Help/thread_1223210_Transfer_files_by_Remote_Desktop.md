---
title: "Transfer files by Remote Desktop"
date: 2009-07-25
forum: General Help
---

### Post by Vignesh S on 2009-07-25
I am just wandering if I can transfer files between the host system and the remote desktop, regardless of the OS e.g. Fedora to Ubuntu, Ubuntu to Windows XP at school, etc.

---

### Post by cbraxton on 2009-07-25
> **Vignesh S said:**
> I am just wandering if I can transfer files between the host system and the remote desktop, regardless of the OS e.g. Fedora to Ubuntu, Ubuntu to Windows XP at school, etc.

You can do it with VNC. I use x11vnc server on linux, UltraVNC Viewer running under wine on linux, and UltraVNC full installation (both server and viewer) on Windows systems. With this setup you have full desktop control and file transfer capability cross-platform.

---

### Post by Vignesh S on 2009-08-08
Can I transfer files with the VNC viewer at school, because I can't exactly install random stuff onto the school computers. Is it even necessary to have a server on the viewing computer?

Don't exactly get how the whole setup is going to be like.

---

### Post by Vignesh S on 2009-08-12
OK, I really have no idea how to set this up. Can anyone tell me how to? And is there any way to avoid that annoying popup come up telling me that someone is trying to access my computer remotely even though its only me?

---

### Post by krunge on 2009-08-12
> **Vignesh S said:**
> OK, I really have no idea how to set this up. Can anyone tell me how to? And is there any way to avoid that annoying popup come up telling me that someone is trying to access my computer remotely even though its only me?
Which VNC programs are you trying to run? (on both local and remote sides)

---

### Post by Vignesh S on 2009-08-12
Probably RealVNC. But since I have to pay for the Linux version of the server, are there any other free servers out there? If not, I can always settle for the Enterprise version of RealVNC

---

### Post by krunge on 2009-08-13
> **Vignesh S said:**
> Probably RealVNC. But since I have to pay for the Linux version of the server, are there any other free servers out there? If not, I can always settle for the Enterprise version of RealVNC
I've never used enterprise (or non-free) version of RealVNC, so I can't help with that.

x11vnc/Unix + (UltraVNC/Windows or TightVNC/Windows) can do file transfer.  I can help with that.

x11vnc/Unix + Browser-with-Java/Windows can do file transfer (ultravnc) too.  

The 2nd one is a little tricky due to the java applet viewer, but it can be done.  Note that this  2nd one involves **no** software install on the Windows viewer side (besides Java in the browser.)

BTW, why don't you just use Putty or SSH/SCP for remote file transfer?

---

### Post by Vignesh S on 2009-08-14
Of the options you have given to me, krunge, I'd say the first one. It is hardly an issue to carry around portable TightVNC / UltraVNC on my USB. Couple of questions on my part though:

1. Is it possible to access the computer without that annoying dialog box coming up asking if it alright for me to remotely access the computer? I can't always have a person at my home pressing the accept button while I am out and about

2. Would this file transferring solution be better than setting up a network at my home? I know that it might be easier, since there are Windows and Ubuntu computers to network, but would it be better, or am I better off setting up a network here?

But yeah, I'm ready for the tutorial.

---

### Post by stereomuffin on 2009-08-14
Not sure if this is of any help but if you have Remote Desktop enabled on XP for instance and use tsclient on ubuntu you can remotely map your ubuntu drive.

I have added a screenshot..

---

### Post by Vignesh S on 2009-08-14
Does that feature also exist under Vista or for that matter, Windows 7 Release Candidate?

---

### Post by Vignesh S on 2009-08-14
Does that feature also exist under Vista or for that matter, Windows 7 Release Candidate, stereomuffin?

---

### Post by Vignesh S on 2009-08-16
Alright, krunge, all I want to know is how to set up the VNC network, so that I can access and transfer files between computers. The OS's I have here are: Ubuntu 9.04, Windows XP Home Edition, Windows XP Professinal (the OS at school), and Windows Vista (probably Business).

---

### Post by krunge on 2009-08-16
> Alright, krunge, all I want to know is how to set up the VNC network, so that I can access and transfer files between computers. The OS's I have here are: Ubuntu 9.04, Windows XP Home Edition, Windows XP Professinal (the OS at school), and Windows Vista (probably Business).
OK.

BTW, if not all machines are on the same LAN, we may have to play with enabling connectivity via your router.  I assume this is not a problem for now.  I.e. we get it working on the LAN first.

Run x11vnc on the linux machine like this:
```
x11vnc -rfbport 5900 -ultrafilexfer -display :0
```
(Note: you don't need the "-display :0" if you run x11vnc from a terminal inside the display :0 X session.)

If running that fails, upload the full x11vnc printout to this thread.

Next, install UltraVNC Viewer version 1.0.5 or later on the Windows machine and then connect from it to VNC display 0 on the linux machine (e.g. "linuxbox:0" if the ubuntu machine is named "linuxbox", or if there is no name lookup for it use the IP, e.g., "192.168.X.Y:0")

Once connected, you should be able to click on 'Open File Transfer...' in the UltraVNC viewer and transfer files back and forth.

This is clearly not the best way to do file transfer, especially if it is over a fast LAN, but it should give a point-and-click interface to it.

Let me know how it goes.

---

