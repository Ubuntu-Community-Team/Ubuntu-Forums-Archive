---
title: "Start Program in system tray"
date: 2010-08-04
forum: General Help
---

### Post by Axel-P on 2010-08-04
Hi!

I would want to know, I have Korganizer starting when I open my machine. I would want to know if there's any way to do the same but instead of being "open" I would want it to start already minimized in the system tray. Anyone know how to do so?


Thanks!

---

### Post by Axel-P on 2010-08-05
Bump?

---

### Post by ankspo71 on 2010-08-05
Hi,
Here's two things to try. 
Install "alltray" then change your korganizer startup command to:
```
alltray korganizer
```
I don't know how well alltray worked in Kubuntu Lucid, but it's crashing on me in Kubuntu Maverick-(aplha), so I have another idea below.

KDE has a native application called ksystraycmd that can be used.
```
ksystraycmd --hidden korganizer
OR
ksystraycmd --hidden --startonshow --keeprunning korganizer
```

See which command works better for you. You can also type "ksystraycmd --help" in the Konsole (terminal) to find more options for ksystraycmd.
Hope this helps.

---

### Post by ankspo71 on 2010-08-05
Hi again.
If neither of those options above work well for you, I was just thinking that you could create a 'window rule' to have korganizer open up on one of your other desktops. Then all you need to do is click on your pager in the panel to access korganizer.

To create window rules go to Applications > Settings > System Settings. Then look for the  Window Behavior > Window Rules.

---

### Post by Axel-P on 2010-08-05
Actually the first one worked :)

Thanks!

---

### Post by softappstudio on 2012-10-16
> **ankspo71 said:**
> Hi again.

To create window rules go to Applications > Settings > System Settings. Then look for the  Window Behavior > Window Rules.

I wish to do the same, but I run a Gnome desktop so the above instructions do not directly apply. Can anyone advise  me how I might achieve the same under Gnome, so I can[B] force a programme (KOrganizer) to open on a specified workspace?
[/B]
Thanks,
--Grahame

---

