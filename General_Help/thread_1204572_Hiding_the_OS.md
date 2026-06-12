---
title: "Hiding the OS"
date: 2009-07-04
forum: General Help
---

### Post by kayn786 on 2009-07-04
I am installing the latest Mythbuntu distro, and I am trying to make it so that it is impossible to access the command promt, or the desktop. Basically, I want the user of this computer to be able to do everything through shortcuts, and never have to (or be able to) even see what's going on in the background.

So for example, if I want to switch from the media player to the browser, I need only to press a shortcut and I will go to that "window."

I'm very good with computers, but a beginner to the wonderful world of Linux...  And for that reason I have no idea where to start. So if you can't help me out too much with this project I'm working on, then any help at all that you guys can provide will be very much appreciated. 

By the way, if your wondering, I am making this sytem for my family, and I dont want the kids (or some of the adults) to have access to anything at all. I also want the kids to be able to quickly understand everything, and be able to run it as if it were a tv or something simple like that. I even got a mce remote. ;)

Thanks in advance for any advice or help you can offer.

---

### Post by earthpigg on 2009-07-04
ive never used mythbuntu, but assuming you can find your way to the standard gnome interface (with applications, places, and system at the top of the screen), here is where i would start:

system -> administration -> users and groups. make a user that has very limited permissions, and no password.

system -> administration -> login window. set it so that the user you just created logs in automatically when the machine is started.

system -> administration -> lockdown editor. start locking things down.

edit:

system -> administration -> update manager. set it so it never bugs the user with system updates. you, the administrator, can check for these manually when you feel like it in system -> administration -> synaptic package manager -> reload.



edit2: nevermind. mythbuntu uses xfce, not gnome. all of my advice above is useless, lol.

---

