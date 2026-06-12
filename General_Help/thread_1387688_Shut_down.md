---
title: "Shut down"
date: 2010-01-22
forum: General Help
---

### Post by knubles on 2010-01-22
Where have the preferences gone
The ones that I mean are the ones associated with the applet
in the top right hand side.
Particularly the the shut down box on/off.
Thanks

---

### Post by Saiko Berry on 2010-01-22
...? What?

You're missing your user/session control thingy on Fail-panel?

Try opening terminal and typing [FONT=monospace]
[/FONT]
sudo shutdown -P now

---

### Post by bluefrog on 2010-01-22
gconf-editor
/apps/indicator-session/suppress_logout_restart_shutdown

---

### Post by knubles on 2010-01-23
Thanks for the replies.
Unfortunately the gconf item did not kill the appearance of the shut-down box and the waiting time of 60 seconds.
I think I should have said that I am using 9.10.
Thanks.

---

### Post by Jackzor on 2010-01-23
What exactly do you want to do?

---

### Post by knubles on 2010-01-25
Saiko Berry
Thanks for the reminder about the command line. A small script a I had a workaround.

Jackzor
I wanted to close down without the shut down box showing. Like I could in 9.04.

Thanks to everybody.

---

