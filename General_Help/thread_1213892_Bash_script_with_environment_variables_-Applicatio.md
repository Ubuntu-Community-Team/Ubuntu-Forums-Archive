---
title: "Bash script with environment variables -Application launcher"
date: 2009-07-15
forum: General Help
---

### Post by offman on 2009-07-15
Hi

I have a bash script where I use EXPORT to set some environment variable. I know if I source it or call it like this ". ~/shellscript.sh" it will set these variables globally.
But is there a way of creating an application launcher for this so it sets the variables properly?

cheers

---

### Post by Brandon Williams on 2009-07-15
Are you trying to get the variables into your login environment? Or are you trying to get them into the environment when you launch some specific application?

If you want them in the environment in your window manager login environment, create a file called ~/.xprofile and put the variable export commands in that file.

If you want them in the environment when you launch an app, then just create a script to launch the app and put the variable export commands in that script.

---

