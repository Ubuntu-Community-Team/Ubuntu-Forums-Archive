---
title: "edit program launcher"
date: 2011-12-26
forum: General Help
---

### Post by sn0m on 2011-12-26
Hi
is there a way to edit program launcher in menu.
I have created a skype-webcam-fixed file in /usr/bin and want to change from /usr/bin/skype to /usr/bin/skype-webcamfixed-launcher.
It used to be done by going in system-preferences and right click and edit but not sure how to do that in oneric.
Thanks
Sokol

---

### Post by VCoolio on 2011-12-26
You can link /usr/bin/skype to /usr/bin/skype-fixed. So you can keep using the command 'skype'. Or edit the launcher. Those are .desktop files, either in /usr/share/applications or in ~/.local/share/applications. If it's in the former:

cp /usr/share/applications/skype.desktop ~/.local/share/applications/

Then edit it (the one in your home folder will then overrule the one in the system directories). Change the Exec= line to whatever you need. Logout and back in to let the menu know what you've done.

---

### Post by koftis on 2012-01-17
if you want you can view my vid in you[tube]("https://www.youtube.com/watch?v=WeaLCzB4qy8")

and rate it if you want its my first one..

its in Greek but i think you can understand it..;)

I've also added Eng Subs.

---

