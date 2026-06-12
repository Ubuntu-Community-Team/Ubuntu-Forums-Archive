---
title: "Conky and sudo commands"
date: 2012-02-26
forum: General Help
---

### Post by MadsRC on 2012-02-26
I have a section of my Conky that requires either the command to be run with sudo, or conky to be started with sudo.

Is there any way, to either have the sudo pw in the conky script (which would be kinda stupid as it would be stored in plain text...)?

or, would it be possible to run conky, on startup, with sudo and the pw enable by gnome keyring or something?

I guess the last solution would be to have conky ask for the sudo pw when it automatically starts up on bootup... But that's kinda tedious...

---

### Post by mcduck on 2012-02-26
I'd say the best way would be to make your command a separate script of it's own, and add it to your bootup scripts so it get automatically started and with root privileges. Then juts make the script output it's results to a text file from which Conky can read them.

That way you'd avoid having to continuously run an application on your desktop with root privileges, and you wouldn't need any password confirmation either.

---

