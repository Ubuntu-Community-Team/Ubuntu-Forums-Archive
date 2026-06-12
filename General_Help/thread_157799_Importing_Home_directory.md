---
title: "Importing Home directory"
date: 2006-04-09
forum: General Help
---

### Post by ottothecow on 2006-04-09
I have my old home directory from the mandriva install that used to on this comptuter backed up in a tarball.

I'd like to import certain parts but I am not sure which of the .folders are safe and which will mess with kubuntu.

I'd like it to import my desktop/appearance settings, firefox/thunderbird settings, etc but not try to import menu settings that point to nonexistant things and stuff like that.

Which folders should I pull in, or shoudl I just redo my appearance settings?

---

### Post by aysiu on 2006-04-09
It's pretty safe to import .mozilla and .thunderbird

For appearance stuff, I think you should just import them one at a time, backing up before you import and see how it goes.

For example, you can rename .kde to .kde_backup and then bring in Mandriva's .kde. If it works, great. Otherwise, delete it and change .kde_backup back to .kde.

---

### Post by nickle on 2006-04-10
I took the jump when moving from Suse 10.0 to Kubuntu. I had the same version of KDE running with all the same application versions and I simply copied the whole tree and it worked without any problems. I was essentially copying to an empty Kubuntu /home with the same user names.. There was no real risk as I had all my original data backed up.

I cannot make any general recommendations about this approach, but if you are careful and sensible, I cannot see what can go wrong...

---

