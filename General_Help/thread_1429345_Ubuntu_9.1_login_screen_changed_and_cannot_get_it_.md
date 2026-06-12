---
title: "Ubuntu 9.1 login screen changed and cannot get it back"
date: 2010-03-13
forum: General Help
---

### Post by antman8969 on 2010-03-13
[IMG]http://img121.imageshack.us/img121/6083/img00105p.jpg[/IMG]

That's a picture of my ubuntu 9.1 64bit login screen. The background image I changed myself months after this problem started, so I'm sure that has nothing to do with it. 

What I DID do that caused this problem was follow the openoffice dark theme fix on this page:

[http://www.gnome-look.org/content/show.php/Openoffice+fix+for+slickness+black+theme?content=77415]("http://www.gnome-look.org/content/show.php/Openoffice+fix+for+slickness+black+theme?content=77415")


BACKGROUND:
I installed a dark theme that made the openoffice word page black, so I had to find a fix for it on the page above. I'm not using the theme anymore, but it was "Slickness black" on gnomelooks. 

In case someone didn't see a problem with the orginal login screen, the section where you click the username and enter your password should look like this:

[IMG]http://1.bp.blogspot.com/_FJH0hYZmVtc/St9cR6HgRgI/AAAAAAAAD9k/l0G4tKA18d0/s400/Capture.PNG[/IMG]

Also incase anyone was going to ask, my login DID look like the second picture at one point (before the openoffice fix)

I just removed openoffice completely and reinstalled it so that isn't the solution....any ideas?

---

### Post by Mr Nemo on 2010-03-14
Reinstalling gdm from synaptic should set it back to the original login screen.

---

### Post by antman8969 on 2010-03-14
> **Mr Nemo said:**
> Reinstalling gdm from synaptic should set it back to the original login screen.

hm, well I tried marking all of the installed packaged that turned up in the 'gdm' search for reinstallation but that didnt work. I'll try actually uninstalling and reinstalling and see how that goes.

---

### Post by nitstorm on 2010-03-14
Maybe this link could help?

[http://superuser.com/questions/113185/ubuntu-9-10-how-to-repair-login-screen-without-reinstalling-gdm](http://superuser.com/questions/113185/ubuntu-9-10-how-to-repair-login-screen-without-reinstalling-gdm)

---

### Post by antman8969 on 2010-03-14
> **nitstorm said:**
> Maybe this link could help?

[http://superuser.com/questions/113185/ubuntu-9-10-how-to-repair-login-screen-without-reinstalling-gdm](http://superuser.com/questions/113185/ubuntu-9-10-how-to-repair-login-screen-without-reinstalling-gdm)

the reinstall didn't work for whatever reason.

I kept looking and found this link:

[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html")

it explained how to edit the themes of the login screen which told me that the 'human theme' was not installed. So I logged in and installed the theme via synaptic and wala! it was back. AND I could edit the colors and everything as well.

So the next question... how do I mark this thread solved lol?

---

### Post by nitstorm on 2010-03-14
Near the top right something called thread tools. That's how u can mark it solved and congrats on finding the solution :)

---

