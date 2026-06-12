---
title: "Graphic login not working after removing pulse audio packages"
date: 2010-08-18
forum: General Help
---

### Post by dumpsterdiver on 2010-08-18
Hello!

Today when I was working on fixing my soundcard I used the package manager to remove the packages associated with pulse audio. I also run the alsa info bash script. After thist I turned the computer off and changed sound card.

When starting it up again after this the login screen didn't look as usual. It's a plain gray window, but functioning. The graphic login also seem to come faster than usual, indicating that there's something that used to be loaded during startup that is now not.

When I try to login in the "new" graphic login screen it just returns me to the same login screen after a few seconds. I can login in through the shell.

[B]Could removing pulse audio cause this? or have I accidently removed something else? What could that be?

How do I solve it?[/B]

Very grateful for any help,

best regards

---

### Post by dumpsterdiver on 2010-08-18
Ok, solution goes like this:

**What happend?**
When I removed pulse audio I was to lazy to look through all packages that was going to be removed automatically if I removed pulse audio packages. Amoung the packages removed automatically were some that were crucial to gnome.

**How to begin solving it**
Reboot, get into the grub menu by pressing ESC and choose "recovery mode". Then look in *var/logs/apt/history.log* and see what packages very removed today. Extract the list of those and remove the comma and the text inside parameters (and the parameters themselves). You can do this with *sed* or by hand ...

Then run:
```
apt-get install $(filename_where_you_saved_package_list)
```This will install the lost packages again.

---

