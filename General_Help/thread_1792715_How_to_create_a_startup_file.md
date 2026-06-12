---
title: "How to create a startup file?"
date: 2011-06-28
forum: General Help
---

### Post by n0c0d3 on 2011-06-28
I need to create a startup file. As far as I've been able to find out the best locations to do this are the /etc/init and /etc/init.d directories. Two questions about that:
1) Can I just make blahblah.conf file in one of these directories and then it will be automatically read at boot-time or do I need to create a line that directs to the right file and location in again some other file?
2) Does it matter which of the directories (init of init.d) directories I use, ie., what's the difference?

Thanks,
Bart

---

### Post by seawolf167 on 2011-06-28
Take a look [here ]("https://help.ubuntu.com/community/UbuntuBootupHowto")for starting and stopping services at boot.
Take a look [here ]("https://help.ubuntu.com/community/AddingProgramToSessionStartup")for adding a program to the startup session (much easier IMO).

---

### Post by tcsmith1978 on 2011-06-28
The normal way to do this is to create a shell script and put this in init.d. If you need to ensure the script runs on startup, put a symbolic link in rcS.d to the file in init.d. I'm not 100% sure what init is - looking at it - it looks like config files for scripts in init.d but I may be wrong. As for runlevels (i.e. the other directories called rc2.d, rc3.d etc) I'm still trying to figure that out!

Hope this helps!

Tim

---

### Post by n0c0d3 on 2011-06-28
Thanks for your quick replies!
I need to run the following command at login (boot):
```
export LC_NUMERIC="C"
```
to try to change some locale-settings in Xubuntu. I don't have the faintest clue how to make a shell-script of it. I was advised to put the command in 'some profile file in /etc/'. I'm struggling to find out how to do this (haven't figured that out yet as well), but I think the best option is to put it in a separate file so if things go wrong I can just easily delete the file and reboot to get back to where I was before.

Bart

---

### Post by seawolf167 on 2011-06-28
You can place the EXPORT in your ~/.bashrc file which will be loaded when your profile is read

---

### Post by sisco311 on 2011-06-28
> **n0c0d3 said:**
> Thanks for your quick replies!
I need to run the following command at login (boot):
```
export LC_NUMERIC="C"
```
to try to change some locale-settings in Xubuntu. I don't have the faintest clue how to make a shell-script of it. I was advised to put the command in 'some profile file in /etc/'. I'm struggling to find out how to do this (haven't figured that out yet as well), but I think the best option is to put it in a separate file so if things go wrong I can just easily delete the file and reboot to get back to where I was before.

Bart

[uhelp]community/Locale#Changing settings permanently[/uhelp]

---

