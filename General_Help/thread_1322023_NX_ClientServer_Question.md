---
title: "NX Client/Server Question"
date: 2009-11-10
forum: General Help
---

### Post by JafoFubar on 2009-11-10
Hi all,
I'm new to Ubuntu but not new to computers. I've installed 9.10 and need to be able to remote to it from Windows boxes. VNC does what I want it to but it's slow and not very secure. I heard about NX Client/Server so I thought I'd try that. I've got it working but I can't interact with the user on the remote pc. I can remote to the client and control it fine but the user at the remote computer can't see what I'm doing and I don't see what they're doing on my screen. Their screen doesn't change when I do something and mine doesn't change when I do something. Although if I fire up a music video or something, they can hear it on their speakers but still nothing on the screen. Shadowing seems to only shadow another NX session and not the remote user's session. 

My question, is there a way to interact with a user on a remote Ubuntu computer using NX Server/Client? Or is this not what NX Clent/Server is designed for? 

No, I'm not trying to spy on them! I'm trying to get our small company off of Windows and (free) remote support is needed. 

Thanks in advance for any help!

---

### Post by prem1er on 2009-11-10
That's because NX client opens its own session. It is not a remote desktop, it is a running a seperate instance of the desktop manager.

---

### Post by JafoFubar on 2009-11-10
> **prem1er said:**
> That's because NX client opens its own session. It is not a remote desktop, it is a running a seperate instance of the desktop manager.

Thanks for the quick reply. 
That's what I thought was going on but I was wondering if there was a way to configure it as a remote desktop. Even if I use the same username and password in NX as I do in Ubuntu to remote to the Ubuntu computer, it still opens a new nx session.....same wallpaper, same icons, same everything...but I can't interact with the user. Very weird way of doing things! 
Thanks!

---

### Post by prem1er on 2009-11-10
It's not a weird way of doing things, it is the way it was meant to be used, so you can have multiple users logging into a single server all with secure remote access. One negative about this is that it is very resource intensive with all the encryption that takes place. If you want remote desktop than allow remote desktop in the client machine and install a remote desktop client on your machine.

---

### Post by JafoFubar on 2009-11-10
Ok. Thanks. I guess it's not what we're looking for.

---

### Post by JafoFubar on 2009-11-12
Nobody else have any thoughts? To go from a Ubuntu pc to a Windows pc, rdesktop works great. So there's nothing like that to go from a Ubuntu pc to another Ubuntu pc? (besides VNC)
Thanks

---

### Post by ricojonah on 2009-11-17
Unless I'm misunderstanding this information from the FreeNX project, shadowing / remote / shared desktop using NX **is, in fact,** very possible: 

See [http://openfacts2.berlios.de/wikien/index.php/BerliosProject:FreeNX_-_HowtoShadow#Session_shadowing]("http://openfacts2.berlios.de/wikien/index.php/BerliosProject:FreeNX_-_HowtoShadow#Session_shadowing")

Unfortunately, I'm fairly new to using NX (I love it!), and haven't had much time to try the suggestions from the wiki myself. (I left off unable to find the "shadow" option from the NX client--perhaps there was a change to the newer versions of the client software which removed this GUI option?).

Anyway, check out that link above--it may give you some insight on configuring the shared desktop ability that you're seeking.

Oh, and if you get it working, please post back with instructions on how you did it. Thanks!

---

### Post by JafoFubar on 2009-11-17
Sharing a remote desktop with FreeNX is possible and it works fine, just not the way I want it to. You can't share the host desktop but you can share an NX session. When you connect to the NX server, that session can be shadowed...by more that one person if you choose. For shadowing, when you go to Applications/Internet/NX Client for Linux and open NX Client for Linux, click on the Configure button and change the Desktop to Shadow and point it to the server IP (in the Host box) and it will come up with a list of sessions on that server, pick one and connect. 

As for my questions above, I can just use Remote Desktop viewer to see another Ubuntu box. That's fine for me for now.

---

