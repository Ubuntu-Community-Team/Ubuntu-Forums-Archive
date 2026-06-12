---
title: "User Specific Screen Resolutions"
date: 2011-09-19
forum: General Help
---

### Post by Alex.H on 2011-09-19
I am using 11.04 and trying to set-up different screen resolutions for different users. I want my main (admin) login to use a 1280x1024 resolution on my main monitor (ONLY), but my secondary (media) login to use a 1920x1080 resolution on my tv(ONLY).

I've tried setting both to the specific resolutions I want but then when I go to run certain programs, they stretch across the two displays, or only display on my main monitor.

Using Nvidia X Server settings and updating the X-configuration file seems to only work globally across all logins, and it is kind of a pain the in butt to have to change all my screen resolutions manually when I want to switch from my media center to general use or visa-versa.

Suggestions?

---

### Post by papibe on 2011-09-19
nvidia-settings (the actual program name of the 'Nvidia X Server settgings') stores personal user settings in a hidden file in each user directory:
```
 ~/.nvidia-settings-rc
```
That way each user can have their own settings.

In order to load those settings in a session, you need to run this:
```
$ nvidia-settings --load-config-only
```
The proper place to do this is creating an entry in the 'Startup Applications'. Note that the entry is probably there already.

Tell us how it goes,
Regards.

---

### Post by Alex.H on 2011-09-20
I can see the --load-config-only in Startup Applications, but the ~/.nvidia-settings-rc comes back as "no file or directory"

I've noticed before that there is an X-config file that the Nvida Server Settings saves to, but haven't been able to find anything user specific or relating to actual resolution when viewing the file.

---

### Post by papibe on 2011-09-20
Try this:

Log into one of the users that needs a custom resolution. Open 'Nvidia X Server settings' set the resolution desired. Quit 'Nvidia X..'

Now check if the file was created. If so, log out an log in again to test if the settings stick.

Regards.

---

### Post by Alex.H on 2011-09-21
Turns out the file is not automatically created. I had to actually "save to x configuration file" with the file directory as the hidden ~/.nvidia-settings-rc manually, but it did the trick.

Thanks so much for your help!
:)

---

