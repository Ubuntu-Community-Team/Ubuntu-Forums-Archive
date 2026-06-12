---
title: "Audacious wont start anymore"
date: 2012-06-19
forum: General Help
---

### Post by clifford junior on 2012-06-19
Hi

Before I start I must admit at being a novice of trying to install from .tar, so please be easy on me.

I'm using ubuntu 12.04 and was using the latest version of audacious 3.2.3-1 installed from the ppa.

I decided to try the new alpha build and so I unistalled the current version and downloaded the 3.3-alpha1.

I unpacked it on my desktop and ran the commands to configure, make and install. everything seemed to go fine except i was left with no icon for audacious and didnt try to run the alpha.

I decided to revert back to the ppa version 3.2.3-1 and so deleted the desktop folder and reinstalled via ppa. the icon reappeared, however when i tried to load the program, nothing at all happens.

I purged audacious and ran ubuntu tweak to clean up all remains and reinstalled via the ppa, but it still wont load. i deleted the cach etc, but still it wont load anymore.

Can anybody help me out here? at this point I dont know what to do.

Regards

---

### Post by deathadder on 2012-06-19
When you say you purged audacious what do you mean? Can you run the audacious command from a terminal and post the output.

---

### Post by clifford junior on 2012-06-19
I mean when I reinstalled audacious from the ppa and it still wouldnt start i ran the command to purge audacious.

i've just ran from the command line with the following errors

```
** (audacious:2814): CRITICAL **: interface_uninstall_toolbar: assertion `current_interface' failed

** (audacious:2814): CRITICAL **: interface_uninstall_toolbar: assertion `current_interface' failed

** (audacious:2814): CRITICAL **: interface_uninstall_toolbar: assertion `current_interface' failed

** (audacious:2814): CRITICAL **: interface_uninstall_toolbar: assertion `current_interface' failed

** (audacious:2814): CRITICAL **: interface_uninstall_toolbar: assertion `current_interface' failed

```

---

### Post by clifford junior on 2012-06-19
basically, when I've tried to build audacious alpha from .tar and then reinstalled the older version (most likely over the top of the alpha version), it seems to have messed up something. im guessing my problem come from this.

and even after uninstalling, cleaning cache, etc i cant run the program.

---

### Post by deathadder on 2012-06-19
Have you tried downloading the alpha tar, extracting it and running the configure and trying make uninstall? Hopefully that'll clear out anything remaining from the previous install, then you can try to reinstall via the PPA again.

---

### Post by clifford junior on 2012-06-19
> **deathadder said:**
> Have you tried downloading the alpha tar, extracting it and running the configure and trying make uninstall? Hopefully that'll clear out anything remaining from the previous install, then you can try to reinstall via the PPA again.

no i havent. i shall give that a try. thank you.

while im at it, regarding the alpha tar, i was right in thinking that to install it i would do the following:

1. extract to desktop
2. cd to extracted folder
3. ./configure
4. make
5. sudo make install

I didnt come up against any errors and yet once done there was no audacious icon. am i missing something here?

---

### Post by deathadder on 2012-06-19
Nope that's correct, Audacious would have probably (but not definately) put a icon file somewhere on the filesystem. The usual candiate is somewhere under /usr/share, either /usr/share/icons or /usr/share/app_name if I remember correctly.

At that point you need to create a .desktop file for the application to be visible in your menu. You'd call it audacious.desktop and place it under /usr/share/applications. You can just copy one of the other .desktop files present and use that.

---

### Post by clifford junior on 2012-06-19
> **deathadder said:**
> Have you tried downloading the alpha tar, extracting it and running the configure and trying make uninstall? Hopefully that'll clear out anything remaining from the previous install, then you can try to reinstall via the PPA again.

Hi again. This has worked and audacious is running again. thank you for your help in this matter i very much appreciate it.

---

### Post by deathadder on 2012-06-19
> **clifford junior said:**
> Hi again. This has worked and audacious is running again. thank you for your help in this matter i very much appreciate it.
No problem, glad its working for you now

---

### Post by clifford junior on 2012-06-19
> **deathadder said:**
> No problem, glad its working for you now

thanks for the clarification of installation instructions too. i some point i'll attempt to do this properly. but for today ive already done enough damage.

---

### Post by andrew.46 on 2012-07-04
You are also compiling the audacious-plugins source?

---

