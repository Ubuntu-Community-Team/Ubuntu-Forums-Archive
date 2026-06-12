---
title: "flash plugins"
date: 2010-01-12
forum: General Help
---

### Post by deathseek on 2010-01-12
mozilla cant play video

---

### Post by garvinrick4 on 2010-01-12
open a Terminal:
          sudo apt-get install flashplugin-installer

---

### Post by deathseek on 2010-01-12
> **garvinrick4 said:**
> open a Terminal:
          sudo apt-get install flashplugin-installer


ive done what u have told me still i cant play video over youtube..
do i need to restart my firefox? and i do how would i do that..

---

### Post by fancypiper on 2010-01-12
> **deathseek said:**
> ive done what u have told me still i cant play video over youtube..
do i need to restart my firefox? and i do how would i do that..Close and re-open firefox.

Do you have a 32 bit or 64 bit CPU?

# 64 bit flash fix
# As per [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
# Howto fix Flash on Ubuntu 9.10
If you are not able to click on flash (e.g. on Youtube), here is how to fix this known bug (works for both 32-bit and 64-bit):
1. Press ALT+F2 and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
2. Add the following line before the last line in the file:
export GDK_NATIVE_WINDOWS=1
3. Save and restart Firefox, or if this doesn't fix it, try restarting Ubuntu.

---

### Post by deathseek on 2010-01-12
thanks... i can watch video... one more thing can i change my username... is that possible... i just install ubuntu 2hrz aog.. love it

---

### Post by fancypiper on 2010-01-12
You can create another user easier than changing your username.

Clicky System>Administration>Users and Groups

Command line:
adduser <name>
Then, follow prompts.

---

