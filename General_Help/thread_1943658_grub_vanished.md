---
title: "grub vanished"
date: 2012-03-19
forum: General Help
---

### Post by bloodyweretiger on 2012-03-19
Hello! Sorry, I just wanted to know...my friend just recently installed ubuntu alongside windows 7, and it was dual booting normally(I saw it working) but since today, it just boots directly to ubuntu. To restore the grub to the win7 I can use the same method that we use to restore grub for ubuntu? sorry for anything, any tip will  be very useful!

and sorry if there is the same question somewhere in the forums, no time to check.

---

### Post by varunendra on 2012-03-20
If grub can boot Ubuntu, it means it is installed and working fine, so there is no need to reinstall or 'repair' it. I guess either the boot-menu timeout has somehow (accidentally or intentionally) got set to '0', or the Win7 entry has vanished from the list for some reason. There can be many easy but different fixes depending on the reason.

First of all, from the installed Ubuntu, try-
```
sudo update-grub
```
Reboot and see if you get the option to choose Win7. If not, then the next easiest approach would be to install and run "Startup Manager" to make simple changes to Grub from a friendly GUI:
```
sudo apt-get install startupmanager
```
After installing, run it and make sure the grub-timeout is set to 10 seconds or something reasonable.

If even that doesn't help (for example, if it doesn't list Win7 as an option at all), try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), yet another friendly GUI tool, but much more powerful. Use it to create 'Boot Info Summary', then post it (or its pastebin link) here for us to analyze the problem.

If Win7 is still there and is intact, the *update-grub* command or at most fixing the timeout should be all you need.

---

