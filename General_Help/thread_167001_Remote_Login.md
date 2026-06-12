---
title: "Remote Login?"
date: 2006-04-27
forum: General Help
---

### Post by chris062689 on 2006-04-27
What would the purpose of remotly logging in?
Would it be kind of like VNC where you can directly access the desktop?
Or is it more of a console command line?

---

### Post by cgjones on 2006-04-27
It depends on what you have setup. You can install the OpenSSH server, and login remotely on the command line. OpenSSH can also be used graphically, provided that you have an X server on the local end. I haven't used it yet, but I'm pretty sure that Ubuntu can be setup to use VNC fairly easily.

---

### Post by chris062689 on 2006-04-27
Well,  Either way I would have to use a program correct?
It's just that the "remote login" is more-integrated within the system, than VNC.  (Right?)

So I would just have to launch a program and it would then show my screen (and alow me to move my mouse, keyboard, etc.) just like VNC?

---

### Post by aysiu on 2006-04-27
I have only a basic understanding of these things, so someone can correct me if I'm wrong, but based on my experiences, this is what I've seen:

A remote login via SSH is command-line, and you're actually logged in as a separate user from far away.

You can VNC into Ubuntu if you use rdesktop or tightvncserver, but that's not being logged in. It's controlling the screen using an already-logged-in user.

---

### Post by chris062689 on 2006-04-27
[QUOTE=aysiu]You can VNC into Ubuntu if you use rdesktop or tightvncserver, but that's not being logged in. It's controlling the screen using an already-logged-in user.[/QUOTE]

That's what I want.  Even if I do stuff like log off, would it kill the VNC server as soon as I log off of that user?

---

### Post by cgjones on 2006-04-27
chris: When you say "remote login", which program are you talking about. There are a number of different ways to login into a remote computer. Anyway you do it, you will have to start a specific program to connect to the remote computer.

aysiu: I'm not sure, but I think that rdesktop and VNC are seperate protocols. And a user doesn't need to be logged into the remote computer.

---

### Post by aysiu on 2006-04-27
[QUOTE=chris062689]That's what I want.  Even if I do stuff like log off, would it kill the VNC server as soon as I log off of that user?[/QUOTE] I think that's something you can set up with the VNC server. What I generally do if I have a VNC server set up is just log in and then lock my screen. Then, when I VNC in with a client, I just unlock the session, use the current login, and then when I'm done, lock the screen again.

[quote=cgjones]aysiu: I'm not sure, but I think that rdesktop and VNC are seperate protocols.[/quote] I've used rdesktop before to control my Ubuntu with my wife's Powerbook (using an open source VNC program for Mac called Chicken of the VNC), and it's worked just fine. They may be separate... protocols... but they achieve the same effect for the end user. > And a user doesn't need to be logged into the remote computer. That's what I said. SSH would be logging in. VNC would just be controlling an existing login.

---

### Post by cgjones on 2006-04-27
aysiu: Have you used rdesktop, or Chicken of the VNC to control Ubuntu from a Mac? And I should have said a user doesn't need to be logged in **at** the remote computer.

---

### Post by aysiu on 2006-04-27
[QUOTE=cgjones]aysiu: Have you used rdesktop, or Chicken of the VNC to control Ubuntu from a Mac?[/quote] Okay, first of all, I have to say I'm not 100% sure the application name is *rdesktop*, but it *is* the "Remote Desktop" option in Ubuntu. 

**Edit**: Yeah, it's not *rdesktop*. Apparently, it's *vino*, whose package description is *VNC server for GNOME*. I found out by running the *top* command in terminal and saw that *vino-server* was hogging up all the CPU.

And, yes, I've controlled Ubuntu from a Mac using Chicken of the VNC, and it works just fine. > And I should have said a user doesn't need to be logged in **at** the remote computer. Oh. Good thing to know.

The attached image is me using a Windows XP computer to VNC (using TightVNC Viewer) to another Windows computer running a Hoary live CD. And this is the option (highlighted in red) I used to share the desktop with Windows.

---

### Post by cwaldbieser on 2006-04-27
[QUOTE=cgjones]chris: When you say "remote login", which program are you talking about. There are a number of different ways to login into a remote computer. Anyway you do it, you will have to start a specific program to connect to the remote computer.

aysiu: I'm not sure, but I think that rdesktop and VNC are seperate protocols. And a user doesn't need to be logged into the remote computer.[/QUOTE]
rdesktop uses the RDP protocol.  You use it to log into Windows XP Pro or Windows Server boxes.

VNC is a more widespread protocol.  There are VNC servers for Windows, Linux, Mac OS9 and Mac OS X.

---

### Post by aysiu on 2006-04-29
This is a screenshot of Chicken of the VNC controlling Ubuntu from Mac OS X.

---

