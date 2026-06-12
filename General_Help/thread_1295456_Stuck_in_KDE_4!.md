---
title: "Stuck in KDE 4?!"
date: 2009-10-19
forum: General Help
---

### Post by daldude on 2009-10-19
I seem to be stuck in the KDE 4 display manager interface. When I boot up it comes up with a blue background screen and my 2 users I set up as Icons that can be clicked to select the one to log on as. After logging on to a user it comes up to the GDM Desktop that I'm used ( I guess)
but if I go to shutdown it only gives me the options to Switch Users, Log Out, Suspend or Hibernate and if I select Switch Users it gives me this message

GDM (GNOME Display Manager) is not running.

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead.
I get the same message if I click the Login In Window option under Administration.

if I want to shutdown or reboot I have to first select Log Out and then use the KDE menu to reboot Shutdown or switch users.

I tried clicking the Menu Button on the KDE 4 log in screen and then selection Session type as GDM GNOME but it still comes back to the KDE 4 log in screen after I reboot even if I relog on after selecting Session type GDM (GNOME).

I also tried recovery mode at the boot manager that comes up before any operating system loads.



It's very annoying:mad:
 

How do I fix it:confused: 

Thanks :)

---

### Post by oldos2er on 2009-10-19
```
sudo dpkg-reconfigure gdm
```

---

### Post by daldude on 2009-10-19
That did the trick! THANKS!!:):guitar:

Now I can stop pulling my hair out:grin:

What could have caused it to switch to KDE 4? I don't remember changing it in any way because I had no Idea there were different display managers or that there was such a thing as a display manager until I had this problem.

Why does KDE have so much limitations in what you can do?

---

### Post by oldos2er on 2009-10-19
Did you install kubuntu-desktop? If so, I think that pulls in kdm as a dependency. I am not as familiar with KDE as I am with Gnome, so I'm not sure about its "limitations."

---

